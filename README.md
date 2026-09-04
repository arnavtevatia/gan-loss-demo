# GAN Loss Curves: Interactive Demo

**Live demo:** https://arnavtevatia.github.io/gan-loss-demo/

An interactive explainer for why the **non-saturating GAN loss** (−log D(G(z))) is used in practice, despite the original formulation converging to the same Nash equilibrium.

## The Core Problem

When D(G(z)) ≈ 0 early in training, the original generator loss

```
log(1 − D(G(z)))
```

produces a near-zero gradient — stalling the generator exactly when it needs the most guidance. The non-saturating alternative

```
−log(D(G(z)))
```

produces a large gradient in the same regime, enabling rapid early learning. Both losses reach the same Nash equilibrium; the difference is entirely in training dynamics.

## Demo Structure

The demo follows a 6-step pedagogical arc — explain, show, feel, summarize:

| Step | What it does |
|------|-------------|
| 1 | Introduce both loss formulations side by side |
| 2 | Isolate the saturation problem with live gradient meters and a pulsing warning at D(G(z)) ≈ 0 |
| 3 | Show that both losses converge to the same Nash equilibrium |
| 4 | Speed race: bar velocity proportional to gradient magnitude, so you see the practical consequence rather than just the math |
| 5 | Synthetic 2D training simulation showing how gradient differences compound into real divergence over epochs |
| 6 | Free exploration with a gradient magnitude view toggle that makes the flatness of the original loss near D = 0 unmistakable |

## Implementation Notes

The gradient meters display ∂L/∂D as a proxy for generator learning signal. The actual generator gradient depends on the full chain rule through D, which is noted in the formula panel. The demo ends with a one-sentence takeaway box summarizing the core conclusion.

## Author

Arnav Tevatia (at846)
