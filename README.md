# Variable-Speed System 3D Service Trainer

An interactive, browser-based 3D explorer of a **variable-speed split-system air conditioner** (outdoor condensing unit), built for training HVAC technicians.

No build step: plain HTML/CSS/ES modules with [three.js](https://threejs.org) loaded from a CDN.

## Features

- **24 modeled components** grouped by system: cabinet & structure, airflow, refrigerant circuit, compressor, electrical & controls.
- **Exploded views**
  - *Exploded*: a cascading, staggered service-order explosion with a scrub slider.
  - *Parts table*: every component lays itself out on the shop floor.
  - Numbered **callouts** with leader lines that de-overlap themselves (like a service-manual parts breakdown).
- **Part detail cards**: what it does, key specs, common failures, how to test, safety warnings and pro tips.
- **Guided Teardown**: an 8-step disassembly walk-through, starting with lockout/tagout and inverter capacitor discharge.
- **Refrigerant Flow**: animated cooling cycle (discharge, condensing, liquid, suction) with color-coded piping.
- **Quiz**: *Locate it* (click the named part) and *Name it* (identify the highlighted part).
- **View tools**: X-ray cabinet, section cut (left/right, front/back, diagonal), blueprint render, turntable, isolate/hide parts.
- Works on desktop and mobile (touch orbit/pinch, bottom-sheet details).

### Keyboard

`E` explode/assemble · `L` callouts · `X` x-ray · `C` section · `B` blueprint · `T` turntable · `R` reset view · `Esc` deselect · `←/→` teardown steps

## Run locally

ES modules need to be served over HTTP:

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

Or enable GitHub Pages for the repository (root folder) — it works as-is.

## Project layout

```
index.html        UI shell + import map
css/style.css     styles (responsive)
js/parts.js       procedural geometry for every part + explode vectors
js/content.js     training content, teardown steps, flow legend
js/main.js        scene, interaction, explode system, modes
```

To add or edit training content, change `js/content.js`. To adjust a part's exploded position, edit its `explode` vector in the `PART_DEFS` table in `js/parts.js`.

## Disclaimer

This is a **representational training model**. Geometry is approximate and not to OEM scale or exact layout, and typical values in the content are general field guidance. Always follow the manufacturer's installation and service literature and the wiring diagram for the specific model and serial number being serviced.

Trane and Spine Fin are trademarks of their respective owners. This project is not affiliated with or endorsed by Trane.
