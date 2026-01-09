# 🔬 Prime Explorer Frontier

**An interactive 3D laboratory for investigating geometric patterns in prime numbers.**

![Prime Explorer Screenshot](Isocahedron%20Soccer%20Ball%20Pattern.png)
```

## Option 2: Rename the file (cleaner)

Rename the image to remove spaces:
```
Isocahedron-Soccer-Ball-Pattern.png

## What Is This?

Prime Explorer Frontier is a browser-based research tool that maps integers onto 3D surfaces to explore whether geometric visualizations can reveal hidden patterns in number theory. It began as a simple prime visualization and evolved into a comprehensive hypothesis-testing laboratory.

**Core Question:** Can geometric positioning reveal structure in prime distribution that could inform factorization?

**Spoiler:** Our research suggests geometry cannot encode multiplicative structure in exploitable ways — but the tool proves this rigorously rather than assuming it.

## Features

### 🌐 12 Surface Geometries
Sphere, Torus, Helix, Double Helix, Triple Helix, Möbius Strip, Klein Bottle, Trefoil Knot, Cylinder, Cone, and more. Each reveals different structural properties.

### 🎯 5 Mapping Modes
Control *what* gets mapped:
- **Generic** — Raw integer value
- **Native** — Geometry-specific optimal mapping
- **Prime Index π(n)** — Position in prime sequence  
- **Gap-Based** — Incorporates prime gap information
- **Residue Fingerprint** — CRT-encoded position

### 📐 12 Mapping Methods
Control *how* values become coordinates:
- Golden Spiral, Mod 6/30 wheels, CRT Residue (210×143)
- Valuation 3D, SPF Bands, Log Helix, Smoothness
- And more...

### 🧪 Statistical Validation Suite
Don't trust your eyes — test your hypotheses:
- **Base Rate Correction** — Compare observed vs expected
- **Permutation Testing** — 1000 label shuffles for p-values
- **N-Scaling Tests** — Does the effect persist at larger N?
- **Radius Sensitivity** — Is it robust to parameter changes?
- **Cross-Mode Validation** — Test across all mapping modes

### 🔍 Research Tools
- **Resonance Spectrum** — Factor distance analysis
- **Neighborhood Lens** — Local geometric structure
- **Error Vector Explorer** — Test multiplicative additivity
- **Multiplication Lab** — Interactive Φ(p×q) vs Φ(p)+Φ(q) testing
- **Factor Finder** — Instant factorization with visualization

## Installation

No installation required! It's a single HTML file.

```bash
# Clone the repo
git clone https://github.com/yourusername/prime-explorer-frontier.git

# Open in browser
open ultimate_prime_explorer_frontier.html
```

Or just download the HTML file and double-click it.

## Quick Start

1. **Explore visually:**
   - Select a Surface (try Torus)
   - Select a Mapping Method (try CRT Residue)
   - Drag to rotate, scroll to zoom

2. **Click any point** to see its number and factorization

3. **Test a hypothesis:**
   - Click "🔬 RUN FULL VALIDATION" in the Hypothesis Validator
   - Check the verdict: DISCOVERY / INCONCLUSIVE / NULL

## The Three-Stage Pipeline

```
MODE (what is n?) → METHOD (n → θ,φ) → SURFACE (θ,φ → xyz)
```

**Example:** Prime Index mode + Mod 30 method + Torus surface

```
n = 541 (the 100th prime)
  → Mode transforms: effectiveN = 100
  → Method applies: θ = (100 % 30) × (π/15)
  → Surface projects: (θ, φ) → (x, y, z) on torus
```

All modes except "native" compose with the method dropdown. Native mode bypasses it for geometry-optimal mapping.

## Recommended Configurations

| Goal | Surface | Mode | Method |
|------|---------|------|--------|
| See divisibility structure | Torus | generic | CRT Residue (210×143) |
| Factor-based bands | Sphere | generic | SPF Bands |
| Direct factorization encoding | Sphere | generic | Valuation 3D |
| Prime sequence patterns | Sphere | primeIndex | spiral |
| Smooth number clustering | Sphere | generic | Smoothness |

## Validation Verdicts

| Verdict | Meaning |
|---------|---------|
| 🏆 **DISCOVERY** | Effect is statistically significant and robust across tests |
| ⚠️ **INCONCLUSIVE** | Some evidence, but not robust — investigate further |
| 🔍 **WEAK** | Single test passed — likely artifact |
| ❌ **NULL** | No effect detected — hypothesis falsified |

## Research Findings

Our investigation established several key results:

1. **Geometry cannot encode multiplicative structure** — The mapping from n → position is inherently linear, while multiplication is non-linear. No geometric arrangement can make p × q predictable from positions of p and q.

2. **Visual "clustering" is usually density artifact** — Composites appear to cluster simply because there are more of them (~88% vs ~12% primes). Statistical tests distinguish real patterns from base-rate effects.

3. **DoubleHelix separation is by design** — The apparent prime/composite separation on double helix is built into the geometry, not a discovered pattern.

4. **CRT mappings reveal divisibility, not factorization** — Numbers sharing residues cluster, but this doesn't help factor unknown numbers.

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│  PrimeMath          Static math utilities               │
│  - isPrime, factorize, valuation, smoothness           │
├─────────────────────────────────────────────────────────┤
│  MappingStrategy    n → (θ, φ) transformations          │
│  - transformN(), map(), nativeMapping()                │
├─────────────────────────────────────────────────────────┤
│  Surface Classes    (θ, φ) → (x, y, z) projections      │
│  - Sphere, Torus, Helix, etc.                          │
├─────────────────────────────────────────────────────────┤
│  TopologyAnalyzer   Statistical validation              │
│  - analyze(), permutationTest(), runFullValidation()   │
├─────────────────────────────────────────────────────────┤
│  PrimeExplorer      Main controller + rendering         │
│  - generatePoints(), render(), event handlers          │
└─────────────────────────────────────────────────────────┘
```

## Performance Notes

- **N = 5000** runs smoothly on most machines
- **Color by Hub** was optimized with caching — now O(n) per frame instead of O(n²)
- **Validation tests** may take a few seconds for permutation testing (1000 iterations)

## Browser Compatibility

Tested on:
- Chrome 120+
- Firefox 120+
- Safari 17+
- Edge 120+

Requires JavaScript enabled. Uses Canvas 2D (no WebGL dependency).

## Contributing

This is a research tool that evolved through iterative investigation. Contributions welcome:

- New surface geometries
- New mapping methods
- Statistical tests
- Performance optimizations
- Bug fixes

## License

MIT License — use freely for research, education, or curiosity.

## Acknowledgments

Built through collaborative exploration between human researcher and AI assistant, using:
- ADEIS methodology (Attune, Derive, Execute, Inhabit, Ship)
- APEX-EVE cognitive architecture
- Kernel v4 coherent generation pipeline

The tool embodies the principle that **rigorous falsification is as valuable as discovery** — knowing what doesn't work is progress.

---

**Questions?** Open an issue or explore the code — it's heavily commented.

*"The goal isn't to prove a hypothesis works. The goal is to learn when it does and when it doesn't."*
