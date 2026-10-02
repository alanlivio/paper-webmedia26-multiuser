---
title: "NCL Users API: gingaf support and new proposed user attribute for <rule>"
template: "home.html"
hide:
  - navigation
authors:
  - name: Alan L. V. Guedes
    institution: University of Reading
  - name: Paulo Victor Borges
    institution: PUC-Rio
  - name: Daniel Moraes
    institution: PUC-Rio
  - name: Sergio Colcher
    institution: PUC-Rio
conference: "WTVDI 2026"
links:
  - name: Paper
    url: main.pdf
    icon: ri:file-pdf-2-line
  - name: Slides
    url: slides/
    icon: ri:slideshow-line
  - name: Software Code
    url: https://github.com/alanlivio/gingaf
    icon: ri:github-line
  - name: LaTeX/Website Code
    url: https://github.com/alanlivio/paper-gingaf-multiuser
    icon: ri:github-line
description: "NCL Users API: gingaf support and new proposed user attribute for <rule>."
---

<div class="abstract-container" markdown="1">
<div class="abstract-inner" markdown="1">

## Abstract

Next-generation digital television standards (TV 3.0) require seamless multi-device interaction and multi-user personalization. In this paper, we present <span style="font-variant: small-caps;">gingaf-multiuser</span>, an extended implementation of the NCL Users API specified in ABNT NBR 25608. By integrating user profile management and multi-user event synchronization at both the document logic engine (`ncl_doc`) and visual widget presentation layer (`gingaf`), we enable collaborative and personalized interactive multimedia applications.

</div>
</div>

## Overview

`gingaf-multiuser` implements the NCL Users API (ABNT NBR 25608) to enable multi-screen synchronization and user personalization across TV 3.0 digital interactive broadcasts.

## Key Highlights

- **NCL Users API Core**: Implements `NCLUser` profile properties and `Users` context in `ncl_doc`.
- **Multi-Screen Property Routing**: Dynamic active user state resolution across companion displays.
- **Visual Widget Synchronization**: Reactive user context changes updating layout regions and targeted ad insertion in `gingaf`.

## Citation

```bibtex
@inproceedings{gingaf_multiuser2026,
  author    = {Guedes, Alan L. V. and Borges, Paulo Victor and Moraes, Daniel and Colcher, Sergio},
  title     = {NCL Users API: gingaf support and new proposed user attribute for <rule>},
  booktitle = {Anais Estendidos do XXXII Simpósio Brasileiro de Sistemas Multimídia e Web (WTVDI 2026)},
  location  = {Lavras, Brazil},
  year      = {2026},
  doi       = {10.5753/webmedia.2026.gingaf-multiuser}
}
```
