[README.md](https://github.com/user-attachments/files/35207550/README.md)
# Supplementary interactive model — Pump–cavity spatial matching at the crystal

**Version 1.0 · October 2026**

This folder contains a self-contained, offline interactive 3D visualization . It is intended to make the geometric relationships in the paper inspectable, not to provide a quantitative laser-oscillation simulation.

---

## 1. What this is

The model shows a fixed incident pump beam and a separately adjustable cavity axis and crystal pose. The user can vary:

- the cavity-axis tilt and transverse position,
- the crystal tilt and three-dimensional translation,
- the crystal dimensions, beam-envelope widths, waist sizes, and display lengths,
- colors, opacities, line styles, labels, camera, and visible objects.

Two views are shown side by side: **(a)** the coaxial reference state and **(b)** the adjustable off-axis state. The display can be switched to a single large view.

The page is a single HTML file. It contains the Three.js renderer and all application code; it does **not** need Node.js, a local server, a package install, or an internet connection.

The page opens in the **author default view** captured from the locally saved settings (palette, crystal dimensions, camera, visible labels, and refractive indices). The “restore all defaults” command returns to this same view; it is not a factory preset. The coaxial-reference panel is still an unposed reference and does not inherit the saved cavity or crystal pose.

---

## 2. Quick start 

1. Unzip the supplement (if it arrived as a ZIP).
2. Open `interactive/index.html` by double-clicking it.
3. Use a current WebGL2-capable browser (Chrome, Edge, Firefox, or Safari). A desktop or laptop screen at 1440 × 900 or larger is recommended.
4. If the browser asks whether to allow local content, allow it. The file does not contact the network.

No installation, account, or command line is required.

### Two-minute tour

| Action | What it demonstrates |
|---|---|
| Click **Coaxial reference / 共轴参考** | The reference state: crystal upright, pump axis and cavity axis coincide, both waists inside the crystal. |
| Click **Angular mismatch / 角度失配** | Only the cavity axis is tilted and translated; the incident pump path stays fixed. |
| Click **Crystal pose / 晶体姿态变化** | Crystal tilt and 3D translation with the original outline retained. |
| Click **Combined control / 联合调控** | Cavity-axis and crystal-pose changes together. |
| Drag in the 3D view | Rotate (left button), pan (right button), zoom (wheel). |
| Open the right-hand panel | Change geometry, colors, opacity, labels, visibility, camera, and export settings. |
| Press **?** | In-page notes on controls, reference section, refraction, and scientific boundaries. |

The four preset animations can be paused and then edited manually. The timeline can be scrubbed; playback speed and looping are adjustable.

---

## 3. Scientific scope and limitations

Please read this section before interpreting the visualization.

- **This is a geometric and mode-envelope illustration, not a quantitative laser-oscillation simulation.** It does not compute oscillation thresholds, stability, mode competition, or mode-selection repeatability.
- **The cavity axis is a schematic input parameter.** No full resonator eigenmode is solved. The drawn cavity axis is not presented as a computed Gaussian eigenmode of the real cavity.
- **The low-order and high-order “HG” envelopes are smooth, same-family parameterized surfaces.** They are used only to compare transverse scales. They are not true multi-lobe Hermite–Gaussian intensity distributions, and their simultaneous display does not imply that both modes oscillate.
- **No angle-to-HG-order mapping is implied.** Changing the tilt angle does not automatically change the displayed mode order; the order is an independent display parameter.
- **The reference section is explicit.** The transverse offsets Δx_pc and Δy_pc are evaluated at the displayed reference plane z = z_ref. The angle θ is the angle between the two axis direction vectors. The model does not draw an undefined angle or distance between skew lines.
- **Refraction is an isotropic Snell model.** When enabled, both the pump and the cavity path refract at the crystal surfaces using separate refractive indices. No birefringence, walk-off, or material anisotropy is modeled unless such parameters are explicitly supplied; the current model does not supply them.
- **The pump incident path is fixed.** The incident segment before the crystal does not follow the cavity axis or the crystal motion. With refraction enabled, the internal and exiting segments are computed from the surface normal and are therefore allowed to differ from a single straight line.
- **Crystal translation is not mechanically equated to an equal pump–cavity offset.** The model distinguishes a change of the crystal relative to the beams from a change of the two optical axes relative to each other.

The phrase shown in the interface — “几何与模式包络示意，非定量激光振荡模拟” / “Geometric and mode-envelope illustration, not a quantitative laser-oscillation simulation” — is the intended interpretation.

---

## 8. Contact

For questions about the model or the manuscript, contact the corresponding author. Please report the browser version and whether WebGL2 is available if you encounter a display problem.
