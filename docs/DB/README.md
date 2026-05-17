# Phase 2: Definition B (Fine-grained Analysis)

During ongoing observation, it became evident that the "Info display" and the "Info display with [i] menu overlay" must be analyzed as distinct states. Furthermore, the "Info display" corresponds to the item displayed when "Display 5" is selected under the menu setting [d19 Custom monitor shooting display]. Based on these insights, the state definitions have been further refined. Focusing on the Information Display appears to be key to understanding this camera's behavior, and the detailed observation results are archived here.

## 1. State Definitions
- State S0 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  EVF off

- State S1 \
  LCD monitor open (less than 180 degrees) \
  Live View with the Display 1 overlay displayed on the LCD monitor \
  EVF off

- State S2 \
  LCD monitor docked \
  Menu displayed on the LCD monitor \
  EVF off

- State S3 \
  LCD monitor open (less than 180 degrees) \
  Menu displayed on the LCD monitor \
  EVF off

- State S4 \
  LCD monitor docked \
  Info display with [i] menu overlay on the LCD monitor \
  EVF off

- State S5 \
  LCD monitor open (less than 180 degrees) \
  Info display with [i] menu overlay on the LCD monitor \
  EVF off

- State S6 \
  LCD monitor open (less than 180 degrees) \
  Info displayed on the LCD monitor \
  EVF off \
  (Note: Visually indistinguishable from S25; S6 is specifically defined for states reached by means other than the DISP button.)

- State S7 \
  LCD monitor docked \
  Info displayed on the LCD monitor \
  EVF off \
  (Note: Visually indistinguishable from S21; S7 is specifically defined for states reached by means other than the DISP button.)

- State S8 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Live View with the Display 1 overlay displayed in the EVF

- State S9 \
  LCD monitor opened to the selfie position (180 degrees) \
  Live View (Selfie mode) displayed on the LCD monitor \
  EVF off

- State S10 \
  LCD monitor docked \
  Images stored on the memory card displayed on the LCD monitor \
  EVF off

- State S11 \
  LCD monitor open (less than 180 degrees) \
  Images stored on the memory card displayed on the LCD monitor \
  EVF off

- State S12 \
  LCD monitor docked \
  Only the White balance adjustment overlay displayed on the LCD monitor \
  EVF off

- State S13 \
  LCD monitor open (less than 180 degrees) \
  Only the White balance adjustment overlay displayed on the LCD monitor \
  EVF off

- State S14 \
  LCD monitor open (less than 180 degrees) \
  Nothing displayed on the LCD monitor \
  EVF off

- State S15 \
  LCD monitor open (less than 180 degrees) \
  Live View with the WB adjustment overlay displayed on the LCD monitor \
  EVF off

- State S16 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Live View with the WB adjustment overlay displayed in the EVF

- State S17 \
  LCD monitor docked \
  Live View with the Display 1 overlay displayed on the LCD monitor \
  EVF off

- State S18 \
  LCD monitor docked \
  Live View with the Display 2 overlay displayed on the LCD monitor \
  EVF off

- State S19 \
  LCD monitor docked \
  Live View with the Display 3 overlay displayed on the LCD monitor \
  EVF off

- State S20 \
  LCD monitor docked \
  Live View with the Display 4 overlay displayed on the LCD monitor \
  EVF off

- State S21 \
  LCD monitor docked \
  Display 5 = Info display displayed on the LCD monitor \
  EVF off \
  (Note: Visually indistinguishable from S7; S21 is specifically defined for states reached via the DISP button.)

- State S22 \
  LCD monitor open (less than 180 degrees) \
  Live View with the Display 2 overlay displayed on the LCD monitor \
  EVF off

- State S23 \
  LCD monitor open (less than 180 degrees) \
  Live View with the Display 3 overlay displayed on the LCD monitor \
  EVF off

- State S24 \
  LCD monitor open (less than 180 degrees) \
  Live View with the Display 4 overlay displayed on the LCD monitor \
  EVF off

- State S25 \
  LCD monitor open (less than 180 degrees) \
  Display 5 = Info display displayed on the LCD monitor \
  EVF off \
  (Note: Visually indistinguishable from S6; S25 is specifically defined for states reached via the DISP button.)

- State S26 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Live View with the Display 2 overlay displayed in the EVF

- State S27 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Live View with the Display 3 overlay displayed in the EVF

- State S28 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Live View with the Display 4 overlay displayed in the EVF

- State S29 \
  LCD monitor docked \
  Live View with [i] menu overlay on the LCD monitor \
  EVF off

- State S30 \
  LCD monitor open (less than 180 degrees) \
  Live View with [i] menu overlay on the LCD monitor \
  EVF off

- State S31 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Live View with [i] menu overlay displayed in the EVF

- State S32 \
  LCD monitor docked \
  Live View with the WB adjustment overlay displayed on the LCD monitor \
  EVF off

- State S33 \
  LCD monitor docked \
  Info display with [i] menu overlay on the LCD monitor \
  EVF off \
  (Note: Visually indistinguishable from S4; S33 is specifically defined for states reached via the DISP button.)

- State S34 \
  LCD monitor open (less than 180 degrees) \
  Info display with [i] menu overlay on the LCD monitor \
  EVF off \
  (Note: Visually indistinguishable from S5; S34 is specifically defined for states reached via the DISP button.)

- State S35 \
  LCD monitor docked \
  Nothing displayed on the LCD monitor \
  Picture Review displayed in the EVF

- State S36 \
  LCD monitor docked \
  Picture Review displayed on the LCD monitor \
  EVF off

---

## 2. Analyzed Cases

The following cases document progressively refined observations
regarding the behavior of the Information Display ("Info")
and its interaction with display routing, monitor states,
and shooting operations.

### [Case B1: The Shadow Double](./Case_B1_Shadow.md): Work in progress
Observation of multiple activation pathways leading to visually identical Info-display states with different operational behavior.

### [Case B2: In the Fray of the Focus](./Case_B2_Fray.md)
Observation of persistent Info-display behavior during actual shooting operations, including continuous burst shooting.

### [Case B3: Cornering the Shadow: A Trace from the Past](./Case_B3_Cornering.md): Work in progress
Observation of how monitor routing conditions and LCD activity influence Info-display persistence and recovery behavior.

---

## 3. Methodology
- **Visualization Tool:** Graphviz (dot)
- **Recording Methodology:** Generation of state transition tables based on empirical operation logs and repetitive stress testing to detect micro-transitions and internal flag mismatches.