# 🔬 Prime Explorer Frontier

**An interactive 3D laboratory for investigating geometric patterns in prime numbers, elliptic curve properties, and classical factorization methods.**

![Prime Explorer Screenshot](Isocahedron%20Soccer%20Ball%20Pattern.png)

## What Is This?

Prime Explorer Frontier is a browser-based research tool that maps integers onto 3D surfaces to explore whether geometric visualizations can reveal hidden patterns in number theory. It began as a simple prime visualization and evolved into a comprehensive hypothesis-testing laboratory with elliptic curve analysis and classical factorization exploration.

**Core Questions:**
- Can geometric positioning reveal structure in prime distribution that could inform factorization?
- Can elliptic curve invariants leak factor information?
- Where exactly do classical methods succeed and fail?

**Research Outcome:** Our systematic investigation established clear **negative results and structural boundaries** — geometry cannot encode multiplicative structure in exploitable ways, EC correlations reduce to scaling artifacts, and classical "partial inversion" collapses to known methods (Pollard p-1). The tool proves these rigorously rather than assuming them.

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

### 🧪 Statistical Validation Suite (FRONTIER)
Don't trust your eyes — test your hypotheses:
- **Base Rate Correction** — Compare observed vs expected
- **Permutation Testing** — 1000 label shuffles for p-values
- **N-Scaling Tests** — Does the effect persist at larger N?
- **Radius Sensitivity** — Is it robust to parameter changes?
- **Cross-Mode Validation** — Test across all mapping modes

### 🔷 Elliptic Curve Mode (NEW)
BSD conjecture verification and EC property exploration:
- **6 Preloaded Curves** — 37a1, 389a1, 681b1, 433a1, 5077a1, 11a1
- **Reduction Type Coloring** — Bad (red), Supersingular (blue), Ordinary (yellow)
- **Sha Test Candidate Filter** — Identify primes for BSD testing
- **Cross-Curve Comparison** — Find common/divergent supersingular primes
- **FRONTIER Experiment** — Test EC additivity hypothesis: does a_n correlate with a_p + a_q?

### 🔑 Order/GCD Telemetry (NEW)
Pollard p-1 style factorization explorer:
- **4 Heuristics** — Factorial (k!), Primorial, LCM(1..k), Power-smooth
- **Step Mode** — Watch gcd evolve step-by-step
- **Test Case Generators** — Smooth p-1 (easy) vs RSA-style (hard)
- **Attack History** — Track successes and failures
- **Educational Value** — Viscerally understand why RSA works

### 🔍 Research Tools
- **Resonance Spectrum** — Factor distance analysis
- **Neighborhood Lens** — Local geometric structure
- **Error Vector Explorer** — Test multiplicative additivity
- **Multiplication Lab** — Interactive Φ(p×q) vs Φ(p)+Φ(q) testing
- **Factor Finder** — Instant factorization with visualization
- **Constraint Visualizer** — See how partial information shrinks search space

## Installation

No installation required! It's a single HTML file.

```bash
# Clone the repo
git clone https://github.com/holbizmetrics/Prime-Explorer.git

# Open in browser
open prime%20explorer.html
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

4. **Try EC Mode:**
   - Enable "Elliptic Curve Mode"
   - Select curve 681b1 (Sha=9)
   - Filter by "Sha test candidates" → observe empty sphere
   - Click "📊 Stats" to see the BSD verification message

5. **Try Order/GCD:**
   - Click "🎲 Smooth p-1" → "▶ Run Attack" → watch it succeed
   - Click "🎲 RSA-style" → "▶ Run Attack" → watch it fail

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

## Research Findings

Our investigation established several key results:

### Negative Results (Factorization)

| Approach | Result | Why |
|----------|--------|-----|
| Geometric embeddings | ❌ NULL | Linear mapping cannot capture non-linear multiplication |
| Digit/base transforms | ❌ NULL | Representational, not structural |
| EC correlation (a_n vs a_p+a_q) | ❌ NULL | Initial signal was scaling artifact (Hasse bound) |
| (ℤ/nℤ)* visualization | ❌ NULL | Product structure algebraically present but computationally hidden |
| "Partial inversion" | → Pollard p-1 | Reduces to known order/smoothness methods |

### Positive Results (BSD Verification)

| Feature | Contribution |
|---------|--------------|
| Reduction type visualization | Correct bad/ordinary/supersingular coloring |
| Sha test candidate identification | Precise filter with proper 3-condition logic |
| 681b1 case verification | Visual proof that p=3 has bad reduction → no Sha test cases |
| "+1" structural insight | Confirms normalization origin, not Sha leakage |

### The Factor Proximity Effect

We tested whether prime factors of semiprimes are geometrically closer to the product's position:

| Surface | Hit Rate | Expected | Verdict |
|---------|----------|----------|---------|
| Sphere | 9.1% | 5% | Weak effect |
| Torus | 8.3% | 5% | Weak effect |
| **Helix** | **2.0%** | 5% | **No effect** |

**Key Insight:** The effect is caused by **latitude correlation**, not factor encoding. Surfaces with latitude (Sphere, Torus, Cylinder) show it; the Helix (pure linear position) eliminates it entirely.

**Why it's not exploitable:**
- Only ~9% of semiprimes show the effect
- Cannot predict which ones
- Effect only confirms factors you already know

### Structural Boundaries Identified

| Boundary | Interpretation |
|----------|----------------|
| Geometry cannot reveal hidden multiplicative structure | Product structure is information-theoretically obscured |
| Digit/base changes add no new arithmetic content | Representational, not structural |
| Classical "partial inversion" collapses to order/smoothness | No new lever beyond known algorithms |
| Visualization is diagnostic, not generative | Excellent for falsification, not extraction |
| EC data does not leak factor information | Consistent with cryptographic expectations |

## EC Mode: BSD Verification

The EC Mode overlay colors primes by their reduction type for a given elliptic curve:

```
🔴 Bad reduction      — p divides conductor
🔵 Supersingular      — a_p = 0 (good reduction)
🟡 Ordinary           — a_p ≠ 0 (good reduction)
⚫ Unknown            — no data available
```

### Sha Test Candidate Logic

A prime p is a Sha test candidate if ALL THREE conditions hold:
1. `p | Sha` — p divides the Shafarevich-Tate group order
2. `p ∤ conductor` — good reduction at p
3. `a_p = 0` — supersingular at p

**681b1 Example (Sha = 9):**
- Only p=3 divides Sha=9
- But 3 | 681 (conductor) → bad reduction
- **Result:** No Sha test candidates exist
- **Implication:** The "+1" in BSD formulas is structural (Frobenius normalization)

## Order/GCD Telemetry: Pollard p-1 Explorer

This panel lets you **see** why Pollard p-1 works on some numbers and fails on others:

### The Algorithm
```
a = 2
for k = 2 to bound:
    a = a^(exponent(k)) mod n
    g = gcd(a - 1, n)
    if 1 < g < n: return g  // Factor found!
