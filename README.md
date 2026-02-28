# Ashraf-s-Stable-Testosterone-Flight-Calculator-week-by-week-
ASAM by Ashrafk.salim — pharmacokinetic calculator modeling testosterone ester serum accumulation week by week. Input your stack, set your threshold Θ, get ascent/plateau/taper phases auto-designed with exact clearance timing. No guesswork. No crashes.


# ASAM — Ashrafk.salim Serum Accumulation Model

> A pharmacokinetic calculator for modeling testosterone ester serum accumulation, threshold control, and hormonal crash prevention.

**Equation authored by: Ashrafk.salim**

---

## What Is ASAM?

Most athletes designing testosterone cycles dose by guesswork — they know the compound, they know the half-life, but they have no idea what their actual serum concentration looks like week by week, whether they're approaching their threshold, or how long the compounds stay in their system after the last injection.

**ASAM solves this.** It takes your ester stack, your target serum ceiling (Θ), and your cycle length — and outputs a precise week-by-week serum map with a controlled ascent, a stable plateau that never breaches your threshold, and a mathematically modeled descent that prevents the cortisol rebound responsible for post-cycle crashes.

---

## The Equation

```
S_total(t) = Σ_i Σ_j≤N(t) [ D_i · f_i · 2^(-(t-t_j)/h_i) ]
```

**Variables:**

| Symbol | Name | Definition |
|--------|------|------------|
| S_i(t) | Ester Serum at time t | Active serum level of ester i at day t |
| D_i | Dose per injection | mg of ester i per injection |
| f_i | Conversion factor | Actual hormone yield (e.g. 0.72 for Enanthate) |
| h_i | Half-life | Ester i half-life in days |
| t_j | Injection timestamp | Day of the jth injection |
| N(t) | Injection count | Total injections administered up to day t |
| E | Ester count | Total number of esters in the stack |
| Θ | Threshold | Maximum allowable serum target |

**Threshold Constraint (Never Exceed Rule):**
```
S_total(t) ≤ Θ  for all t
```
If S_total(t) > Θ, the ASAM scale factor λ is applied:
```
λ = Θ / S_baseline
D_i' = D_i · λ
```

**Clearance Model:**
```
T_clear = T_end + h_max · log₂(S_total(T_end) / C_min)
```
Where h_max is the longest ester half-life and C_min = 1mg residual floor.

---

## Features

- **Multi-ester support** — stack any combination of testosterone esters
- **Automatic dose scaling** — ASAM scale factor ensures you never exceed your threshold Θ
- **Three-phase cycle design:**
  - Ascent phase — linear ramp-up preventing shock loading
  - Plateau phase — locked at threshold, maximum stable output
  - Taper phase — linear descent preventing hormonal crash
- **Week-by-week output table** showing pin days, dose per injection, retained serum from previous week, total serum, and % of threshold
- **Full clearance calculation** — exact days and PCT start recommendation
- **Per-ester pharmacokinetic breakdown** — half-life, conversion factor, scaled dose, weekly actual testosterone

---

## Supported Esters

| Ester | Half-Life | Conversion Factor |
|-------|-----------|-------------------|
| Testosterone Propionate | 3 days | 0.800 |
| Testosterone Enanthate | 8 days | 0.718 |
| Testosterone Cypionate | 10 days | 0.700 |
| Testosterone Hexahydrobenzylcarbonate | 14 days | 0.670 |
| Testosterone Decanoate | 15 days | 0.620 |
| Testosterone Undecanoate | 21 days | 0.610 |

---

## How to Use

1. Open `index.html` in any browser — no installation required
2. Add your testosterone esters and mg per injection
3. Set your cycle length, injection frequency, ascent weeks, and taper weeks
4. Set your threshold Θ (target actual testosterone per week in mg)
5. Click **RUN ASAM**
6. Read your week-by-week serum table and clearance timeline

---

## Deployment

This is a single-file HTML/JS application with no dependencies or backend.

**Netlify Drop (fastest):**
1. Go to netlify.com/drop
2. Drag `index.html` onto the page
3. Live in under 60 seconds

**GitHub Pages (permanent):**
1. Create repository at github.com
2. Upload `index.html`, rename to `index.html`
3. Settings → Pages → deploy from main branch
4. Live at `yourusername.github.io/repo-name`

---

## Pharmacokinetic Background

Testosterone esters release the active hormone at a rate determined by their ester chain length. Longer esters = slower release = longer half-life. When multiple esters are stacked, their serum contributions accumulate — meaning steady-state serum is significantly higher than a single injection would suggest.

The ASAM model accounts for:
- Ester molecular weight correction (actual testosterone content vs labeled mg)
- Cumulative serum accumulation across all injections
- Half-life decay for each ester independently
- Linear ascent ramp to avoid initial overload
- Linear taper to prevent abrupt cessation and cortisol rebound

---

## Author

**Equation and methodology: Ashrafk.salim**

Built as an academic pharmacokinetics modeling tool for studying ester half-life stacking and serum accumulation curves in testosterone replacement and performance pharmacology.

---

## Disclaimer

This tool is for academic and educational pharmacokinetics study only. All outputs are theoretical mathematical models. Consult a licensed medical professional for any clinical decisions.
