# The Ising model: an interactive introduction

An interactive, single-file web demo introducing the Ising model, its thermodynamics and its quantities of interest. It is based on lecture notes by Sang Hoon Lee for Chapter 2 (part 1), which follow K. Christensen and N. R. Moloney, *Complexity and Criticality* (2005). It is a companion to the percolation demos (square lattice, networks and the Bethe lattice).

Everything runs in the browser. There is no build step, no server and no dependencies beyond an optional web font. Units are k<sub>B</sub> = 1 and J = 1.

## Running it

Open `index.html` in any modern browser (Chrome, Edge, Firefox or Safari).

To publish it with GitHub Pages, push this repository, then go to **Settings → Pages**, choose **Deploy from a branch**, and select the branch and the root folder. The page will be served at `https://<user>.github.io/<repository>/`.

## What the page contains

**Live lattice.** A two-dimensional Ising model on an 8 × 8 to 256 × 256 periodic square lattice.

- Controls: temperature T/T<sub>c</sub> with presets matching the lecture snapshots (0.7, 0.99, 1, 1.2, 1.5 and 4 T<sub>c</sub>), an external field H, the update rule (Metropolis, or Wolff clusters at H = 0), the speed, and random or fully aligned starts.
- Readouts: m, the time average of |m|, Onsager's m<sub>0</sub>(T), and the energy per spin.
- Charts: m over time, the distribution of m, and the spin–spin correlation function g(r) on log–log axes with the r<sup>−1/4</sup> decay expected at T<sub>c</sub>.

**Defining the Ising model.** A clickable 5 × 5 lattice with free boundaries for E = −J Σ s<sub>i</sub>s<sub>j</sub> − H Σ s<sub>i</sub>. It has a ferromagnet or antiferromagnet switch and a field slider. Bonds are colored by their energy, and readouts give E<sub>int</sub>, E<sub>ext</sub>, M and the pair counts, next to the table of pair energies.

**Statistical mechanics by exact enumeration.** Every microstate of a 3 × 3, 4 × 4 or 5 × 5 periodic lattice (up to 33 554 432 states) is summed with a Gray code, for the Ising model or for non-interacting spins. The charts show:

- m(T), χ(T), c(T), f, ε and S/N against T
- m(H) against H
- the distribution P(M)

The response functions are computed both as derivatives and from fluctuations, which checks k<sub>B</sub>Tχ = (⟨M²⟩ − ⟨M⟩²)/N and k<sub>B</sub>T²c = (⟨E²⟩ − ⟨E⟩²)/N. A table lists the thermodynamic relations, followed by the argument that a finite system has no phase transition.

**Non-interacting spins.** The closed forms Z = [2 cosh βH]<sup>N</sup>, m = tanh(βH), χ = β sech²(βH), ε = −H tanh(βH) and c = (βH)² sech²(βH). It also shows the binomial distribution of m for N = 16, 256 and 4 096, with relative fluctuations csch(βH)/√N.

**Quantities of interest near T<sub>c</sub>.**

- Wolff-algorithm simulations of 16 × 16, 32 × 32 and 64 × 64 lattices across T<sub>c</sub> = 2/ln(1 + √2)
- ⟨|m|⟩, χ, c and ε against T, compared with Onsager's and Yang's exact infinite-lattice results
- finite-size scaling at T<sub>c</sub> for β/ν and γ/ν
- a table of the exponents α, β, γ, δ, ν and η for the 2D Ising model, mean-field theory and 2D percolation

**Symmetry breaking.** Why ⟨M⟩ = 0 for any finite system at H = 0, a table of P<sub>{s<sub>i</sub>}</sub>/P<sub>{−s<sub>i</sub>}</sub> = exp(2βHM) against N showing that the order of the limits H → 0 and N → ∞ matters, and a button that shows an 8 × 8 lattice flipping between +m and −m.

## Methods

| Topic | Approach |
| --- | --- |
| Metropolis | Checkerboard sweeps with tabulated acceptance probabilities, any H |
| Wolff | Single-cluster updates with bond probability 1 − e<sup>−2J/k<sub>B</sub>T</sup>, H = 0 only; a "sweep" flips at least N spins |
| Exact enumeration | Gray-code walk through all 2<sup>N</sup> states, one spin flip per step, building the joint histogram of bond sum and magnetization; all averages at any T, H and J follow from it |
| Exact infinite lattice | Onsager's energy through the complete elliptic integral (computed with the arithmetic–geometric mean), the specific heat by differentiating it, and Yang's spontaneous magnetization |
| Susceptibility in the sweep | N(⟨m²⟩ − ⟨|m|⟩²)/k<sub>B</sub>T, and N⟨m²⟩/k<sub>B</sub>T for finite-size scaling at T<sub>c</sub> |

## Files

```
index.html   the complete demo (HTML, CSS and JavaScript in one file)
README.md    this file
```

## Performance

The temperature sweep runs in small chunks after the page loads and takes under a minute on a laptop. The 5 × 5 enumeration takes a few seconds. A 256 × 256 live lattice at 16 sweeps per frame is the heaviest setting.

## References

**Key reference.** K. Christensen and N. R. Moloney, *Complexity and Criticality*, Imperial College Press, London (2005), Chapter 2.

1. E. Ising, "Beitrag zur Theorie des Ferromagnetismus," *Z. Phys.* **31**, 253 (1925).
2. S. G. Brush, "History of the Lenz–Ising model," *Rev. Mod. Phys.* **39**, 883 (1967).
3. L. Onsager, "Crystal statistics. I. A two-dimensional model with an order-disorder transition," *Phys. Rev.* **65**, 117 (1944).
4. C. N. Yang, "The spontaneous magnetization of a two-dimensional Ising model," *Phys. Rev.* **85**, 808 (1952).
5. N. Metropolis, A. W. Rosenbluth, M. N. Rosenbluth, A. H. Teller and E. Teller, "Equation of state calculations by fast computing machines," *J. Chem. Phys.* **21**, 1087 (1953).
6. U. Wolff, "Collective Monte Carlo updating for spin systems," *Phys. Rev. Lett.* **62**, 361 (1989).
7. D. V. Schroeder, *An Introduction to Thermal Physics*, Addison-Wesley (2000), Chapter 6.
8. N. Goldenfeld, *Lectures on Phase Transitions and the Renormalization Group*, Addison-Wesley (1992).

## Credits

Lecture notes: Sang Hoon Lee.

Created by Claude Opus 5.5.
