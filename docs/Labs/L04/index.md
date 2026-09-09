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
I designed a basic rectangular block with three vertical steps testing
# Lab 4: Benchmark a Parameter

## Objective
The goal of this lab is to test the minimum physical wall thickness limits of the Prusa Core One printer using a simple custom benchmark model and compare the results to standard FDM design rules.

---

## Parameter

- **Tested Parameter:** Minimum Printable Wall Thickness (0.4 mm, 0.8 mm, and 1.2 mm vertical walls).
- **Prediction:** It is predicted that the 0.8 mm and 1.2 mm walls will print cleanly because they equal 2 and 3 passes of the 0.4 mm nozzle. It is predicted that the 0.4 mm wall will be weak, flimsy, or fail to slice cleanly due to single-extrusion limits.

---

## Document Design

### Design Process
To keep the benchmark as simple as possible, a basic rectangular block was designed in CAD with three vertical steps testing different wall thicknesses.

1. **CAD Sketch:** Created a 30 mm by 15 mm base plate outline in CAD.
2. **Feature Extrusion:** Extruded three vertical fins on top of the base plate with thicknesses of 0.4 mm, 0.8 mm, and 1.2 mm at a height of 10 mm.
3. **Time Constraint Check:** Total artifact dimensions (30 mm by 15 mm by 13 mm) maintain an active print time under 15 minutes, well within the 1-hour limit.

![Simple Wall Thickness CAD Model]([IMAGE_PLACEHOLDER_CAD_MODEL_OVERVIEW])
*Figure 1: Simple CAD model of the wall thickness benchmark block.*

![CAD Dimensions and Features]([IMAGE_PLACEHOLDER_CAD_SKETCH])
*Figure 2: Dimensioned sketch showing the 0.4 mm, 0.8 mm, and 1.2 mm wall features.*

---

## Preprocessor

The model was loaded into PrusaSlicer to configure build parameters for wall printing.

![PrusaSlicer Toolpath Preview]([IMAGE_PLACEHOLDER_PRUSASLICER_SCREENSHOT])
*Figure 3: PrusaSlicer setup showing layer heights and toolpaths.*

### Build Parameter Justifications
- **Infill (15% Grid):** Applied to the base plate to maintain structural integrity while reducing print time and material usage.
- **Build Orientation (Flat Base):** Positioned flat on the bed so that test walls extend upward along the Z-axis for consistent layer alignment.
- **Supports (Disabled):** Configured to None because adding supports to thin vertical test walls would interfere with testing native extrusion limits.
- **Scaling (Adjusted Scale Factor):** Scaled within PrusaSlicer (scale factor set to 3.94) to ensure the sliced model dimensions match the exact intended physical target of 30 mm by 15 mm by 13 mm.
- **Print Metrics:** Estimated time ~8 minutes; estimated material ~4 grams of PLA.

---

## Print Artifact

### Execution & Results
- **Printer Assigned:** UNCC Print Farm – Prusa CORE One
- **Material Used:** Generic PLA
- **Results:** The 1.2 mm and 0.8 mm walls printed cleanly with rigid structure. The 0.4 mm single-perimeter wall printed but exhibited noticeable flexibility and structural weakness.

![Printed Benchmark Artifact]([IMAGE_PLACEHOLDER_PRINTED_ARTIFACT_BED])
*Figure 4: Completed print on the build plate.*

![Close-up of Printed Walls]([IMAGE_PLACEHOLDER_PRINTED_ARTIFACT_CLOSEUP])
*Figure 5: Side view comparing the rigidity and surface finish of each wall thickness.*

> **Note:** [VIDEO_PLACEHOLDER_ACTIVE_PRINT] A 15-second video recording of the active print process is embedded.

---

## Lessons Learned

1. **Wall Thickness Match:** The initial prediction was confirmed; 0.8 mm is the minimum functional wall thickness when using a standard 0.4 mm nozzle.
2. **Design Rule Comparison:** Results matched standard FDM design guidelines, which specify a minimum recommended wall thickness of 0.8 mm.
3. **Single Perimeter Limit:** Walls printed with a single perimeter pass (0.4 mm) lack adequate strength due to the absence of internal perimeter-to-perimeter bonding.
4. **Future CAD Guidelines:** Future CAD models will incorporate a minimum wall thickness of 0.8 mm for all non-structural walls to guarantee at least two perimeter paths.

### Workflow & Monitoring
- **Print Process:** Observed the first layer deposition and perimeter extrusion paths during printing to verify bed adhesion and wall consistency.
- **Post-Print Inspection:** Measured wall rigidity by hand and verified feature dimensions with digital calipers after removing the part from the build plate.
- **Total Workflow Time:** ~26 minutes total (10 min CAD/Slicing + 8 min Print + 8 min Inspection/Documentation).

---

## Resources

- [Prusa CORE One Specifications & User Manual](https://instructure.charlotte.edu/courses/272053/assignments/2900506) – Machine specifications and operational guidelines.
- **Class Design Rules for 3D Printing Chart** – FDM design recommendations and feature limits.
