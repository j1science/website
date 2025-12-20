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

<style>
/* Make Flourish embeds feel substantial */
.flourish-embed {
  min-height: 800px;
  margin: 3rem 0;
}
</style>

I built two Big Ten visualizations that track lifetime cumulative trajectories for conference wins and NFL draft picks. These were created for the Rutgers IT Data Visualization Championship: Big Ten’s Love Data Week.

---

<div class="flourish-embed flourish-bar-chart-race"
     data-src="visualisation/26878999">
  <script src="https://public.flourish.studio/resources/embed.js"></script>
  <noscript>
    <img src="https://public.flourish.studio/visualisation/26878999/thumbnail"
         width="100%"
         alt="Big Ten cumulative conference wins, 2020–2025" />
  </noscript>
</div>

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

<div class="flourish-embed flourish-bar-chart-race"
     data-src="visualisation/26918430">
  <script src="https://public.flourish.studio/resources/embed.js"></script>
  <noscript>
    <img src="https://public.flourish.studio/visualisation/26918430/thumbnail"
         width="100%"
         alt="Big Ten cumulative conference wins, 1998–2025" />
  </noscript>
</div>

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

<div class="flourish-embed flourish-bar-chart-race"
     data-src="visualisation/26918306">
  <script src="https://public.flourish.studio/resources/embed.js"></script>
  <noscript>
    <img src="https://public.flourish.studio/visualisation/26918306/thumbnail"
         width="100%"
         alt="Big Ten cumulative conference wins, 2010–2025" />
  </noscript>
</div>

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

## Interesting questions

Together, these plots pair on-field outcomes with NFL talent production over time.  
That opens the door to questions such as:

1. Who consistently wins without producing many draft picks, and who produces draft picks without dominating conference play?

2. Do increases in draft production tend to precede improvements in conference performance, or follow them?

3. Era dependence -- How stable are program rankings across 1998–2025, 2010–2025, and 2020–2025?

4. Are gaps between programs widening or closing over time, and in which metric does that happen faster?


---

## What are you looking at

Both visualizations are cumulative by construction:

- Conference wins accumulate week-by-week across seasons.
- NFL draft picks accumulate year-by-year across draft classes.

Values only move upward when an event occurs; there are no resets and no negative contributions.

The three time windows simply expose the same cumulative processes at different temporal scales:
- 1998–2025: long-run program history  
- 2010–2025: modern era  
- 2020–2025: recent momentum  

---

## Notes

Draft picks use current Big Ten membership, counting each school’s drafted players back to 1998. Conference wins are built by carrying season-level cumulative wins forward so totals persist across years. All outputs are shaped into wide tables optimized for Flourish ingestion with consistent team naming and logos. The focus here is the visualization; the heavy lifting happens upstream in the data engineering in R using the API wrapper: cfbfastr.

---
