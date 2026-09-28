# A6 – Parametric Snap-Fit Design for Motor Mount Artifact

## Objective
Design and 3D print a small parametric component in PLA that snap-fits into a specific feature of the yellow motor mount artifact. The design must utilize parameters, constraints, and engineered allowances in Creo Parametric, followed by proper slicer setup and physical verification.

---

## Parametrically Design

### Research & Feature Analysis
To create a properly mated component, key features on the yellow motor mount artifact were measured using digital calipers. 

* **Artifact Top View:** Shows the rectangular opening and overall cavity structure.
  
  ![Top View of Yellow Artifact](IMG_4106.jpeg)

* **Artifact Frontal View:** Displays the frontal orientation and entry profile.
  
  ![Frontal View of Yellow Artifact](IMG_4107.jpeg)

* **Slot Measurement (`Slot_W`):** Digital calipers measuring the primary slot width ($0.350\text{ in}$).
  
  ![Digital Caliper Measuring Slot Width](IMG_4108.jpeg)

* **Side Latch Hole Detail:** A close-up view highlighting the small side rectangular slot/hole that the locking lip must enter to secure the snap fit.
  
  ![Small Side Window Hole](IMG_4120.jpeg)

### Hand Sketch & Dimensioning
Below is the layout sketch outlining the measured geometry and interface constraints prior to CAD modeling.

*(Include photo/scan of hand sketch here if available)*

### Creo CAD Modeling & Parameters
The part was modeled in Creo Parametric using parametric dimensions, relations, and geometric constraints.

* **Creo Parameters Table:** Displays the defined variables, types, and baseline values used to drive the geometry.
  
  ![Creo Parameters Table](Screenshot%202026-09-28%20130628.png)

* **Initial CAD Concept:** Early CAD stage displaying full $0.350\text{ in}$ depth prior to feature adjustments.
  
  ![Initial CAD Model Concept](Screenshot%202026-09-28%20121045.png)

* **Final Optimized CAD Part:** Final shortened geometry ($0.125\text{ in}$ depth) ensuring the locking lips align directly with the side window slots.
  
  ![Final Creo CAD Model](Screenshot%202026-09-28%20121802.png)

### Design & Parameter Q&A
1. **What are the parameters used?**
   * `Slot_W`: Measured slot opening width ($0.350\text{ in}$).
   * `Flange_W`: Overall base stop block width ($0.700\text{ in}$).
   * `Flange_H`: Base stop block height ($0.300\text{ in}$).
   * `Part_Y`: Total depth of the part ($0.125\text{ in}$).
   * `Arm_H`: Vertical length of cantilever arms ($0.750\text{ in}$).
   * `Arm_T`: Flexure wall thickness ($0.080\text{ in}$).
   * `Lip_Overhang`: Latch tooth protrusion ($0.063\text{ in}$).
   * `Fit_Clearance`: Engineered tolerance gap ($0.010\text{ in}$).
2. **Why did you choose the specific parameters?**
   * They capture the functional mating geometry of the yellow motor mount while allowing flexural arms to deflect inward during insertion and expand outward into the side locking holes.
3. **What values did you choose for the specific parameters?**
   * `Slot_W = 0.350 in`, `Part_Y = 0.125 in`, `Arm_T = 0.080 in`, `Arm_H = 0.750 in`, `Lip_Overhang = 0.063 in`.
4. **Did the values change throughout the process? If so, why?**
   * Yes. The depth (`Part_Y`) was originally modeled at $0.350\text{ in}$ to match the main opening. However, analyzing the small side window hole (`IMG_4120.jpeg`) revealed that a full-depth lip could not snap into place. The total part depth was modified to $0.125\text{ in}$ so the full tooth profile slides directly into the narrow window.
5. **Engineered Allowances:**
   * A $0.010\text{ in}$ clearance allowance was subtracted from mating faces to account for FDM PLA material expansion and surface roughness, ensuring smooth mechanical insertion without binding.

---

## Documentation

### Slicer Setup & 3D Printing Process
The STL was exported from Creo and sliced using PrusaSlicer for printing on a Prusa printer.

* **Bed Layout & Orientation:** Model laid flat on its side to align extruded filament paths along the length of the cantilever arms for maximum flexural strength.
  
  ![PrusaSlicer Build Plate Layout](Screenshot%202026-09-28%20122305.png)

* **Perimeter Settings:** Set to 3 perimeter loops to ensure the thin cantilever arms are printed almost entirely solid.
  
  ![Perimeters Setting - 3 Loops](Screenshot%202026-09-28%20122539.png)

* **Infill Settings:** Set to 20% Infill Density with a Grid pattern.
  
  ![Infill Settings - 20% Grid](Screenshot%202026-09-28%20122557.png)

### In-Progress Printing Video
**

### Printing Technical Specifications
* **Machine Used:** Prusa Core One
* **Print Size / Bounding Box:** $0.700\text{ in} \times 0.125\text{ in} \times 1.050\text{ in}$ ($17.78\text{ mm} \times 3.18\text{ mm} \times 26.67\text{ mm}$)
* **Build Orientation Reason:** Laid flat on its side so bending stress acts perpendicular to layer lines rather than pulling layers apart (preventing layer cleavage).
* **Supports:** None used/required due to flat side orientation.
* **Wall Thickness / Perimeters:** 3 perimeter wall loops ($1.2\text{ mm}$ wall thickness).
* **Layer Thickness:** $0.20\text{ mm}$ (Standard Quality).
* **Infill:** 20% Grid infill.

---

## Show and Tell

**

The printed component was tested on the yellow motor mount artifact feature. The chamfered lips successfully flexed inward during insertion and snapped firmly into the rectangular side slot, holding the assembly together under light hand tension.

---

## Lessons Learned

1. **Layer Orientation is Critical for Flexures:** Printing cantilever arms vertically causes them to snap along layer lines under light bending. Laying the part flat on its side forces continuous filament strands down the length of the arm, drastically increasing strength.
2. **Feature Alignment Over Bulk Geometry:** Shortening the entire $Y$-depth from $0.350\text{ in}$ to $0.125\text{ in}$ to match the side window length simplified the CAD model while guaranteeing the locking teeth would engage.
3. **Engineered Allowances Prevent Jamming:** Leaving a $0.010\text{ in}$ clearance gap on mating surfaces accommodated PLA print tolerances perfectly, allowing a firm snap-fit without requiring forced over-insertion.
