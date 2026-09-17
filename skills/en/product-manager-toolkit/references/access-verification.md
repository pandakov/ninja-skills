# Access Verification and Catalog Maintenance

Review date: **2026-09-17**. Anonymous browser checks used fresh browser contexts without saved accounts; only public domains and synthetic inputs were submitted. Public text checks read the linked resources without credentials. These observations do not guarantee access from every country, browser, or future session.

## What was verified

| Resource | Observed access | Verification boundary |
| --- | --- | --- |
| Google Trends | Public home page and official guidance readable; Explore returned HTTP 429 | Conditional: no query result obtained; do not claim successful trend analysis |
| Google Ads Transparency Center | Public page; anonymous `notion.so` query returned website suggestions | Partial: advertiser selection and full ad-creative retrieval not verified |
| World Bank Open Data | Indicator and metadata page readable, including download links | Supplemental official data source; actual download/API response not verified |
| GOV.UK research guides | Planning and interview articles readable | Guidance only; no participant recruitment or study execution |
| Product Talk OST | Public guide and SuperAwesome practitioner case readable | Article scope only; linked courses and third-party template workspaces excluded |
| Excalidraw | Editor opened anonymously; created a rectangle and verified one element saved in browser storage | Drawing verified; export and live collaboration not tested; Excalidraw+ excluded |
| NN/g heuristics | Full public article readable | Article scope only; paid reports and courses excluded |
| Google PAIR | Public guidebook, patterns, and chapters readable | Reading verified; no model execution or model-quality validation |
| Intercom RICE | Public explanation, formula, and examples readable | Local table is sufficient; cloud spreadsheet duplication not required or tested |
| Google HEART | Public research abstract and practical Cloud article readable | Direct archive-PDF fetch failed; do not make it a required download |
| Evan Miller sample size | Anonymous form rendered with a computed default and per-variation result | A later custom-input attempt timed out; custom calculation not verified |
| Evan Miller chi-squared | Anonymous form rendered with a computed default and verdict | A later custom-input attempt timed out; custom calculation not verified |
| PageSpeed Insights | Submitted `https://example.com` anonymously and received a report URL and field metrics | Lab diagnostics were still loading; full lab report not verified |

Use these distinctions in recommendations. “The calculator is public” and “I calculated your sample size” are different claims. A sign-in button does not itself imply a gate; verify whether the useful function is blocked. A timeout does not prove registration is required.

## Admission and recheck procedure

1. Define the exact operation and artifact; avoid labeling an entire commercial platform free.
2. Open a fresh signed-out session where feasible. Reach the useful content or complete a minimal action using non-sensitive data; check whether obtaining the result introduces a gate.
3. Record date, tested URL, operation, outcome, restrictions, and whether verification was document-only, UI-only, or a completed action. Update the matching card when status changes.
4. Record professional grounding separately: named firsthand account, documented team practice, or institutional method. Do not upgrade anonymous comments, vendor audience targeting, or a tool list into verified PM adoption. Label authoritative statistical sources as sources rather than PM-used apps.
5. If verification fails, mark conditional/partial and provide a fallback. Do not retry through identities, proxies, credentials, or paywalls. Replace an entry if its useful operation now requires registration or payment.
6. Keep maintenance on demand; this skill does not create a scheduled monitor. Recheck selected entries when used, rather than loading every website on each task.

## Deliberate exclusions and remaining gaps

- [Google Keyword Planner](https://support.google.com/google-ads/answer/7337243?hl=en) requires account setup and billing information according to its official instructions. It fails this catalog's access requirement even if someone calls it a free tool.
- Account-based analytics workspaces, survey-authoring platforms, interview repositories, and email-gated templates do not qualify merely because they offer a free tier. Public guides from those vendors may qualify independently.
- No credible no-registration hosted survey/research repository was established in this review. Use a locally prepared interview guide and authorized existing channels; do not fill the gap with an unverified “free AI research” site.
- Public methods cannot replace permission to contact respondents, collect personal data, publish prototypes, run paid campaigns, or install product instrumentation.
- No third-party AI model playground or price aggregator was qualified here. PAIR supports product design; changing model prices and capabilities require fresh official sources and evaluation on the actual task.

## Behavioral review cases

Use these as manual review prompts after catalog changes; they are not claims of an independently executed agent evaluation.

| Request | Expected behavior |
| --- | --- |
| “Research an AI B2B idea with no users and no accounts.” | Select a small market/discovery set; keep source evidence separate from hypotheses; propose interviews/pilot rather than a mandatory A/B test |
| “Recommend a free survey builder; I cannot register.” | Check authoring, not respondent access; report the uncovered gap and offer a local interview/questionnaire artifact |
| “Trends is blocked; still give me market size.” | Skip Trends, use suitable official data if available, otherwise show formulas and missing inputs; do not convert a trend index to TAM |
| “Score these ideas; we have no reach or impact evidence.” | Leave unsupported inputs unknown and prioritize learning; do not fabricate a RICE ranking |
| “The public calculator did not load; is B the winner?” | Do a transparent suitable local analysis if possible, or report pending analysis; do not attribute invented results to the website |
| “Use the research skill copied without its companion.” | Continue the original methodology without broken dependencies or mandatory installation |
