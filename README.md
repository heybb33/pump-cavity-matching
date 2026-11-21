[README.md](https://github.com/user-attachments/files/35207550/README.md)
# Supplementary interactive model — Pump–cavity spatial matching at the crystal

**Version 1.0 · October 2026**

This folder contains a self-contained, offline interactive 3D visualization that accompanies the manuscript. It is intended to make the geometric relationships in the paper inspectable, not to provide a quantitative laser-oscillation simulation.

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

## 2. Quick start for reviewers

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

## 4. Package contents

| Path | Description |
|---|---|
| `interactive/index.html` | Self-contained offline interactive model (single file, all code and Three.js inlined). |
| `figures/FigS1_coaxial_vs_offaxis.png` | Static fallback: coaxial reference versus angular-mismatch state, English labels. |
| `figures/FigS2_combined.png` | Static fallback: combined cavity-axis and crystal-pose adjustment. |
| `figures/FigS3_interface.png` | Interface overview, including the control panel. |
| `S1_text_for_manuscript.md` | Draft supplementary text and figure captions for the manuscript. |
| `DEPLOY.md` | Recommended routes for hosting, DOI archiving, and journal submission. |
| `source/` | Editable source, vendored Three.js, and the single-file build script (for reproducibility; not needed to open the model). |
| `source/BUILD.md` | How to run the source version and rebuild the single-file page. |
| `LICENSE-NOTES.txt` | Provenance and license notes for the code and bundled libraries. |
| `README_CN.md` | Chinese version of this guide. |
| `CHECKSUMS.txt` | SHA-256 checksums for the delivered files. |

The figures are 3200 × 2000 px PNGs. They are provided so that reviewers who cannot run WebGL, or who prefer not to open an interactive file, can still evaluate the geometry.

---

## 5. If the interactive file does not open

Try, in order:

1. **Open with a current browser, not a PDF viewer or office suite.** Right-click the file → *Open with* → Chrome/Edge/Firefox.
2. **Check WebGL2.** Visit `chrome://gpu` (Chrome/Edge) or `about:support` (Firefox) and confirm that WebGL is enabled. A remote desktop or virtual machine may disable hardware acceleration; try a local browser.
3. **Unblock a downloaded file (Windows).** Right-click the HTML file → *Properties* → tick *Unblock* if present → *Apply*.
4. **Use a local server only as a fallback.** In the supplement folder, run `python -m http.server 8000` (Python 3) and open `http://localhost:8000/interactive/index.html`. This is not required for normal use; it is only a workaround for unusually restrictive browser policies.
5. **Use the static figures.** If the interactive page still cannot run, the PNG panels convey the main geometry and are suitable for review.

The single-file page was smoke-tested from a local `file://` URL in Chrome. Other current browsers are expected to work, but reviewers should use the static figures if their environment blocks WebGL or local scripts.

---

## 6. For the authors: submission and preservation

The most reliable way to let reviewers open the model is **not** to rely on an HTML attachment being rendered by the manuscript system. Use a combination:

1. **A hosted, citable copy.** Put `interactive/index.html` at a stable URL (GitHub Pages, Netlify, Cloudflare Pages, or an institutional page), and archive the same package on Zenodo or OSF to obtain a DOI. Cite the DOI and URL in the supplementary text.
2. **An offline copy in the supplement ZIP.** Include this folder as submitted supplementary software/data, with the README and static figures. This covers reviewers who download the ZIP and open it locally.
3. **Static fallback in the PDF supplement.** Include Fig. S1–S3 (and a short video if the journal supports it) so the geometry is assessable without running JavaScript.
4. **A journal-policy check.** Check the target journal’s supplementary-material instructions for accepted file types. Many systems accept PDF, images, spreadsheets, ZIP, and video but do not execute HTML/JavaScript. If HTML is not an accepted type, submit the ZIP as supplementary software/data and put the hosted DOI link in the manuscript’s data/software-availability statement.
5. **A double-blind-safe link.** During review, use an anonymized OSF view link or an anonymous repository mirror rather than a personal GitHub account. Replace it with the public DOI after acceptance if the journal requires it.

See `DEPLOY.md` for a step-by-step checklist.

---

## 7. Suggested citation

If the interactive model is cited or deposited, use the article’s supplementary-material citation and the archive DOI. A suitable form is:

> Interactive three-dimensional model of pump–cavity spatial matching at the crystal. Supplementary Software S1, Version 1.0. [DOI / URL to be inserted].

Please add the final DOI and author list before submission.

---

## 8. Contact

For questions about the model or the manuscript, contact the corresponding author. Please report the browser version and whether WebGL2 is available if you encounter a display problem.
