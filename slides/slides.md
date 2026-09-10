---
marp: true
theme: default
paginate: true
header: 'NCL Users API & Rule Extension — WTVDI / WebMedia 2026'
---

<style>
.grayscale {
  filter: grayscale(100%);
}
</style>

<!--
_paginate: false
_header: ""
-->

<div style="display: grid; grid-template-columns: 3fr 1fr; align-items: center;">

<div>

# NCL Users API: gingaf Support and New Proposed User Attribute for &lt;rule&gt;

**Alan L. V. Guedes**$^1$, **Paulo Victor Borges**$^2$, **Daniel Moraes**$^2$, **Sergio Colcher**$^2$
$^1$University of Reading, UK | $^2$PUC-Rio, Brazil

*XXXII Simpósio Brasileiro de Sistemas Multimídia e Web (WebMedia 2026)*

**Paper Website (slides, code, demo)**:
https://alanlivio.github.io/paper-webmedia26-multiuser/

</div>

<div style="display: flex; flex-direction: column; justify-content: center;">

<img src="assets/uor.svg" height="200" class="grayscale" />
<img src="assets/puc-rio.svg" height="120" class="grayscale" />
<img src="assets/qrcode.svg" height="250" />

</div>

</div>

---

# Agenda

- **Context**
- **Proposed Solution**
- **Results**
- **Final Remarks**

---

# Context: The TV 3.0 Paradigm Shift

**From Single-Viewer STBs to Multi-User Living Rooms**
- Broadcast-broadband convergence, multi-screen companion devices, personalized TV.
- Multiple family members watch a shared main screen with companion smartphones/tablets.

**Limitation of Legacy Ginga-NCL (TV 2.0 / 2.5)**
- Context managed solely through global `system` variables (`system.language`, `system.caption`).
- Modifications affect all viewers globally, preventing individualized personalization.

---

# TV 3.0 Standard: The NCL Users API

**Standardization**
- Standardized in SBTVD ABNT 15608-4 for Next-Gen Digital TV.

**New XML Elements**
- `<userBase>`: Container for active user profile definitions.
- `<userProfile>`: Represents viewer profiles; supports external JSON queries via `src`.
- `<settings user="...">`: Binds specific user profile attributes into NCL properties.
- Causal assessment links: Evaluate user attributes (e.g., `gender`, `age`) to drive presentation.

---

# Implementation in gingaf

**Centralized User Profile Registry**
- Headless state machine resolves and caches active viewer profiles.
- Dynamic JSON query evaluation (`adult_query.json`).

**Reactive Property Binding**
- Automatically updates bound `<settings>` properties when user profiles change or log in.
- Integrates seamlessly with `ncl_doc` event scheduling.

**Cross-Platform Delivery**
- Consistent profile management across desktop, mobile, and web targets.

---

# Limitation of Current Causal Link Approach

**High Verbosity & Boilerplate**
- Evaluating user properties requires defining custom `<causalConnector>` elements.
- Needs `<compoundCondition>` with `<assessmentStatement>` comparing variables.
- Each conditional branch requires separate `<link>` definitions.

**Cognitive Overhead**
- Separates selection logic across connectors, links, and settings rather than grouping alternatives together.

---

# Proposed Solution: user Attribute for &lt;rule&gt;

**Extending Native NCL Declarative Rules**
- NCL natively supports `<switch>` and `<rule>` for content adaptation.
- Proposal: Add a `user` attribute to `<rule>` elements:

  ```xml
  <rule id="rAdultMale" user="pAdult" var="gender" comparator="eq" value="male"/>
  ```

**Declarative Selection via `<switch>`**
- Groups alternative media nodes directly inside a single `<switch>`.
- Eliminates connector definitions and verbose multi-link bindings.
- Drastically improves authoring ergonomics and maintainability.

---

# Use Case: Targeted Advertising

**Personalized Content Adaptation**
- **No Adult Male Active**: Dynamically displays general commercial banner (`ad_general.png`).
- **Adult Male Active**: Dynamically selects and renders targeted commercial banner (`ad_male.png`).

<div style="display: flex; gap: 24px; justify-content: center; margin-top: 15px;">
  <div style="text-align: center;">
    <img src="assets/image1.png" height="270" style="border-radius: 4px; box-shadow: 0 2px 8px rgba(0,0,0,0.15);" />
    <p style="font-size: 15px; margin-top: 6px; color: #555;">(a) Without adult male user (general ad)</p>
  </div>
  <div style="text-align: center;">
    <img src="assets/image2.png" height="270" style="border-radius: 4px; box-shadow: 0 2px 8px rgba(0,0,0,0.15);" />
    <p style="font-size: 15px; margin-top: 6px; color: #555;">(b) With adult male user (targeted ad)</p>
  </div>
</div>

---

# Final Remarks

- Complete open-source implementation of the SBTVD TV 3.0 NCL Users API in `gingaf`.
- Architectural support for dynamic user profiles and reactive property evaluation.
- Novel proposal extending NCL `<rule>` with `user` attribute for concise `<switch>` selection.
- Validated with automated test cases and multi-user application scenarios.

---

<!--
_paginate: false
_header: ""
-->

# Thank You!

<div style="display: grid; grid-template-columns: 3fr 2fr; align-items: start;">

<div>

### Questions & Discussion

- **Repository**: https://github.com/ginga-org-br/gingaf
- **About Ginga**: https://ginga.org.br
- **Contact**: `a.guedes@reading.ac.uk` | `danielmoraes@telemidia.puc-rio.br`

</div>

<div style="display: flex; justify-content: center; align-items: flex-start;">

<img src="assets/portal1.png" />

</div>

</div>
