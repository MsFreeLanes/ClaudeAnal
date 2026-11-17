# Benchmark Palette Reference — Draft

**Companion:** V6.5 Benchmark Specification  
**Status:** Draft; pending owner freeze  
**Scope:** UI, track legend, semantic surfaces, and benchmark screenshots  
**Evidence source:** User-supplied text in this conversation  
**Canonical project spelling:** UNRESOLVED — source alternates between “Vega Core” and “Veda Core” (vedacore.dev).

This document preserves the source's distinction between **LOCKED** values and **PROPOSED** values. Proposed colors and mappings are not approved canonical tokens until the owner freezes them.

## 1. Locked UI tokens — V6.5 §5.3 as supplied

| Token | Hex | Role | Supplied contrast against bg |
|---|---|---|---|
| bg | #0f172a | Deep navy/charcoal background | — |
| text | #f8fafc | Off-white typography | 17.1:1 (source-reported) |
| purple | #a855f7 | Semantic accent / orchestrator | 4.5:1 (source-reported, borderline) |
| cyan | #06b6d4 | Semantic accent / info | 7.4:1 (source-reported) |
| green | #22c55e | Success / start flag | 7.8:1 (source-reported) |
| orange | #f59e0b | Warning / caution zones | 8.3:1 (source-reported) |
| red | #ef4444 | Race-over / danger / finish flag | 4.7:1 (source-reported) |

The supplied note says #f59e0b is technically Tailwind amber-500 rather than orange-500, but the **hex is canonical** and the token name is cosmetic. Do not change the hex merely to make the name match a color family.

The supplied proposal says purple and red at 500 may be too close to AA for small text; use proposed 400 shades for body text and keep 500 for borders, icons, fills, or large text. This rule is **PROPOSED**, not locked.

## 2. Track legend

| Legend color | Hex | Meaning | Status |
|---|---|---|---|
| Red | #ef4444 | Safety walls | LOCKED (shared UI hex) |
| Blue | #3b82f6 | Hard metal walls / elevation boundaries | PROPOSED — named in spec, hex missing |
| White | #ffffff | Directional arrows, dotted underpass lines | PROPOSED — named in spec, hex missing |
| Green | #22c55e | Start/Finish markers | LOCKED (shared UI hex) |
| Cyan | #06b6d4 | NPC paths | Hex LOCKED; role mapping PROPOSED |
| Yellow | #eab308 | Vendor locations | PROPOSED — named in spec, hex missing |
| Orange | #f59e0b | Bleacher zones | Hex LOCKED; role mapping PROPOSED |

The source says V6.5 groups “Cyan, Yellow, Orange” without a one-to-one role mapping. The mapping cyan=NPC paths, yellow=vendors, orange=bleachers is a proposal. Confirm it in the Track Legend attachment before freezing or treating any affected grader/test as objective.

## 3. Proposed neutral surface ramp

| Token | Hex | Role | Status |
|---|---|---|---|
| page | #020617 | Outer canvas behind panels | PROPOSED |
| bg | #0f172a | App background | LOCKED |
| surface | #1e293b | Bento card base fill | PROPOSED |
| border | #334155 | Card borders and dividers | PROPOSED |
| border-strong | #475569 | Hover/focus borders | PROPOSED |
| text-muted | #94a3b8 | Secondary labels, timestamps | PROPOSED |
| text-subtle | #cbd5e1 | Tertiary body text | PROPOSED |
| text | #f8fafc | Primary text | LOCKED |

## 4. Proposed semantic ramps

| Hue | 400 | 500 canonical | 600 | Status |
|---|---|---|---|---|
| Purple | #c084fc | #a855f7 | #9333ea | 400/600 proposed; 500 locked |
| Cyan | #22d3ee | #06b6d4 | #0891b2 | 400/600 proposed; 500 locked |
| Green | #4ade80 | #22c55e | #16a34a | 400/600 proposed; 500 locked |
| Orange | #fbbf24 | #f59e0b | #d97706 | 400/600 proposed; 500 locked |
| Red | #f87171 | #ef4444 | #dc2626 | 400/600 proposed; 500 locked |
| Blue | #60a5fa | #3b82f6 | #2563eb | Proposed |
| Yellow | #facc15 | #eab308 | #ca8a04 | Proposed |

## 5. Proposed Bento card recipe

- Base card: fill #1e293b, border 1px #334155, radius 12–16px.
- Semantic card: border 1.5–2px in hue 500; fill tinted hue at 12% over #0f172a.

| Hue | Proposed tinted fill |
|---|---|
| Purple | #211e43 |
| Cyan | #0e2a3e |
| Green | #112c30 |
| Orange | #2b2726 |
| Red | #2a1c2d |
| Blue | #142442 |
| Yellow | #292a26 |

These tinted fills are transcribed from the supplied draft. Recompute and visually test them before using as canonical tokens.

## 6. Dual-use reservations

- Red is intentionally shared by safety walls, finish flag, and race-over UI.
- Green is shared by start flag, start/finish markers, and success states.
- White #ffffff is track-marking-only; UI text remains #f8fafc.
- Flagman, weather flashes, and night lighting should use existing palette values; no new hues unless owner-approved.

## 7. CSS token block

~~~css
:root {
  /* LOCKED */
  --vc-bg: #0f172a;
  --vc-text: #f8fafc;
  --vc-purple: #a855f7;
  --vc-cyan: #06b6d4;
  --vc-green: #22c55e;
  --vc-orange: #f59e0b;
  --vc-red: #ef4444;

  /* PROPOSED — track */
  --vc-blue: #3b82f6;
  --vc-yellow: #eab308;
  --vc-white: #ffffff;

  /* PROPOSED — surfaces */
  --vc-page: #020617;
  --vc-surface: #1e293b;
  --vc-border: #334155;
  --vc-border-strong: #475569;
  --vc-text-muted: #94a3b8;
  --vc-text-subtle: #cbd5e1;
}
~~~

## 8. Freeze checklist

- [ ] Approve proposed Blue, White, Yellow hexes.
- [ ] Approve surface ramp and semantic 400/600 ramps.
- [ ] Confirm cyan/yellow/orange role mapping.
- [ ] Ratify small-text policy for purple and red.
- [ ] Confirm canonical project name: Vega Core or Veda Core.
- [ ] Recalculate WCAG contrast and test actual text/background combinations.
- [ ] Update the Track Legend attachment and benchmark test fixtures together.
- [ ] Ensure screenshots, grader rules, and CSS tokens all use the same frozen palette.

**Important:** This is a companion draft based on pasted source text. It does not replace V6.5 or resolve any owner approval items.
