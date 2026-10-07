# Demo model and limitations

This demo computes whole-string DC current with a simplified Level-1 series-MOS model. It does not assume a `p^h` sensing probability.

## Electrical assumptions

| Parameter | Value |
| --- | --- |
| String size | 4 bits / 8 cells |
| High threshold | 5.312 V |
| Low threshold | -2.369 V |
| High-read voltage | 8 V |
| Bit-line voltage | 0.7 V |
| Sense threshold | 100 nA |
| KP | 200 µA/V² |
| W/L | 10 |
| Channel-length modulation | 0.02 V⁻¹ |
| Body connection | Tied to each cell's local source |

From BL to SL, each cell pair consists of a high-driven cell followed by a low-driven cell. For the fixed query `1111`, a matching bit stores `[HVT, LVT]`; a mismatching bit stores `[LVT, HVT]`. No claim is made that the WL driver arrangement has been demonstrated in silicon.

## Random reads and sensing

Each low-driven WL receives a fresh independent perturbation per read. The random variable is the sum of 12 independent uniforms minus 6, clipped to [-2, 2], then multiplied by sigma and added to the low-read voltage. This approximates Gaussian randomization. Sigma is the pre-clipping scale, not the exact post-clipping standard deviation. High-driven WLs remain fixed.

The solver propagates the voltage drops required for a trial current from SL to BL and uses bisection to find the string current at VBL = 0.7 V. The same fixed-current calculation at 100 nA determines sensed-on versus below-threshold. A read contributes one count only when the whole-string current reaches the sensing threshold.

A deterministic seed of 42 is restored when the settings or stored bits change or when Reset is pressed, allowing paired comparisons across conditions. Runs from the same seed are reproducible, not independent experimental trials.

## Limitations

- Not calibrated to measured string I–V curves.
- No subthreshold leakage, charge trapping dynamics, retention, wear, parasitic capacitance, or sensing-circuit noise.
- Local body ties and the MOS geometry are assumptions, not a complete vertical NAND structure.
- Moving markers illustrate the string sensing outcome, not carrier transport or independently sensed cell states.
- Animation timing is not a prediction of hardware read latency.
- A single-string count does not establish end-to-end retrieval accuracy, array scalability, or energy advantage.

No collaborator spreadsheets, raw measurement data, or research datasets are included in this repository update.
