# Lab 4: Benchmark a Parameter

## Objective
The objective of this lab is to design, slice, print, and evaluate a custom benchmark artifact to determine the physical manufacturing limits of the Prusa Core One 3D printer. By characterizing specific machine constraints, we establish empirical design rules necessary for reliable FDM additive manufacturing.

---

## Parameter

- **Tested Parameter:** Minimum Wall Thickness and Pin/Hole Tolerance Limits (Wall thicknesses: 0.4mm, 0.8mm, 1.2mm, 1.6mm, 2.0mm; Pin/Hole clearance: 0.1mm, 0.2mm, 0.3mm, 0.4mm).
- **Hypothesis / Prediction:** I predict that the Prusa Core One (using a 0.4mm nozzle) will reliably produce walls down to 0.8mm (two perimeter passes). The 0.4mm single-wall section is predicted to exhibit fragile layer bonding or slicing gaps. For fit tolerance, I predict a minimum clearance of 0.2mm will be required for a free-moving clearance fit.

---

## Document Design

### Design Process & Iteration
To evaluate dimensional limits and wall extrusion constraints, a compact gauge block was modeled in CAD.

1. **CAD Modeling:** Modeled a rectangular base plate incorporating vertical test fins with step-increasing wall thicknesses and precision pin/hole pairs.
2. **Feature Sizing:** Kept overall dimensions compact (45 mm x 30 mm x 15 mm) to ensure the active print time remains under the 1-hour limit.
3. **Identification Markers:** Embossed dimension values next to each wall and pin feature for clear post-print measurement.

![Dimensional Gauge CAD Model Overview]([IMAGE_PLACEHOLDER_CAD_MODEL_OVERVIEW])
*Figure 1: CAD model layout of the dimensional tolerance and wall thickness benchmark block.*

![Feature Design Iterations]([IMAGE_PLACEHOLDER_CAD_FEATURE_SKETCHES])
*Figure 2: Initial CAD feature sketches and clearance testing layout.*

---

## Preprocessor

The STL file was imported into **PrusaSlicer** to configure build parameters suited for fine-feature accuracy testing.

![PrusaSlicer Toolpath Setup]([IMAGE_PLACEHOLDER_PRUSASLICER_SCREENSHOT])
*Figure 3: Toolpath preview, layer alignment, and slicing breakdown in PrusaSlicer.*

### Build Parameter Justifications
- **Infill (15% Grid):** Chosen to provide internal stability for top surfaces without affecting thin outer wall perimeters or adding unnecessary print time.
- **Build Orientation (Flat Base Alignment):** Placed completely flat on its primary base to ensure vertical walls and pins print perpendicular to the build plate for maximum accuracy.
- **Supports (Disabled):** Supports were set to **None**. Adding supports around precision clearance holes or thin walls would alter dimensions and invalidate the benchmark.
- **Scaling (100% / Native Scale):** Printed at native 1:1 scale so that nozzle extrusion widths match modeled wall values directly.
- **Print Metrics:** Estimated print time ~32 minutes; estimated material ~11.2 grams of PLA.

### Process Notes & Adjustments
- Positioned the model near the center of the bed in PrusaSlicer to benefit from uniform bed temperature and optimal first-layer extrusion.

---

## Print Artifact

### Execution & Results
- **Printer Assigned:** UNCC Print Farm – Prusa CORE One
- **Material Used:** Generic PLA
- **Test Results:** Thin walls down to 0.8mm printed cleanly with high structural integrity, while the 0.4mm wall showed minor top-edge fragility. The 0.2mm hole clearance allowed smooth pin insertion without binding.

![Completed Benchmark Print]([IMAGE_PLACEHOLDER_PRINTED_ARTIFACT_BED])
*Figure 4: Completed dimensional calibration print artifact on the build plate.*

![Detailed Feature View]([IMAGE_PLACEHOLDER_PRINTED_ARTIFACT_CLOSEUP])
*Figure 5: Close-up inspection of printed pin tolerances and wall thickness steps.*

> **Note:** [VIDEO_PLACEHOLDER_ACTIVE_PRINT] A 15-second video recording of the active printing process is embedded for evaluation.

---

## Lessons Learned

1. **Wall Thickness vs. Nozzle Diameter:** The 0.8mm wall printed cleanly because it equals two exact passes of a 0.4mm nozzle. The 0.4mm single perimeter was weak, demonstrating that nominal wall thickness should be designed as multiples of the nozzle diameter.
2. **Comparison to Design Rules:** Class FDM design rules recommend a minimum wall thickness of 0.8mm and a clearance tolerance of 0.3mm. The Prusa Core One matched the 0.8mm wall rule and exceeded expectation by achieving a tight 0.2mm functional clearance fit.
3. **Slicer Perimeter Generator Impact:** Using Arachne perimeter generation in PrusaSlicer helps smooth out variable-width features, but physical extrusion limits still govern thin-wall rigidity.
4. **Future Design Adjustments:** In future CAD designs for moving assemblies, I will use 0.25mm as the standard offset gap for sliding fits and avoid single-extrusion walls below 0.8mm.

### Workflow Time
- **Total Time Elapsed:** ~50 minutes (12 min CAD & Slicing + 32 min Print + 6 min Post-Inspection).

---

## Resources

- [Prusa CORE One Specifications & User Manual](https://help.prusa3d.com/) – Machine specs and extrusion capabilities.
- **Class Design Rules for 3D Printing Chart** – Minimum wall thickness and tolerance guidelines for FDM manufacturing.
