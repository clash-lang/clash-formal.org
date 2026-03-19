---
title: "Our new crypto library is out!"
date: "2026-03-02"
description: "clash-crypto is publicly available now"
disable_comments: false
author: "felixklein"
authorbox: true # Optional, enable authorbox for specific post
toc: false
mathjax: true
menu:
  main:
    parent: 'news'
---

One of the key ingredients of our Smart Card demonstrator is a cryptography core that supports secure hashing, secure message authentication and (a)symmetric data encryption. We created a completely self-contained hardware design for such a core in <a href="https://clash-lang.org">Haskell / Clash</a> and made it publicly available under the [CERN-OHL-P-2.0](https://cern-ohl.web.cern.ch) hardware license. All sources and the related tooling can be found at https://github.com/clash-lang/clash-crypto.

<!--more-->

Two of our core principles baked into this library are correctness and security by design. Leveraging these principles extensively makes formal verification of a design straightforward, e.g., we do not have to verify the absence of a bad state being reachable, if the design never introduces such a state in the first place. Haskell is a great design language for that purpose, as it offers many language features that help in following these design principles as much as we can.

Nevertheless, not all of the properties can be formally proven within a single language yet, which is why we also formulate some of our correctness guarantees using the proof assistants <a href="https://github.com/agda/agda">Agda</a> and <a href="https://rocq-prover.org">Rocq</a>.

The library still is in an experimental state and we hope that we can extend it even further during the course of this project and beyond. Our goal is to offer robust and transparent hardware crypto components that are easy and ready to use, especially in applications where safety, trust and security really matters.