```

### Heuristics for exponent(k)
| Heuristic | Exponent | Best For |
|-----------|----------|----------|
| Factorial | k | General smooth p-1 |
| Primorial | p_k (k-th prime) | Squarefree p-1 |
| LCM | lcm(1..k) | Theoretically optimal |
| Power-smooth | prime powers ≤ bound | Highly composite p-1 |

### Expected Results
- **Smooth p-1 semiprimes:** Factor found quickly (k < 100)
- **RSA-style semiprimes:** No factor found (would need k ≈ largest prime factor of p-1)

This formally closes the "partial inversion" intuition: it's Pollard p-1 (1974), and it works exactly as theory predicts.

## Validation Verdicts

| Verdict | Meaning |
|---------|---------|
| 🏆 **DISCOVERY** | Effect is statistically significant and robust across tests |
| ⚠️ **INCONCLUSIVE** | Some evidence, but not robust — investigate further |
| 🔍 **WEAK** | Single test passed — likely artifact |
| ❌ **NULL** | No effect detected — hypothesis falsified |

## Recommended Configurations

| Goal | Surface | Mode | Method |
|------|---------|------|--------|
| See divisibility structure | Torus | generic | CRT Residue (210×143) |
| Factor-based bands | Sphere | generic | SPF Bands |
| Direct factorization encoding | Sphere | generic | Valuation 3D |
| Prime sequence patterns | Sphere | primeIndex | spiral |
| Smooth number clustering | Sphere | generic | Smoothness |
| BSD reduction visualization | Sphere | generic | spiral + EC Mode |

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
│  - Sphere, Torus, Helix, Klein, Trefoil, etc.          │
├─────────────────────────────────────────────────────────┤
│  TopologyAnalyzer   Statistical validation (FRONTIER)   │
│  - analyze(), permutationTest(), runFullValidation()   │
├─────────────────────────────────────────────────────────┤
│  EC Mode Classes    Elliptic curve analysis             │
│  - EllipticCurveData, ECModeAnalyzer                   │
│  - SemiprimeECAnalyzer, FRONTIERExperiment             │
├─────────────────────────────────────────────────────────┤
│  OrderGCDTelemetry  Pollard p-1 exploration             │
│  - runAttack(), stepMode, smoothness estimation        │
├─────────────────────────────────────────────────────────┤
│  PrimeExplorer      Main controller + rendering         │
│  - generatePoints(), render(), event handlers          │
└─────────────────────────────────────────────────────────┘
```

## Performance Notes

- **N = 5000** runs smoothly on most machines
- **Color by Hub** was optimized with caching — now O(n) per frame instead of O(n²)
- **Validation tests** may take a few seconds for permutation testing (1000 iterations)
- **Order/GCD attacks** are instant for reasonable bounds (< 500)

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
- Additional elliptic curves with a_p data
- Statistical tests
- Performance optimizations
- Bug fixes

## License

MIT License — use freely for research, education, or curiosity.

## Acknowledgments

Built through collaborative exploration between human researcher and AI assistant, using:
- ADEIS methodology (Attune, Derive, Execute, Inhabit, Ship)
- FRONTIER falsification framework
- Kernel coherence principles

The tool embodies the principle that **rigorous falsification is as valuable as discovery** — knowing what doesn't work is progress.

---

## The Real Outcome

You started with:
> "What if geometry sees what arithmetic hides?"

You ended with:
> "Geometry can *test*, *filter*, and *falsify* — but it cannot *extract* hidden multiplicative structure."

**That's a clean scientific result, not a disappointment.**

The primary contribution is not a new algorithm, but a **map of where not to look — and why**.

---

**Questions?** Open an issue or explore the code — it's heavily commented.

*"The goal isn't to prove a hypothesis works. The goal is to learn when it does and when it doesn't."*
