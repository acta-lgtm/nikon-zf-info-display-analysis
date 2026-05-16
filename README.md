# nikon-zf-info-display-analysis

## Analysis of Nikon Z f State Transitions: "Info" Display Logic

This repository documents the results of analyzing the state transitions observed on my personal Nikon Z f.

With this particular camera, pressing the shutter button halfway at times failed to immediately ready the camera for shooting. This behavior can depart from a photographer’s natural expectations and may lead to missed photo opportunities.
Furthermore, under default settings, the LCD could remain locked on the Information Display even during continuous shooting. To uncover the specific triggering conditions and identify potential workarounds, I conducted detailed behavioral observations.

I hypothesize that the phenomena observed here are closely tied to the "Information Display (Info)"—a feature inherited from the D-series DSLRs—and may represent a visible manifestation of the coexistence between legacy and modern system logic.
 While this camera boasts a heritage design, it appears to attempt a fusion between legacy hardware and modern systems not just on the surface, but deep within its internal logic.

Although I am a complete layman in the field of systems engineering, I hold a deep interest in user interfaces and the integration of legacy and modern technology. I share this report in the hope that it will spark meaningful discussions among experts and specialists in the community.

As this analysis was conducted independently by a non-specialist, some terminology or interpretations may be incomplete.

---

## 1. Project Overview

### 1.1 Objective

- Visualization of state transitions involving the "Information Display (Info)" on the Nikon Z f.
- Logical analysis of "display priority" and "state persistence" occurring under specific operational conditions.
- A study on the coexistence of legacy and modern architectures within the system.

### 1.2 Observed Phenomena 

* **Display Priority Persistence:** The "Information Display (Info)" appears to preempt or retain display priority over other operational displays under certain conditions.
* **Recovery Path Removal Through Configuration:** Certain customizations can make standard UI-level recovery paths inaccessible without any explicit system warning.
* **State Persistence:** The status of the "Information Display (Info)" is maintained (resumed) even after cycling the power.
* **Inconsistency of Internal States:** Even when the visual appearance remains identical, the system's response (output) to inputs varies depending on past display history.
* **Persistent Info Display Under Specific Modes:** Under specific conditions such as continuous shooting mode, the "Information Display (Info)" persistently occupies the entire LCD when the user's eye is removed from the viewfinder.

### 1.3 Target Environment

- **Device:** Nikon Z f
- **Firmware:** [ C: Ver. 3.01 ]

### 1.4 Video documentation in preparation.

Video documentation is currently in preparation.

Independent reproduction attempts on other Nikon Z f units
are welcome.

---

## 2. Structure of Data 

### Current Status

The following case documentation is currently available:

- [Case B2: In the Fray of the Focus](./docs/DB/Case_B2_Fray.md)

Additional documentation is currently in preparation.

### Phase 1: Definition A (Coarse-grained)
- [**Case A1:** Schrödinger's Sisyphean Loop](./docs/DA/Case_A1_Schrodinger.md): Work in progress
- [**Case A2:** Deterministic Loop: Immediate Transition from Default Settings](./docs/DA/Case_A2_Deterministic.md): Work in progress

### Phase 2: Definition B (Fine-grained)
- [**Case B1:** The Shadow Double](./docs/DB/Case_B1_Shadow.md): Work in progress
- [**Case B2:** In the Fray of the Focus](./docs/DB/Case_B2_Fray.md)
- [**Case B3:** Cornering the Shadow: A Trace from the Past](./docs/DB/Case_B3_Cornering.md): Work in progress



---

## 3. Insights & Hypotheses
- [Analysis and Hypothesis](./insights.md): Work in progress

---

## 4. Visual Appendix
- [Video / GIF Resources](./docs/media.md) : Work in progress
- [Extra Visualization (Concept Map)](./case-a1-concept-map-cat.pdf)

---



## 5. Appendix: Reference Definitions

### Display Control Contexts
- **Context A**
  - [Monitor mode] = Prioritize viewfinder (1 or 2)
  - [Automatic monitor display switch] = On (when monitor docked)
- **Context B**
  - [Monitor mode] = Automatic display switch
  - [Automatic monitor display switch] = On
  - Factory default configuration
- **Context C**
  - [Monitor mode] = Monitor only
- **Context D**
  - [Monitor mode] = Prioritize viewfinder (1 or 2)
  - LCD monitor inactive due to EVF priority activation
- **Context E**
  - [Monitor mode] = Automatic display switch
  - [Automatic monitor display switch] = On (when monitor docked)

> [!NOTE]
> **Context D** represents a temporary display-routing condition in which Live View is assigned to the EVF and the LCD monitor becomes inactive due to EVF-priority behavior. Under this condition, previously observed Info persistence behavior was not maintained while Live View routing remained EVF-active.

<a id="assessment-codes"></a>
### Assessment Codes

- **E** = Expected
- **N** = Not Expected
- **M** = Mechanically consistent, but operationally Not Expected

The term "Expected" refers to behavior expected from the currently active display and shooting context as observed from the user's perspective.

These assessments are observational and operational in nature, and do not imply conclusions regarding internal firmware intent.



---

## Disclaimer

This repository contains personal observations and hypotheses
based on behavior observed on a specific Nikon Z f unit.

The observations and interpretations presented here do not
represent official Nikon specifications, nor do they imply
that identical behavior occurs on all units.

---

## License

Unless otherwise noted, the contents of this repository
are licensed under the Creative Commons
Attribution-NonCommercial 4.0 International License
(CC BY-NC 4.0).

See [LICENSE](./LICENSE.md) for details.

---

This repository is a work in progress and will be updated as additional observations are organized.
