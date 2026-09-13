# Magnetic Top Panel - Small Panel Variant

A Voron 2.4 top-panel corner system for **undersized 3 mm polycarbonate panels**. It is based on Printopal's [Magnetic top panel](https://github.com/VoronDesign/VoronUsers/tree/main/printer_mods/Printopal/Magnetic_top_panel), but moves the magnetic interface outside the panel footprint and captures the panel from above.

![Installed overview](Images/installed_overview.jpg)

## Why this variant exists

The original magnetic-top-panel design places the upper magnet carrier underneath the panel. If the top panel is slightly undersized, that carrier can consume the limited gap between the panel and frame and may require thicker sealing foam.

This variant changes the geometry in a functional way:

- the **frame magnet is moved to the center of the four extrusion locating features**;
- the panel-side corner is **reversed into a top cap**;
- the cap sits on top of a **3.0 mm PC panel**, with a 1.0 mm roof and a 3.0 mm drop beside the panel;
- the magnet sits immediately outside the panel corner, so there is no magnet carrier trapped underneath the sheet;
- larger **10 x 3 mm magnets** are used for a firm, positive hold.

![Corner installed](Images/installed_corner.jpg)

## Tested dimensions

This exact STL set was physically tested on a Voron 2.4 with:

| Parameter | Value |
|---|---:|
| Top panel | 434 x 434 mm |
| Panel thickness | 3.0 mm |
| Upward-extrusion center spacing | 441 x 441 mm |
| Panel inset per side | 3.5 mm |
| Magnets | 10 x 3 mm |
| Magnet pocket | 10.1 mm diameter x 3.0 mm |

The inset is simply:

`inset = (extrusion-center spacing - panel dimension) / 2`

For the tested build: `(441 - 434) / 2 = 3.5 mm`.

The supplied parametric OpenSCAD source exposes the X/Y panel and frame dimensions independently if your panel is different.

## BOM

- 4x `frame_corner_10x3`
- 4x `panel_corner_top_cap_10x3`
- 8x neodymium magnets, **10 mm diameter x 3 mm thick**
- Existing 3 mm top panel
- Optional: a small amount of VHB, epoxy, or another suitable adhesive if you want the four top caps to remain attached to the panel when it is lifted off

## Printing

Recommended: **ABS or ASA**, 100% scale, standard Voron structural-part settings. No supports are required with the supplied STL orientations.

- `frame_corner_10x3_x4.stl`: print base-down as supplied.
- `[a]_panel_corner_top_cap_10x3_x4.stl`: supplied **roof-down**, so the 1 mm top face is on the build plate and the recess prints upward.
- Do not scale the model to compensate for ABS shrinkage; calibrate dimensional/XY compensation instead.

## Assembly

1. Print four of each part.
2. Dry-fit all eight 10 x 3 mm magnets before bonding anything.
3. Check polarity carefully: every top-cap magnet must attract its matching frame magnet.
4. Install the four frame corners.
5. Place the centered 434 mm panel into the four top caps. The cap recess is exactly 3.0 mm deep.
6. If desired, bond the cap to the panel so the complete top lifts off as one assembly. VHB or epoxy avoids the whitening/blooming that some CA glues can produce on clear polycarbonate.
7. Place the panel on the printer; the magnets align over the frame corners automatically.

![Magnet detail](Images/magnet_detail.jpg)

## CAD / adapting to another panel

`CAD/panel_corner_top_cap_10x3_parametric.scad` contains variables for:

- panel width/depth;
- extrusion-center spacing X/Y;
- panel thickness;
- roof thickness;
- magnet diameter and clearance.

The default values reproduce the physically tested 434/441 mm version. STEP exports of the final tested geometry are also included.

## Attribution and license

This is a derivative of **Printopal's Magnetic top panel** from the VoronUsers repository. The original geometry, concept, and accepted upstream mod are credited to Printopal.

The changes in this variant were developed around an undersized-panel fit problem and physically tested on a Voron 2.4. This derivative is released under **GPL-3.0**, consistent with the upstream VoronUsers repository and original mod.
