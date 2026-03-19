---
identifier: community
title: Community
menu:
  main:
    parent: 'community'
disable_comments: true
---

# Communities

* [Ecosystem Formally Verifiable IT](https://trustworthy-it.com/en)
* [Clash -- A modern, functional, hardware description language](https://clash-lang.org)
* [Haskell -- A purely functional, declarative programming language](https://www.haskell.org)
* [Liquid Haskell -- Haskell with Refinement Types](https://ucsd-progsys.github.io/liquidhaskell)

# Repositories

* [ghc-typlits-proof-assist](https://github.com/clash-lang/ghc-typelits-proof-assist): A GHC plugin enabling the developer to rely on an external proof assistant (Agda, Rocq or Lean) to prove statements that are either impossible or too difficult to prove with the existing constraint solver of GHC.
* [clash-crypto](https://github.com/clash-lang/clash-crypto): A hardware design library for cryptographic primitives written in Clash.

# Talks

* __Ökosystem Vertrauenswürdige IT -- Projekt Clash Formal__ </br>
  20 January 2025, [Project Kickoff](https://www.cyberagentur.de/en/press/a-milestone-for-it-security-in-germany) </br>
  <small> [Slides](../media/talks/clash-formal-20250120-kickoff-en.pdf) _(EN)_, [Slides](../media/talks/clash-formal-20250120-kickoff-de.pdf) _(DE)_ </small>
* __Formale Verifikation von Hardware__ </br>
  15 May 2025, [Security and Innovation in Cyberspace](https://sic.cyberagentur.de) </br>
  <small> [Slides](../media/talks/clash-formal-20250515-sic.pdf) _(DE)_ </small>
* __`ghc-typelits-proof-assist`: A Haskell Plugin for Type-Nat Proofs__ </br>
  6 June 2025, [Haskell Implementors Workshop (Lightning Talk)](https://haskell.foundation/events/2025-haskell-implementors-workshop.html) </br>
  <small> [Slides](../media/talks/clash-formal-20250606-hiw-plugin.pdf) _(EN)_, [Video](https://youtu.be/KfxyyADOsIk?list=PLQpeDZt0_xQfpBPdVV3hUZ3_pDxmYhsbr&t=848) _(EN)_ </small>
* __Experience Report: Translating Haskell / Clash to Coq / Agda / Liquid Haskell__ </br>
  6 June 2025, [Haskell Implementors Workshop (Lightning Talk)](https://haskell.foundation/events/2025-haskell-implementors-workshop.html) </br>
  <small> [Slides](../media/talks/clash-formal-20250606-hiw-report.pdf) _(EN)_, [Video](https://youtu.be/KfxyyADOsIk?list=PLQpeDZt0_xQfpBPdVV3hUZ3_pDxmYhsbr&t=1999) _(EN)_ </small>
* __Synergizing Functional Programming, Proofs & Hardware Design__ </br>
  6 October 2025, [FOMSESS Annual Workshop](https://fg-fomsess.gi.de/veranstaltung/jahrestreffen-2025) </br>
  <small> [Slides](../media/talks/clash-formal-20251006-fomsess.pdf) _(EN)_ </small>

# Challenges

* [The Clash UDBC Arbiter Verification Challenge](https://github.com/QBayLogic/UDBC-Arbiter): The challenge is to formally verify that the given implementation satisfies a given list of safety and security properties for any number of clients and all potential data types.

* [TSL Kitchen Timer Verification](https://github.com/reactive-systems/kitchentimer): The Clash hardware implementation of the timer has been claimed to satisfy the given temporal specification by construction, but the specification cannot be verified against the synthesized or any other manually given specification yet. The challenge is to connect the specification with a Clash implementation using a verification system that is capable of verifying the design against the specified properties.

# Acknowledgements

This project would be impossible without the availability of a vast range of already existing open source software and hardware projects indirectly contributing to the success of the project as well. Some of the most influential projects are:

* [Clash: Haskell to VHDL/Verilog/SystemVerilog Compiler](https://github.com/clash-lang/clash-compiler)
* [Glasgow Haskell Compiler](https://www.haskell.org/ghc)
* [Liquid Types For Haskell](https://github.com/ucsd-progsys/liquidhaskell)
* [Nix Packet Manager](https://nixos.org)
* [Yosys Open SYnthesis Suite](https://github.com/YosysHQ/yosys)
* [`nextpnr`: A portable FPGA place and route tool](https://github.com/YosysHQ/nextpnr)
* [Project Trellis](https://github.com/YosysHQ/prjtrellis)
* [OrangeCrab Development Board](https://orangecrab-fpga.github.io/orangecrab-hardware)
* [Sail Architecture Definition Language](https://github.com/rems-project/sail)
* [Rocq Proof Assistant](https://rocq-prover.org)
* [Agda Proof Assistant](https://github.com/agda/agda)
* [Lean Proof Assistant](https://lean-lang.org)

<style>
.post__title{ display:none; }
</style>
