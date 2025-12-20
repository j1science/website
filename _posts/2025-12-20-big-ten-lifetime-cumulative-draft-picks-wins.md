---
title: "Big Ten NFL Draft Picks: Lifetime Cumulative Timelines"
date: 2025-12-20
categories: fun-things
tags:
  - data-viz
  - college-football
  - big-ten
  - nfl-draft
  - r
  - flourish
  - cfbfastr
  - cfbd-api
---

I built a pair of Big Ten visualizations that track **lifetime cumulative** counts over time—meaning the totals **never reset**. Values only move upward when an event happens (a draft pick or a conference win). No penalties, no negative steps, no “netting out” losses—just accumulation.

These were made for the Rutgers IT **Data Visualization Championship: Big Ten’s Love Data Week**:
https://it.rutgers.edu/data-viz-championship-big-tens-love-data-week/

---

## Embedded Plots

### 2020–2025

#### Lifetime cumulative conference wins (Big Ten)
<div class="flourish-embed flourish-bar-chart-race"
     data-src="visualisation/26878999">
  <script src="https://public.flourish.studio/resources/embed.js"></script>
  <noscript>
    <img src="https://public.flourish.studio/visualisation/26878999/thumbnail"
         width="100%"
         alt="Big Ten cumulative conference wins, 2020–2025" />
  </noscript>
</div>

#### Lifetime cumulative NFL draft picks (Big Ten)
<div class="flourish-embed flourish-chart"
     data-src="visualisation/26918692">
  <script src="https://public.flourish.studio/resources/embed.js"></script>
  <noscript>
    <img src="https://public.flourish.studio/visualisation/26918692/thumbnail"
         width="100%"
         alt="Big Ten cumulative NFL draft picks, 2020–2025" />
  </noscript>
</div>

---

### 1998–2025

#### Lifetime cumulative conference wins (Big Ten)
<div class="flourish-embed flourish-bar-chart-race"
     data-src="visualisation/26918430">
  <script src="https://public.flourish.studio/resources/embed.js"></script>
  <noscript>
    <img src="https://public.flourish.studio/visualisation/26918430/thumbnail"
         width="100%"
         alt="Big Ten cumulative conference wins, 1998–2025" />
  </noscript>
</div>

#### Lifetime cumulative NFL draft picks (Big Ten)
<div class="flourish-embed flourish-chart"
     data-src="visualisation/26918687">
  <script src="https://public.flourish.studio/resources/embed.js"></script>
  <noscript>
    <img src="https://public.flourish.studio/visualisation/26918687/thumbnail"
         width="100%"
         alt="Big Ten cumulative NFL draft picks, 1998–2025" />
  </noscript>
</div>

---

### 2010–2025

#### Lifetime cumulative conference wins (Big Ten)
<div class="flourish-embed flourish-bar-chart-race"
     data-src="visualisation/26918306">
  <script src="https://public.flourish.studio/resources/embed.js"></script>
  <noscript>
    <img src="https://public.flourish.studio/visualisation/26918306/thumbnail"
         width="100%"
         alt="Big Ten cumulative conference wins, 2010–2025" />
  </noscript>
</div>

#### Lifetime cumulative NFL draft picks (Big Ten)
<div class="flourish-embed flourish-chart"
     data-src="visualisation/26918546">
  <script src="https://public.flourish.studio/resources/embed.js"></script>
  <noscript>
    <img src="https://public.flourish.studio/visualisation/26918546/thumbnail"
         width="100%"
         alt="Big Ten cumulative NFL draft picks, 2010–2025" />
  </noscript>
</div>

---

## What these charts are doing

Both charts use the same idea: **a running total over time**.

- **Draft picks chart:** counts how many players from each school were selected in the NFL draft, accumulating year by year.
- **Conference wins chart:** counts Big Ten conference wins, accumulating week by week across seasons.

In both cases:
- totals **only increase** when the team gets a win / produces a draft pick,
- totals **do not reset** at season boundaries,
- and there is no concept of “losses” subtracting from anything.

That makes it easy to compare long-horizon dominance and momentum without constantly re-orienting to a new season baseline.

---

## Windowing: three views of the same idea

I exported and published the same cumulative logic for three time windows:

- **1998–2025** (long view: eras + program history)
- **2010–2025** (modern view)
- **2020–2025** (recent view: current trajectory and momentum)

The underlying data-generation pipeline is identical; only the displayed time range changes.

---

## How the draft-picks table is generated

For draft picks, the output table is **Flourish-wide**:

**Columns**
- `Team Name`
- `Image URL`
- `1967`, `1968`, …, `2025` (each year column is a lifetime cumulative total through that year)

**Definition**
- For a given team and year `Y`, the value in column `Y` is:
  - *(# of drafted players from that team in years start_year..Y)*

**Membership rule**
- I use **current Big Ten membership** (from `cfbd_team_info(conference="B1G")`) and count draft picks for those schools back to 1967.
  - This is intentionally “stable”: the team set is fixed to the present-day Big Ten, rather than changing historically by conference realignment.

**Reliability / API behavior**
- The pull is hardened against transient API hiccups (empty payloads, schema differences like `college_team` vs `college`, rate limiting).
- If a year fails after retries, it is treated as **0 picks for that year** rather than aborting the entire run.

---

## How the conference-wins table is generated

For conference wins, the output is also **Flourish-wide**, but the time axis is weekly and spans multiple seasons.

**Columns**
- Metadata: `Team Name`, `Region`, `Image URL`
- Weekly columns labeled like: `2020_Week 1`, `2020_Week 2`, …, `2025_Week N`

**Definition**
- Each season file already has cumulative wins within that season.
- The script applies a carry-over `C` so that:
  - `lifetime_value = season_cumulative + C`
- At the end of a season, the carry-over is updated using the **last non-missing** season value, then applied to the next season.

Again: **losses do nothing**—the series increases only when a win happens.

---

## Notes on the visuals

The charts are meant to be read as *trajectories*:

- **Slope** = rate of accumulation (draft picks per year, wins per week/season)
- **Separations** between lines show sustained differences over time
- **Recent acceleration** pops out clearly in the 2020–2025 window

I’m publishing the visuals here; the heavy lifting is in the data shaping so Flourish can ingest clean wide tables with consistent team naming + logos.

---
