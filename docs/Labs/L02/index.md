# Lab 2 – Print Something Small

## Objective
The goal of this assignment was to select, preprocess, and 3D print a small functional or decorative object adhering to strict manufacturing size and print time constraints, while documenting the end-to-end design-to-print workflow.

---

## Download

### Item Selection & Justification
For this assignment, I selected an emergency whistle model to test printing thin-walled, hollow functional geometries with internal air channels without requiring support material.

- **Selected Model:** Emergency Whistle (`cat_bookmark_v2.stl` / mini travel set / whistle model).
- **Reasons for Selection:** 
  - Meets all spatial stipulations (under 0.25 inches tall and under 2x2 inches).
  - Features internal cavity mechanics to test print tolerances.
  - Quick print time well below the 1.5-hour threshold.

### Alternative Consideration
Before selecting the whistle, I considered downloading and printing other models:
- **Helldivers Skull (`helldivers2_skull v1.obj`):** Rejected due to complex overhangs that would have required support enforcement and increased post-processing time.
- **Mini Travel Container & Lid:** Considered as a backup multi-part print option, but the whistle was prioritized for its single-body functional test.

![Downloaded Models Overview](../../docs/image.png)
*Figure 1: Overview of downloaded candidate STL/OBJ files prepared for slicing.*

---

## Preprocessor

The downloaded STL file was loaded into **PrusaSlicer** (v2.9.6) to prepare the build setup and output the G-code for the UNCC print farm.

![PrusaSlicer Setup & Dimensions](../../docs/Screenshot%202026-08-29%20153924.png)
*Figure 2: Whistle layout, dimensions, and slicing metrics in PrusaSlicer.*

### Slicer Configuration & Metrics
- **Slicer Software:** PrusaSlicer 2.9.6
- **Printer Profile:** Prusa CORE One 0.4 nozzle
- **Print Profile:** 0.20mm SPEED
- **Material:** Generic PLA
- **Part Dimensions:** $41.4\text{ mm} \times 14.3\text{ mm} \times 3.5\text{ mm}$ (fits well within the 2 in x 2 in x 0.25 in envelope)
- **Infill:** 15%
- **Supports:** None / For support enforcers only
- **Estimated Filament Used:** 8.22 g (2.76 m / 6628.75 mm³)

### Preprocessor Decisions & Analysis
1. **Build Orientation:**
   - The part was oriented completely flat on the build plate along its largest face. This maximized bed contact area for optimal adhesion and eliminated the need for support material inside or outside the air channel.

2. **Supports:**
   - **No supports were used.** The internal whistle cavity and outer profile were oriented so that all angles bridged naturally without sagging.

3. **Scaling:**
   - No scaling was required as the model natively measured $41.4\text{ mm} \times 14.3\text{ mm} \times 3.5\text{ mm}$, staying strictly below the $0.25\text{ inch}$ ($\sim 6.35\text{ mm}$) height limit and $2\text{ inch}$ ($\sim 50.8\text{ mm}$) length/width limits.

4. **Process & Mistakes:**
   - Initial check revealed potential adhesion risks if printed near build plate edges. The part was moved directly to the center of the print bed to leverage optimal bed heating.

---

## Print

### Execution Details
- **Printer Assigned:** UNCC Print Farm - Printer #04 (Prusa CORE One FDM printer)
- **Material Used:** PLA (Orange / Green multi-part platform print)
- **Print Partner(s):** Printed on the same build platform alongside lab partners to optimize bed space and print efficiency.

### Process Photos
![Printed Whistle](../../docs/IMG_4056.jpeg)
*Figure 3: Completed 3D printed whistle post-printing.*

![All Printed Items](../../docs/image.png)
*Figure 4: Complete batch of 3D printed objects printed on the shared build plate.*

---

## Lessons Learned

Throughout the download, slicing, and printing process, four key technical lessons were identified:

1. **Bed Orientation & Surface Contact:** Orienting planar objects flat against the print bed eliminates the overhead of support structures and prevents warping on thin-profile PLA prints.
2. **Multi-Part Batch Efficiency:** Combining multiple small prints onto a single build plate significantly reduces printer setup overhead and maximizes machine uptime across the farm.
3. **Dimensional Constraint Checking:** Verifying absolute bounding box dimensions in the slicer prior to exporting G-code ensures compliance with physical limits without needing manual rescale steps.
4. **Tolerance for Internal Cavities:** FDM bridging capabilities allow small internal chambers (like whistle resonance chambers) to print cleanly without infill or internal supports blocking airflow.

### Total Time Elapsed
- **Total Time:** ~1 hour 15 minutes (comprising 15 minutes downloading/slicing, 35 minutes active print time, and 25 minutes documentation/post-inspection).

### Acknowledgments
- Thanks to my lab partner(s) for coordinating platform space
---

## Resources

- [PrusaSlicer User Manual](https://help.prusa3d.com/) – Slicing settings and layer height configuration guidelines.
- [Printables Free 3D Models](https://www.printables.com/) – Source repository for open-source model downloads.
