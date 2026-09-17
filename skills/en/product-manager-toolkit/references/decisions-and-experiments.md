# Decisions, Metrics, and Experiments

Use for the `decisions` route. Access snapshot: 2026-09-17. Choose resources based on the decision and data, not as mandatory stages. See [access verification](access-verification.md) for what was actually tested.

## Intercom RICE — comparable priorities

- **Open:** [Sean McBride's original Intercom article](https://www.intercom.com/blog/rice-simple-prioritization-for-product-managers/).
- **Free scope:** readable methodology and worked examples. Recreate a small table locally; duplicating an online spreadsheet or subscribing to Intercom is unnecessary.
- **Professional use:** the author describes developing and using the approach within Intercom's product team.
- **Use:** compare candidates against the same outcome and time horizon with `reach × impact × confidence / effort`. Show evidence and units for each input. Confidence is a planning judgment, not a calibrated probability. Check dependencies, obligations, and hard constraints before sorting.
- **Return:** a ranked table with assumptions, sensitivity, and justified overrides. Do not invent reach or impact to make the formula complete; rank discovery work separately when value remains unknown.
- **Fallback:** an explicit impact/effort discussion with evidence gaps. A score does not establish customer demand.

## Google HEART — goals, signals, and metrics

- **Open:** [Original research and publication page](https://research.google/pubs/measuring-the-user-experience-on-a-large-scale-user-centered-metrics-for-web-applications/); [practical Google Cloud discussion](https://cloud.google.com/transform/unlocking-product-success-by-combining-dora-and-heart).
- **Free scope:** public explanation and research material. No Google Analytics account or analytics installation is needed to specify metrics.
- **Professional grounding:** Google's researchers describe using the framework with product teams; the Cloud article describes its application to product outcomes.
- **Use:** start with a product goal, identify observable user signals, and specify the few relevant metrics. For each metric define numerator, denominator, cohort, time window, source, and guardrail. Do not require every HEART dimension.
- **Return:** a measurement plan, not invented measurements. Without instrumentation, distinguish measurable now from planned collection.
- **Fallback:** a local goals/signals/metrics table. Do not mistake activity growth for customer benefit or business impact.

## Evan Miller — A/B sample size

- **Open:** [Sample size calculator](https://www.evanmiller.org/ab-testing/sample-size.html).
- **Free scope:** public calculator and result/share URL, without an account. The paid mobile app is separate. The form and its computed default rendered anonymously; custom-input execution was not completed in this review.
- **Professional grounding:** [Kuroha, an HR product manager, recommends the calculator for experiment planning](https://note.com/kento_kuroha/n/n7b30a26cfb77); [Bildung's practitioner walkthrough](https://bildungdata.com/en/insights/ab-tests-for-product-and-comms) applies it to product onboarding. These are practitioner accounts, not endorsements of every statistical statement in those articles.
- **Use:** enter a valid baseline rate, minimum detectable effect (MDE), power, and alpha. Specify whether MDE is relative or percentage points: 10% → 12% is +2 points or +20% relative. Read the result **per variation**. Record the assumed test design and allocation.
- **Return:** required sample and feasible duration using eligible traffic per arm and full business cycles. Do not force equal-allocation output onto unequal allocation or clustered B2B accounts. If traffic is insufficient, recommend a different test or accept a larger detectable effect explicitly.
- **Fallback:** a transparent local power calculation matching the design, or a calculation brief if no suitable statistical tool is available.

## Evan Miller — completed binary-outcome tests

- **Open:** [Chi-squared calculator](https://www.evanmiller.org/ab-testing/chi-squared.html); [author's warning about repeated peeking](https://www.evanmiller.org/how-not-to-run-an-ab-test.html).
- **Free scope:** public successes/trials calculator. An anonymous computed default was visible; custom-input execution was not completed in this review.
- **Professional use:** [Bildung's product-experiment walkthrough](https://bildungdata.com/en/insights/ab-tests-for-product-and-comms) explicitly uses this calculator after data collection.
- **Use:** provide successes and trials for two independent randomized groups at the predefined analysis point. Check counts, randomization unit, allocation imbalance, and expected cell sizes. Ordinary chi-squared approximations are unsuitable for sparse cells; use an appropriate exact method instead. Revenue, repeat events, clustered users, and multiple comparisons require a matching analysis.
- **Return:** observed rates, effect size, uncertainty, and business interpretation. A p-value is not the probability that the hypothesis is true. “Not significant” means inconclusive, not proof of equality or rejection of all useful effects.
- **Fallback:** local analysis with the appropriate statistical method, or a qualified-analysis brief. Never report a website result that was not obtained.

## PageSpeed Insights — web experience diagnostics

- **Open:** [Public analyzer](https://pagespeed.web.dev/); [official interpretation guide](https://developers.google.com/speed/docs/insights/v5/about).
- **Free scope:** analyze a public URL and read a report without an account. Account-dependent APIs and monitoring products are outside scope.
- **Professional use:** [QuintoAndar's published product-team case](https://web.dev/case-studies/quintoandar) includes PageSpeed reports as part of performance improvement work.
- **Use:** analyze the relevant public page for mobile and desktop. Separate observed field data from simulated lab diagnostics, and page data from origin aggregates. Record URL, device, date, and dataset period; small sites may have no field data.
- **Return:** performance risks and hypotheses for the task funnel. A score alone is not a UX audit, conversion forecast, or evidence of demand. Test business impact separately.
- **Fallback:** a local browser performance inspection if available, labeled with its environment; otherwise provide a manual check and leave measurements pending. Never submit private or token-bearing URLs.

## Match the tool to the stage

A pre-launch idea with no traffic usually needs interviews or a constrained pilot. A statistical calculator can establish that an A/B test is infeasible; it cannot create a sample. For existing onboarding, first define the metric with HEART, assess sample feasibility, then analyze only a valid completed experiment. Use RICE to compare supported investment options, not to decide whether invented benefits are real.
