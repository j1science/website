---
title: "Big Ten Draft Picks & Conference Wins: Cumulative Trends"
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
/* Full-width breakout for Flourish embeds */
.flourish-full {
  width: 100vw;
  max-width: 100vw;
  margin-left: calc(-50vw + 50%);
  margin-right: calc(-50vw + 50%);
  padding-left: 1rem;   /* optional breathing room */
  padding-right: 1rem;
}

/* Keep vertical spacing clean */
.flourish-full .flourish-embed {
  margin: 3rem 0;
}
</style>


I built two Big Ten visualizations that track lifetime cumulative trajectories for conference wins and NFL draft picks. These were created for the Rutgers IT Data Visualization Championship: Big Ten’s Love Data Week.

---

<div class="flourish-full">
  <div class="flourish-embed flourish-bar-chart-race"
       data-src="visualisation/26878999">
    <script src="https://public.flourish.studio/resources/embed.js"></script>
    <noscript>
      <img src="https://public.flourish.studio/visualisation/26878999/thumbnail"
           width="100%"
           alt="Big Ten cumulative conference wins, 2020–2025" />
    </noscript>
  </div>
</div>

<div class="flourish-full">
  <div class="flourish-embed flourish-chart"
       data-src="visualisation/26918692">
    <script src="https://public.flourish.studio/resources/embed.js"></script>
    <noscript>
      <img src="https://public.flourish.studio/visualisation/26918692/thumbnail"
           width="100%"
           alt="Big Ten cumulative NFL draft picks, 2020–2025" />
    </noscript>
  </div>
</div>

---

<div class="flourish-full">
  <div class="flourish-embed flourish-bar-chart-race"
       data-src="visualisation/26918430">
    <script src="https://public.flourish.studio/resources/embed.js"></script>
    <noscript>
      <img src="https://public.flourish.studio/visualisation/26918430/thumbnail"
           width="100%"
           alt="Big Ten cumulative conference wins, 1998–2025" />
    </noscript>
  </div>
</div>

<div class="flourish-full">
  <div class="flourish-embed flourish-chart"
       data-src="visualisation/26918687">
    <script src="https://public.flourish.studio/resources/embed.js"></script>
    <noscript>
      <img src="https://public.flourish.studio/visualisation/26918687/thumbnail"
           width="100%"
           alt="Big Ten cumulative NFL draft picks, 1998–2025" />
    </noscript>
  </div>
</div>

---

<div class="flourish-full">
  <div class="flourish-embed flourish-bar-chart-race"
       data-src="visualisation/26918306">
    <script src="https://public.flourish.studio/resources/embed.js"></script>
    <noscript>
      <img src="https://public.flourish.studio/visualisation/26918306/thumbnail"
           width="100%"
           alt="Big Ten cumulative conference wins, 2010–2025" />
    </noscript>
  </div>
</div>

<div class="flourish-full">
  <div class="flourish-embed flourish-chart"
       data-src="visualisation/26918546">
    <script src="https://public.flourish.studio/resources/embed.js"></script>
    <noscript>
      <img src="https://public.flourish.studio/visualisation/26918546/thumbnail"
           width="100%"
           alt="Big Ten cumulative NFL draft picks, 2010–2025" />
    </noscript>
  </div>
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

Both visualizations are cumulative by construction: conference wins accumulate week by week across seasons, while NFL draft picks accumulate year by year across draft classes. In both cases, values only move upward when an event occurs—there are no resets and no negative contributions. The three time windows simply present the same underlying cumulative processes at different temporal scales, with 1998–2025 capturing long-run program history, 2010–2025 reflecting the modern era, and 2020–2025 highlighting recent momentum.

---

## Notes

Draft picks use current Big Ten membership, counting each school’s drafted players back to 1998. Conference wins are built by carrying season-level cumulative wins forward so totals persist across years. All outputs are shaped into wide tables optimized for Flourish ingestion with consistent team naming and logos. Credit: Visualizations created with Flourish using data from CollegeFootballData.com (via the cfbfastR R package) for the Rutgers IT Data Visualization Championship.


---
