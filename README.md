# An Analysis of Display 5 (“Info”) Persistence in Nikon Z-Series Cameras: The Case of the Nikon Z f

Originally initiated as an investigation into unusual “Info” persistence on my personal Nikon Z f, this repository gradually expanded into a broader observational analysis of Display 5 (“Info”) behavior across Nikon Z-series cameras.

With this particular camera, pressing the shutter button halfway at times failed to immediately ready the camera for shooting. This behavior can depart from a photographer’s natural expectations and may lead to missed photo opportunities.
Furthermore, under default settings, the LCD could remain locked on the Information Display even during continuous shooting. To uncover the specific triggering conditions and identify potential workarounds, I conducted detailed behavioral observations.

I hypothesize that the phenomena observed here are closely tied to the "Information Display (Info)"—a feature inherited from the D-series DSLRs—and may represent a visible manifestation of the coexistence between legacy and modern system logic.


Although I am a complete layman in the field of systems engineering, I hold a deep interest in user interfaces and the integration of legacy and modern technology. I share this report in the hope that it will spark meaningful discussions among experts and specialists in the community.

As this analysis was conducted independently by a non-specialist, some terminology or interpretations may be incomplete.


---

## 1. Project Overview

### 1.1 Objective

- Visualization of state transitions involving the "Information Display (Info)" on the Nikon Z f.
- Logical analysis of "display priority" and "state persistence" occurring under specific operational conditions.
- A study on the coexistence of legacy and modern architectures within the system.

### 1.2 Historical Context

The “Info” display in Nikon cameras historically functioned as a temporary shooting-information screen.

Introduced prominently during the DSLR era (e.g., Nikon D3 generation), the Info display was accessed via a dedicated “INFO” button and Nikon manuals explicitly documented how to dismiss the screen, including:
- half-pressing the shutter button,
- pressing the INFO/R button again,
- or waiting for timeout.

This behavior and terminology remained consistently documented through multiple DSLR generations.

However, beginning around the launch period of the Nikon Z system (2018), explicit documentation describing how to dismiss the Info display disappeared from Nikon manuals.
At the same time, mirrorless Z-series cameras integrated the former Info display into the DISP display-cycle system (“Display 5”).

| Era       | Info access method                     | Manual                                         | Actual behavior        |
| --------- | -------------------------------------- | ---------------------------------------------- | ---------------------- |
| D3–D3500  | Dedicated INFO/R button                | “Info can be turned off” explicitly documented | half-press clears Info |
| Z7/Z6     | Integrated into DISP cycle (Display 5) | documentation removed                          | unknown                |
| D780      | Dedicated INFO/R button                | documentation removed                          | unknown                |
| D6        | Dedicated INFO/R button                | documentation removed                          | half-press still works |
| Z9/Z8/Zf  | Integrated into DISP cycle (Display 5) | documentation removed                          | Display5 persistence   |

This repository does not attempt to infer Nikon’s internal design intentions.
However, the observed transition in documentation and device behavior appears to coincide with the introduction of the Z system and may be historically significant.

### 1.3 Observed Phenomena 

* **Display Priority Persistence:** The "Information Display (Info)" appears to preempt or retain display priority over other operational displays under certain conditions.
* **Recovery Path Removal Through Configuration:** Certain customizations can make standard UI-level recovery paths inaccessible without any explicit system warning.
* **State Persistence:** The status of the "Information Display (Info)" is maintained (resumed) even after cycling the power.
* **Inconsistency of Internal States:** Even when the visual appearance remains identical, the system's response (output) to inputs varies depending on past display history.
* **Persistent Info Display Under Specific Modes:** Under specific conditions such as continuous shooting mode, the "Information Display (Info)" persistently occupies the entire LCD when the user's eye is removed from the viewfinder.

### 1.4 Target Environment

- **Device:** Nikon Z f
- **Firmware:** [ C: Ver. 3.01 ]

### 1.5 Notes on the Observation Process

The cases in this repository were developed chronologically through observation, rather than from a predefined state model.

Over time, these observations revealed inconsistencies, hidden dependencies, and visually identical states exhibiting different operational behaviors. Consequently, state definitions and transition interpretations evolved throughout the investigation process.

For this reason, earlier tables intentionally preserve the original coarse-grained observations, including ambiguities and apparent inconsistencies that later motivated finer-grained analyses.

Ultimately, this repository is not merely a collection of transition tables, but also a chronological observational record documenting how the underlying display-state structure gradually became visible.

---

## 2. Structure of Data 


## Phase 1: Definition A (Coarse-grained)
- [DA README](./docs/DA/README.md)
- [**Case A1:** Schrödinger's Sisyphean Loop](./docs/DA/Case_A1_Schrodinger.md): Initial observational archive published
- [**Case A2:** Deterministic Loop: Immediate Transition from Default Settings](./docs/DA/Case_A2_Deterministic.md): Initial observational archive published

### Phase 2: Definition B (Fine-grained)
- [DB README](./docs/DB/README.md)
- [**Case B1:** The Shadow Double](./docs/DB/Case_B1_Shadow.md): Initial observational archive published
- [**Case B2:** In the Fray of the Focus](./docs/DB/Case_B2_Fray.md)
- [**Case B3:** Cornering the Shadow: A Trace from the Past](./docs/DB/Case_B3_Cornering.md): Work in progress





---

## 3. Insights & Hypotheses
- [Analysis and Hypothesis](./insights.md): Work in progress

---

## 4. Visual Appendix
- [![Reference Video for Case B2](https://www.youtube.com/watch?v=Linzjau-Ucg)](https://www.youtube.com/watch?v=Linzjau-Ucg)
*Note: This video does not completely reproduce the steps for Case B2.*

- ![Animated illustration of Case B2](./Case_B2_mov1.gif)
  
*Note: A short GIF clipped from the reference video showing the key steps for Case B2.*

- [Extra Visualization (Concept Map)](./case-a1-concept-map-cat.svg)
　- [Download PDF version](https://github.com/acta-lgtm/nikon-zf-info-display-analysis/releases/download/pdf/case-a1-concept-map-cat.pdf)

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
