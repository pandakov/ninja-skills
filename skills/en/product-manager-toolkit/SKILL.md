---
name: product-manager-toolkit
description: >-
  Select and apply free, no-registration web tools and professional resources for
  product discovery, market research, competitor analysis, prioritization,
  prototyping, AI product design, metrics, and experiment planning. Use when a
  product task needs practical tools, source links, or a minimal working toolkit.
  Complements a product workflow; does not replace research or validate demand.
---

# Product Manager Toolkit

Turn a product question into a small, executable tool plan and a useful artifact. Respond in the user's language. This is a reusable selection and execution skill, not an autonomous agent, software integration, or a list to open on every task.

## Select only what the task needs

Identify the decision, workflow stage, geography, available evidence, required artifact, and available browser/calculation capabilities from existing context. Ask only for missing inputs that change tool selection. Prefer one primary resource and a fallback for the current question; combine resources when they answer different questions.

Read only the applicable reference:

| Route | When to use | Reference | Return to the product workflow |
| --- | --- | --- | --- |
| `market` | Search interest, market context, competitive messaging | [Market and competition](references/market-and-competition.md) | Dated evidence, reproducible filters, and limits on interpretation |
| `discovery` | Interview planning, opportunity mapping, workflow sketches, usability, AI suitability | [Discovery and design](references/discovery-and-design.md) | Interview guide, evidence-linked map, sketch, or evaluation checklist |
| `decisions` | Prioritization, success metrics, experiment sizing, conversion analysis, page performance | [Decisions and experiments](references/decisions-and-experiments.md) | Explicit assumptions, decision table, metric specification, or test plan |
| Access or maintenance | Eligibility is unclear, a page is gated, or the catalog is being updated | [Access verification](references/access-verification.md) | Exact access status and a usable fallback |

## Eligibility and evidence

- “Free without registration” applies to the named function, including obtaining its useful result. A free account, trial, email-gated download, API key, payment card, or sales call does not qualify.
- Public articles and methods qualify as resources. They are not interactive products. Paid courses, cloud storage, integrations, and workspaces advertised alongside them are outside the recommended scope.
- Cards identify professional grounding: a named practitioner's account, a documented product-team case, or an institutional method. Self-reported use is evidence of use, not audited employment or universal adoption. Official statistical sources are labeled separately; do not invent a PM endorsement for them.
- Access observations are dated snapshots, not guarantees. Distinguish a readable public page, an available form, and a successfully completed action. Check the exact function signed out before relying on it; a working home page is insufficient.
- If login, payment, CAPTCHA, regional restrictions, or rate limits block the function, use the stated fallback and record the gap. Do not silently switch to an account-based service or bypass restrictions. Conditional entries are optional, never required steps.

## Apply the resource

1. State the question and why this resource can help. A tool's popularity is not a reason to use it.
2. Prepare only necessary inputs: query terms, geography, time range, competitor domain, outcome, or aggregate measurements. Do not submit private interviews, customer data, internal URLs, or confidential strategy to external services without authorization. Anonymous access does not imply local processing.
3. Use the relevant public function through available tools. If interaction is unavailable, provide exact manual steps and mark execution pending. A generated sketch or local calculation must be labeled as such, not attributed to a website you did not operate.
4. Save the useful artifact and provenance: resource URL, access date, query/filters, input units, output, and limitations. Keep source facts, calculations, and hypotheses distinct. Cite original evidence rather than this catalog as evidence of market facts.
5. Explain how the result changes the decision and return it to the calling workflow. Stop when the artifact answers the question; do not tour the whole catalog.

The catalog supplies resources, not missing customer evidence. Search interest is not revenue; ads are not proof of profitable acquisition; a framework score is not demand validation; statistical significance is not commercial value.

## Handoff

Use a compact table when it helps:

| Question / stage | Resource and exact free function | Inputs / filters | Artifact and next decision | Access date / status | Limitation / fallback |
| --- | --- | --- | --- | --- | --- |

For an executed task, attach the artifact or results, not merely links. For a recommendation request, provide a short selection with links and usage steps. Translate the deliverable's headings and labels into the user's language.

## Integration and examples

A parent skill retains the methodology and final recommendation. It can invoke this skill for a specific route, passing the question, context, inputs, and desired artifact. Load only that route's reference. Return evidence and outputs without restarting the whole research process. Each skill remains usable independently; do not require installations or cross-skill calls when the companion is absent.

- **New AI B2B idea, no traffic:** `market` for terminology and public alternatives, `discovery` for interviews and AI suitability. Return a shortlist of hypotheses and a pilot plan; do not force an A/B test or infer paying buyers from search interest.
- **Existing onboarding with valid baseline data:** `decisions` for a primary metric and sample-size feasibility. Define the randomization unit, MDE, allocation, and horizon before interpreting results.
- **Several supported opportunities:** `discovery` for a map, then `decisions` for comparable priorities. Missing evidence reduces confidence; it must not be filled with invented reach or impact estimates.

When maintaining this skill, verify the specific free operation and practitioner/source evidence, update the dated access record, and preserve fallbacks. Add a script or API adapter only when a repeated operation justifies it and the public interface permits it; public web access alone does not establish an unrestricted API.
