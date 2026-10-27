# 06: Motion and Implementation Notes

The mockups were built as web SVG/CSS, so the numbers below are real, tested values. They port directly to SwiftUI or React Native.

## Recipe A: Construction reveal (primary; use for the daily card)

Order matters: **the instrument builds first, and the number arrives into a completed structure.** Structure precedes meaning, which enacts the brand's thesis on every open. Total ~3 seconds.

| Step | Element | Delay | Duration |
|---|---|---|---|
| 1 | Ring 1 (r=50) traces in | 100ms | 550ms |
| 2 | Ring 2 (r=86) | 350ms | 650ms |
| 3 | Ring 3 (r=118) | 650ms | 750ms |
| 4 | Inner diamond draws edge by edge | 950ms | 600ms |
| 5 | Outer diamond | 1250ms | 650ms |
| 6 | Ticks (and spokes at hero scale) fade in | 1550–1850ms | 300–500ms |
| 7 | Vertex dots settle, staggered ~100ms | ~1950ms | 380ms |
| 8 | Numeral fades up + slight scale/translate | ~2250ms | 480–600ms |
| 9 | Label, then reading, then challenge line, then footer | ~2450 / 2650 / 2800 / 2950ms | 480ms each |

Design rules:
- **Overlap the ring draws** (each starts before the previous finishes). Overlapped reads as ripples; strictly sequential reads as a loading screen.
- **Vertex dots get the only spring** in the sequence: `cubic-bezier(0.34, 1.56, 0.64, 1)`. Everything else eases out (`cubic-bezier(0.25, 0.1, 0.25, 1)`). One overshoot moment is the punctuation; if everything springs, nothing does.

**SwiftUI:** animate `.trim(from: 0, to: 1)` on each `Shape` path, dashes included natively; use `spring(response: 0.35, dampingFraction: 0.6)` for the dots; stagger with per-element `.delay()`. No physics engine or Lottie is needed for v1 (Lottie export is a reasonable later step if designers need to tune timing).

**Web mockup technique (for reference):** a solid white stroke on an SVG `<mask>` with `pathLength="100"`, `stroke-dasharray: 100`, animating `stroke-dashoffset` from 100 to 0, reveals the dashed path underneath. The mask shape must match the visible shape's `d`/`cx`/`cy`/`r` exactly.

## Recipe B: Celebration burst (secondary; mark motifs)

- Each mark scales 0→1 over ~420ms with the overshoot curve.
- Delay is proportional to the mark's position along the path parameter `t` (~1.1s end to end), plus up to ~120ms of **per-mark random jitter**. The jitter is load-bearing: without it the sweep reads as a mechanical cascade; with it, sparks catching one at a time.
- Deploy on: sighting log confirmation (shorter, denser burst), streak milestone. Not on the daily reveal.
- For the staggered grid, reveal row by row (~130–150ms per row, ~22–30ms per column, ~50ms jitter, ~340–360ms per mark).

## Mark placement algorithms

### Problem found: naive random scatter overlaps and looks digital

The fix is **stratified sampling plus collision rejection**: divide the path into N equal segments, draw one candidate per segment, and reject any candidate that doesn't clear every placed neighbor by the sum of both radii plus a gutter (4–5px). Jitter survives inside each cell; overlap doesn't.

```js
// Catmull-Rom centerline through hand-placed anchors
function cr(p0,p1,p2,p3,t){ const t2=t*t,t3=t2*t;
  return [0.5*((2*p1[0])+(-p0[0]+p2[0])*t+(2*p0[0]-5*p1[0]+4*p2[0]-p3[0])*t2+(-p0[0]+3*p1[0]-3*p2[0]+p3[0])*t3),
          0.5*((2*p1[1])+(-p0[1]+p2[1])*t+(2*p0[1]-5*p1[1]+4*p2[1]-p3[1])*t2+(-p0[1]+3*p1[1]-3*p2[1]+p3[1])*t3)]; }

// Placement loop (N marks, GUTTER px)
for (let i = 0; i < N; i++) {
  for (let tries = 0; tries < 50; tries++) {
    const t = (i + 0.15 + rnd()*0.7) / N;            // stratified: one candidate per segment
    const p = sample(t), n = normalAt(t);            // point + unit normal on the curve
    const w = 10 + 30*Math.sin(Math.PI*t);           // band breathes: narrow tails, wide middle
    const off = (rnd()*2 - 1) * w;
    const x = p[0] + n[0]*off, y = p[1] + n[1]*off;
    if (inExclusionZone(x, y)) continue;             // keep clear of numeral/prose
    const spine = 1 - Math.min(Math.abs(off)/w, 1);  // 1 at centerline, 0 at edge
    const size = (0.7 + 0.9*spine) * (0.85 + 0.35*rnd());
    const rad = markRadius(type, size);
    if (placed.every(q => Math.hypot(q.x-x, q.y-y) >= q.rad + rad + GUTTER)) { placed.push({x,y,t,size,type,rad}); break; }
  }
}
```

Use a **seeded** RNG (mulberry32). Same seed gives the same wave; changing the seed per user gives each user a subtly personal wave for free.

Mark shapes (unit paths, scaled per mark):
- Spark: `M0 -5 L1.1 -1.1 L5 0 L1.1 1.1 L0 5 L-1.1 1.1 L-5 0 L-1.1 -1.1 Z`
- Diamond: `M0 -4 L4 0 L0 4 L-4 0 Z`
- Cross: `M0 -4.5 V4.5 M-4.5 0 H4.5` (stroke ~1.1–1.2, non-scaling)
- Dot: circle, r ≈ 1.2 + size×0.7

Staggered grid: columns ~22px, rows ~20px, odd rows offset by half a column, ±1.5–2px jitter per cell, numeral zone punched out.

## Pitfalls hit during design (check these early in the real build)

1. **Two coordinate systems drift.** The ornament (SVG with explicit centers) and the text (flexbox auto-centering) were centered on different reference points, producing a visible ~30px offset. **Fix:** one shared coordinate system. Size the geometry layer to the container's actual content size and position the numeral by the same center point as the rings. In SwiftUI, derive both from a single `GeometryReader` center.
2. **Dashes vanish at hero scale on near-black.** Ornament tuned to "recede" at night disappeared entirely. **Fix:** lighten the hue (not just opacity) to the `hairline-hero` tones and keep stroke width ≥1.3px.
3. **Box-sizing math.** In the web mockups, `width: 300px` with a 6px border meant a 288px content box; the SVG viewBox must match the content box, not the outer size. Not relevant to native, but explains why those mockup numbers are 288 wide.
4. **Overlapping marks** read as digital scatter; clearance reads as hand-set typesetting (see algorithm above).

## Suggested technical approach (proposed, not decided)

- **Framework:** SwiftUI (iOS-first) gives native `trim` animations and StoreKit; React Native/Expo is the alternative if cross-platform from day one matters more. Unspecified by the builder.
- **Storage:** local-first (SwiftData / SQLite / MMKV). No backend, no user accounts in v1.
- **Payments:** RevenueCat SDK + StoreKit; configure a yearly product with a 3-day trial and an optional weekly anchor; enable restore purchases.
- **Content:** ship number entries as a bundled JSON file (see `03` schema); no CMS needed for v1.
- **Fonts:** bundle Fraunces (variable) and Inter; use the `opsz` axis (high for hero numerals, low for body).
- **Notifications:** local notifications (UNUserNotificationCenter), copy pulled from the number entry.
- **Theming:** semantic color tokens; follow system appearance first, sunset-based switching later.
