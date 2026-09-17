# AI Suitability, Economics, and Experiments

Apply AI sections to AI solutions; business models, channels, and hypothesis testing apply to any product. Do not turn research into detailed technical architecture design.

## Is AI justified?

Define the model's specific operation, autonomy boundaries, and measurable useful outcome. Compare it with the current workflow and simpler approaches: rules, search, templates, conventional automation, and specialist assistance. A service with partly manual fulfillment may be the best MVP.

Check:

- What input data is actually available, its completeness, and permitted use for the scenario. Assess training, retrieval, and inference-time processing separately.
- Whether correctness criteria, real examples, and a qualified evaluator exist.
- Costs of different error types, error detectability, acceptable latency, and human review needs.
- Privacy, retention, localization, security, and integration requirements that affect purchasing. Verify legal claims against current primary sources; do not imply legal expertise.
- Supplier dependencies: prices, limits, regional availability, quality and terms changes, and replaceability.
- External instructions in input data, leakage, erroneous actions, and quality drift to the extent they affect product viability.

A convincing demo does not establish reliable quality. Propose evaluation on typical, rare, and costly failure cases from the actual workflow, separate from tuning examples. State evaluation method, sample, and limitations; do not choose thresholds to fit observed results. Compare AI and the baseline on identical inputs and conditions.

Use task-relevant metrics: correctly completed operations, severe errors, rework, user time, human escalation rate, latency, and cost per successful outcome. Average “accuracy” can hide unacceptable failures in critical segments. Set thresholds from error costs and process requirements. For the MVP, specify behavior under uncertainty: clarification, refusal, human review, or a restricted use case.

## Value, pricing, and costs

Separate customer value from product revenue. Time savings become cash savings through a specific mechanism, such as reduced paid hours. Avoid double-counting overlapping benefits. Revenue uplift and risk reduction hypotheses need separate validation.

Choose a charging unit buyers understand and that aligns with their benefit: seat, organization, operation, volume, or outcome. For outcome pricing, define attribution and dispute handling. Compare price with existing spending, alternatives, and real willingness-to-pay evidence. Competitor pricing is a reference, not proof of acceptable pricing for the new product.

Calculate variable costs for the same period and volume:

```text
Model cost = sum across all calls (
    input tokens / billing unit × input price
  + output tokens / billing unit × output price
  + separately billed modalities or operations
)
Variable cost = model + retrieval/storage/infrastructure
  + third-party APIs + human review + variable support
  + other direct variable costs
Cost per successful operation = costs of all attempts / accepted successful operations
Contribution = net revenue − all included variable costs
Contribution margin = contribution / net revenue
```

Define net revenue and cost categories, including treatment of discounts, refunds, taxes, and fees; keep definitions consistent across scenarios. Contribution is not net profit: fixed costs remain separate. If calculating gross margin, define cost of revenue and distinguish it from other variable costs.

Include retries, failed attempts, long contexts, result checking, heavy users, and onboarding. Separate onboarding from recurring delivery costs. Apply caching benefits and discounts only when justified. Verify supplier prices, currencies, billing units, and dates against sources. Do not exclude failed attempts from the numerator of cost per success.

Show sensitivity to price, usage, human review rate, and quality. With zero successes, cost per success is undefined; with zero revenue, margin percentage is undefined. Negative contribution means growth worsens the economics.

When evidence permits:

- `CAC = attributable acquisition spending / new paying customers`, using a comparable cohort and accounting for sales delay. Without data, label it a scenario assumption, not a market fact.
- `CAC payback = CAC / monthly contribution per customer` assumes roughly stable positive contribution. For changing usage, accumulate contribution by month; nonpositive contribution does not repay CAC in this model.
- Estimate LTV from retention and contribution cohorts. Without observations, do not present a constant-churn formula as a reliable forecast; show ranges and assumption dependence.
- `Fixed-cost break-even volume = fixed costs / positive contribution per unit` assumes consistent periods and a linear model. State capacity constraints.

## Go-to-market

For the initial segment, propose a testable sequence: where to find buyers → conversation trigger → promise to test → pilot → purchase decision owner → reason for continued use.

Choose channels by audience reachability, contact cost, trust, and sales cycle. Avoid generic lists such as “SEO, social, partners” without connecting them to buyers. For B2B, include integrations, procurement, and security; for B2C, activation, task recurrence, acquisition, and retention. Treat untested channels as hypotheses. Account for attention competition and dependence on a single platform.

## Experiments and MVP boundaries

Prioritize assumptions by uncertainty, decision impact, and test cost. Start with potential project blockers: problem importance, data access, buyer, quality, and economics. Do not impose a universal sequence when the dominant risk is known.

Specify each experiment:

| Hypothesis | What would disprove it | Method and target sample | Metric and predefined threshold | Timeline, budget, owner/role | Actions for success, failure, and ambiguity |
| --- | --- | --- | --- | --- | --- |

Derive thresholds from business requirements, the baseline, and acceptable risk. Without a basis, mark them as proposed for agreement. Treat small or biased samples as directional signals; for quantitative conclusions, state uncertainty and sample adequacy. Avoid unsupported claims of statistical significance.

Match methods to risks:

- Problem: interviews about recent behavior and observation of the current workflow.
- Buyer access and positioning: authorized channel and offer tests; clicks indicate response, not payment or retention.
- Willingness to pay: specific commercial terms, a paid pilot, or a purchase. A letter of intent is weaker than payment; disclose commitment conditions.
- Quality: held-out real cases, expert evaluation, and severe-error analysis.
- Value and economics: a limited pilot recording manual effort, costs of all attempts, and customer outcomes.
- Repeatability: usage and payment over multiple natural task cycles; one successful session is insufficient.

Define the minimal MVP scenario, user, inputs and outputs, acceptance criteria, human role, data needs, and manual components. Defer features that do not test critical hypotheses. Tie a build recommendation to a specific test, budget, and stopping condition. Listing an external experiment in the plan does not authorize executing it.
