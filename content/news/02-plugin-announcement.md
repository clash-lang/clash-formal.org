---
title: "ghc-typelist-proof-assist's new API is out!"
date: "2025-06-06"
description: "Announcement for the GHC typelits plugin"
disable_comments: false
author: "diegodiv"
authorbox: true # Optional, enable authorbox for specific post
toc: false
mathjax: true
menu:
  main:
    parent: 'news'
---

Two weeks ago, we released a new API for [ghc-typelits-proof-assist](https://github.com/clash-lang/ghc-typelits-proof-assist). It's due
time for a short presentation!

## What is it?

It's a GHC plugin that bridges proof assistants (Coq and Agda at the time
of writing) and Haskell code to enable developers to prove statements on
[`Nat`](https://hackage.haskell.org/package/base-4.21.0.0/docs/GHC-TypeLits.html#t:Nat)s.

<!--more-->

## When do I need it?

Whenever you'd need to use
[`unsafeCoerce`](https://hackage.haskell.org/package/base-4.21.0.0/docs/Unsafe-Coerce.html#v:unsafeCoerce)
to have GHC accept a statement on `Nat`s as
sometimes, it's hard/impossible for GHC to deduce properties even as
simple-looking (but looks are deceiving) as `n + 1 <= m -> n <= m`.

Let's jot this property down:

```haskell
lemmaAdd :: forall n m. (KnownNat n, KnownNat m, n + 1 <= m) => Dict (n <= m)
lemmaAdd = unsafeCoerce (Dict :: Dict (0 <= 0))
```

And then bring it into scope:

```haskell
myVeryImportantFunction :: forall n m. (KnownNat n, KnownNat m, n + 1 <= m) => ...
myVeryImportantFunction
 | Dict <- lemmaAdd @n @m
 = ...
```

However, `unsafeCoerce`, as its name suggests, is not exactly a safe mechanism
to use here - I could have used it to bring something blatantly wrong into scope
(and assuredly did so in the past). In contrast, `ghc-typelits-proof-assist`
bestows Haskell developers with the power to extend GHC's type-checking with
assertions proven in a proof assistant.

Using the plugin, you'd write:

```haskell
class
  ( n <= m
  ) => Lemma n m

instance
  ( n + 1 <= m
  ) => Lemma n m

instance Lemma n m => QED (Lemma n m)
```

Then using `Lemma` in the body of your function with one of the provided mechanisms:

```haskell
usingRewrite :: forall n m. (n + 1 <= m) => SNat n -> SNat m -> Int
usingRewrite | Rewrite <- using @(Lemma n m) = demand

usingApply :: forall n m. (n + 1 <= m) => SNat n -> SNat m -> Int
usingApply = apply @(Lemma n m) demand

usingAuto :: forall n m. (n + 1 <= m) => SNat n -> SNat m -> Int
usingAuto = demand

demand :: n <= m => SNat n -> SNat m -> Int
demand _ _ = 3
```

The added value here lies in the fact that now, if we don't provide a proof
for `Lemma`, the code will refuse to compile. There's no `unsafeCoerce`-shaped
escape hatch, your duty is to provide a proof - either a Coq or Agda proof.

So let's just do that:
```haskell
{-/ Preamble (Coq):
Require Import Coq.Arith.PeanoNat.
/-}

{-/ Proof (Coq): Lemma
  intros.
  apply le_S in H.
  apply le_S_n.
  rewrite <- PeanoNat.Nat.add_0_l at 1.
  rewrite PeanoNat.Nat.add_comm.
  rewrite PeanoNat.Nat.add_succ_l.
  rewrite PeanoNat.Nat.add_comm.
  rewrite <- PeanoNat.Nat.add_succ_l.
  rewrite PeanoNat.Nat.add_comm.
  apply H.
/-}
```

Et hop! Now that you provided a proof, your code compiles - without having to
resort to lowly coercions. Isn't that nice?

## Next steps: using the plugin and potentially contributing

The plugin is available [on Github](https://github.com/clash-lang/ghc-typelits-proof-assist)
and comes with a full-fledged `README` on how to properly use the plugin.

Keep in mind it's a work-in-progress and that as such, things are subject to change.
Contributions are welcomed, and we're interested to hear from you!
