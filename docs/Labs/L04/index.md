# Lab 4: Benchmark a Parameter

## Objective
The goal of this lab is to test the minimum physical wall thickness limits of the Prusa Core One printer using a simple custom benchmark model and compare the results to standard FDM design rules.

---

## Parameter

- **Tested Parameter:** Minimum Printable Wall Thickness (0.4mm, 0.8mm, and 1.2mm vertical walls).
- **Prediction:** I predict that the 0.8mm and 1.2mm walls will print cleanly because they equal 2 and 3 passes of the 0.4mm nozzle. I predict the 0.4mm wall will be weak, flimsy, or fail to slice properly due to single-extrusion limitations.

---

## Document Design

### Design Process
To keep the benchmark as simple as possible, I designed a basic rectangular block with three vertical steps testing different wall thicknesses.

1. **CAD Sketch:** Drew a basic $30\text{ mm} \times 15\text{ mm}$ base plate in CAD.
2. **Feature Extrusion:** Extruded three vertical fins on top of the base plate with thicknesses of 0.4mm, 0.8mm, and 1.2mm, all at a height of 10mm.
3. **Time Constraint Check:** Total artifact dimensions ($30\text{ mm} \times 15\text{ mm} \times 13\text{ mm}$) keep the active print time under 15 minutes, well within the 1-hour limit.

![Simple Wall Thickness CAD Model]([IMAGE_PLACEHOLDER_CAD_MODEL_OVERVIEW])
*Figure 1: Simple CAD model of the wall thickness benchmark block.*

![CAD Dimensions and Features]([IMAGE_PLACEHOLDER_CAD_SKETCH])
*Figure 2: Dimensioned sketch showing the 0.4mm, 0.8mm, and 1.2mm wall features.*

---

## Preprocessor

The model was loaded into **PrusaSlicer** to configure build settings for wall printing.

![PrusaSlicer Toolpath Preview]([IMAGE_PLACEHOLDER_PRUSASLICER_SCREENSHOT])
*Figure 3: PrusaSlicer setup showing layer heights and toolpaths.*

### Build Parameter Justifications
- **Infill (15% Grid):** Used for the base plate to save print time and material while maintaining a stable foundation.
- **Build Orientation (Flat Base):** Oriented flat on the print bed so the test walls extend straight up along the Z-axis for clean layer stacking.
- **Supports (Disabled):** Set to **None** because adding supports to thin vertical walls would defeat the purpose of testing unsupported extrusion.
- **Scaling (100% Native Scale):** Kept at 100% scale so that the physical wall measurements match the exact nozzle extrusion width.
- **Print Metrics:** Estimated time ~12 minutes; estimated material ~4 grams of PLA.

---

## Print Artifact

### Execution & Results
- **Printer Assigned:** UNCC Print Farm – Prusa CORE One
- **Material Used:** Generic PLA
- **Results:** The 1.2mm and 0.8mm walls printed cleanly with solid structure. The 0.4mm single-perimeter wall printed but was fragile and flexible.

![Printed Benchmark Artifact]([IMAGE_PLACEHOLDER_PRINTED_ARTIFACT_BED])
*Figure 4: Completed print on the build plate.*

![Close-up of Printed Walls]([IMAGE_PLACEHOLDER_PRINTED_ARTIFACT_CLOSEUP])
*Figure 5: Side view comparing the rigidity and finish of each wall thickness.*

> **Note:** [VIDEO_PLACEHOLDER_ACTIVE_PRINT] A 15-second video recording of the active print process is embedded.

---

## Lessons Learned

1. **Wall Thickness Match:** My prediction was correct; 0.8mm is the minimum practical wall thickness for functional parts using a 0.4mm nozzle.
2. **Design Rule Comparison:** Standard FDM design rules recommend a minimum wall thickness of 0.8mm. The Prusa Core One matched this spec exactly.
3. **Single Perimeter Strength:** Walls printed with only one perimeter pass (0.4mm) lack structural strength because there is no internal bonding between perimeter loops.
4. **Future Design Standard:** In future CAD designs, I will make all non-structural outer walls at least 0.8mm thick to ensure two perimeter extrusions.

### Workflow Time
- **Total Time Elapsed:** ~30 minutes (10 min CAD/Slicing + 12 min Print + 8 min Inspection/Documentation).

---

## Resources

- [Prusa CORE One Specifications & User Manual](https://help.prusa3d.com/) – Machine specifications and extrusion recommendations.
- **Class Design Rules for 3D Printing Chart** – FDM minimum feature and wall thickness guidelines.
