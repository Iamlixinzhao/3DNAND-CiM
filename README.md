# 3DNAND-CiM

## Probabilistic NAND readout demo

[Open the interactive demo](https://Iamlixinzhao.github.io/3DNAND-CiM/)

An English-language, browser-only animation of randomized word-line voltages and repeated current sensing in one short NAND string.

- 4 bits / 8 cells, using two complementary threshold-state cells per bit.
- Fixed query `1111`; click the Data bits to change mismatch positions.
- Adjustable low-read voltage and random-voltage scale.
- Animated sampling, whole-string current sensing, and count accumulation.
- Single-read and 500-read modes.

Open `index.html` locally or use the GitHub Pages link above. No installation, backend, or model download is needed.

**Scope:** This is an uncalibrated Level-1 MOS mechanism demonstration, not a validated 3D NAND simulator or a silicon measurement result. Animation timing does not represent hardware latency.

See [model assumptions](DEMO_MODEL.md) for electrical parameters, randomization, and limitations.
