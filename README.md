# Beta Graduation Day

**Which new Beta data connectors earn GA this quarter? A Bayesian Beta-Binomial decision room.**

- **Live demo:** https://shriyashekatkar25-byte.github.io/beta-graduation-day/
- **Gallery:** [APM Lab](https://shriyashekatkar25-byte.github.io/apm-lab/)
- Built by Shriya Shekatkar · UCLA · Stats 102C Monte Carlo Methods

## The launch that inspired it

On **October 20, 2026**, Databricks added three managed connectors to Lakeflow Connect in **Beta**: SurveyMonkey, Oracle Eloqua and Asana. Workspace admins control access from the Previews page, and all three use OAuth U2M authentication.

- Release notes, October 2026: https://docs.databricks.com/aws/en/release-notes/product/2026/october
- SurveyMonkey connector docs: https://docs.databricks.com/aws/fr/ingestion/lakeflow-connect/surveymonkey
- Oracle Eloqua connector docs: https://docs.databricks.com/aws/fr/ingestion/lakeflow-connect/oracle-eloqua
- Asana connector docs: https://docs.databricks.com/aws/fr/ingestion/lakeflow-connect/asana
- Release stage definitions (Beta vs GA): https://docs.databricks.com/aws/fr/release-notes/release-types

## The PM decision

As the PM for ingestion connectors: **which Beta connectors graduate to GA at the end of the quarter?** I set a single, written rule: graduate a connector when the posterior probability that its pipeline-update success rate clears the GA bar (default 99.0%) is at least the required confidence (default 90%), **and** all four guardrails pass (tickets per 100 pipelines ≤ 1.5, P95 freshness ≤ 30 min, OAuth refresh failures ≤ 0.3%, schema-drift breakages ≤ 2 per 1k updates).

The prototype simulates Beta-period outcomes for the three connectors (all synthetic), lets you change the weeks of data, the strength of a prior learned from past launches, the GA bar and the confidence level, and rewrites a director memo with a decision, evidence, risks, rollout plan, next step and a one-sentence VP summary.

## What it shows about product judgment

| Databricks APM skill | Where it shows up |
|---|---|
| Customer problem framing | Why a Beta label keeps survey, campaign and project data out of production dashboards |
| Prototyping | A working, seeded Monte Carlo decision room in one HTML file |
| SQL / Python | Illustrative SQL for Beta outcome counts and a NumPy Beta-Binomial gate |
| Data-driven decisions | Posterior probability vs. a GA bar, credible intervals, expected shortfall, guardrails |
| Clear writing | A memo that rewrites itself, ending in one sentence a VP can repeat |

## Methods

| Method (Stats 102C) | Used for |
|---|---|
| Ch2 Beta prior + Binomial likelihood → Beta posterior (conjugacy) | Each connector's success-rate belief after Beta |
| Ch2 Posterior mean as weighted average of prior and data | "Prior strength" slider: how much past launches count |
| Ch2 Flat prior → MAP = MLE | Setting prior strength to 0 |
| Ch2 Quantile credible intervals (vs HPD) | 90% interval on each KPI badge |
| Ch1 Monte Carlo estimates from sample means | P(rate ≥ bar) and expected shortfall from 6,000 seeded draws |
| Ch5 Box-Muller normals | Inside the Gamma sampler used to draw Beta variables |

## Design baseline

Four pins from Shriya's Pinterest home feed, redrawn from scratch in SVG/CSS/canvas. No pin images are used.

| Page part | Pin | What I took |
|---|---|---|
| Hero | [#love#kindness#affirmation# (Crafartill)](https://www.pinterest.com/pin/1000643610980277688/) | Lavender-to-pink holographic gradient, teal/violet aurora ribbon, white four-point sparkles, chunky rounded olive-green type with a dark outline, affirmation voice |
| Cards and buttons | [stampies (collage by Chavez Buckley)](https://www.pinterest.com/pin/465770786484047306/) | Black block-print stamp motifs on cream and blush paper, ink borders, halftone dot texture, masonry board layout |
| KPI badges | [anything can be an altar (Danielle Janaye)](https://www.pinterest.com/pin/264093965645664676/) | Quiet white field, centered classic serif, blush blossom-cluster crowns on brown branches |
| Simulation room | [i love you; and i love myself too (pixiedust)](https://www.pinterest.com/pin/934708097649283764/) | Cream panel with grain, hand-lettered caps headings, pinks/reds with soil-brown ground and sprouts that grow; the "together and independently" idea became partial pooling |

---

Unofficial concept prototype by Shriya Shekatkar. All data is simulated. Not affiliated with any company.
