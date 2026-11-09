# Houssain El Marouni | Elmaroun Hub

**AI reliability · Software testing · Reproducible evaluation**

I'm an independent developer in Tétouan, Morocco. I investigate silent failures: API errors reported as zero results, missing inputs replaced by plausible numbers, and AI answers that go beyond the evidence a tool returned.

I build reproductions, regression tests and fixes that make those failures visible.

[LinkedIn](https://www.linkedin.com/in/houssain-elmarouni) · [Voltura live](https://voltura-web.onrender.com/cribado) · [Merged Career-ops PRs](https://github.com/career-ops-hq/career-ops/pulls?q=is%3Apr+is%3Amerged+author%3Aelmaroun07-hub)

## Featured work

| Project | What it does | Evidence and status |
| --- | --- | --- |
| [Reported or Invented?](https://github.com/elmaroun07-hub/reported-or-invented) | Tests whether AI agents report silent tool failures, accept corrupted data, or invent unsupported values. | HTTP failure injection, a deterministic mock API, a crewAI runner and a rule-based judge. Early prototype; the full experiment has not run yet. |
| [Voltura](https://github.com/elmaroun07-hub/Voltura) | Screens housing for summer heat risk and estimates solar and battery savings with explicit data provenance. | Live application; Córdoba screening covers 32,431 residential buildings. Public code, tests, methodology and recorded verification evidence. |
| [voltura-proof](https://github.com/elmaroun07-hub/voltura-proof) | A standalone copy of selected Voltura code and tests for inspection and reproduction. | Three suites covering the heat-risk index, Spanish building-code calculations and NASA POWER regressions. Runs without an external service, database or API keys. |

### Current evaluation work

Reported or Invented? separates **accepting corrupted tool data** from **inventing values the tool never returned**. It includes genuine empty-data and explicit-error controls.

The repository contains 23 judge tests, including nine recorded model responses. These are initial examples, not a completed benchmark. Next steps are validating the judge, running repeated experiments and publishing reproducible results.

## Merged upstream contributions

Five authored fixes merged into [Career-ops](https://github.com/career-ops-hq/career-ops):

| PR | Problem addressed |
| --- | --- |
| [#4504](https://github.com/career-ops-hq/career-ops/pull/4504) | Gemini API failures appeared as “New offers: 0” with a successful exit. The scanner now reports failures and exits non-zero when every call fails, with a scan-level regression test. |
| [#5817](https://github.com/career-ops-hq/career-ops/pull/5817) | The OpenRouter runner instructed models to use tools it did not provide. Its prompt now states the limitation and removes unavailable steps, with regression coverage. |
| [#6169](https://github.com/career-ops-hq/career-ops/pull/6169) | A fixed two-second wait missed delayed job descriptions. The runner now tries supported job-board APIs first, then waits for page content. |
| [#6017](https://github.com/career-ops-hq/career-ops/pull/6017) | Slow model responses exceeded a 15-second deadline. The timeout was raised to 120 seconds. |
| [#6018](https://github.com/career-ops-hq/career-ops/pull/6018) | A failed package-index download caused a misleading missing-package error. The CV test image now retries and fails on the underlying fetch error. |

Other contributions:

- **Career-ops:** [issue #4416](https://github.com/career-ops-hq/career-ops/issues/4416) proposed distinguishing unverified zero results from successful empty responses; implemented upstream in [PR #4441](https://github.com/career-ops-hq/career-ops/pull/4441). During review, I also identified a page-cap forwarding bug and contributed the one-line fix.
- **Career-ops documentation:** [PR #89](https://github.com/career-ops-hq/career-ops-docs/pull/89), merged, directs readers to check unverified-zero warnings before changing job-title filters.
- **Mastra:** [issue #25237](https://github.com/mastra-ai/mastra/issues/25237) reported an empty trajectory reaching workflow experiment scorers, with a failing-test reproduction. The upstream fix merged in [PR #25269](https://github.com/mastra-ai/mastra/pull/25269).

## The bug that shaped my work

Voltura looked up NASA POWER data with keys such as `2022JAN`, while the response used `202201`. Every lookup missed. A `|| 4.0` fallback then gave Fuengirola and Tétouan the same 4,203 kWh annual estimate while still naming NASA as the source.

That failure shaped my approach: make missing evidence visible, trace numbers to their inputs, and keep a regression test that catches the original defect.

## More work

[tokenguard](https://github.com/elmaroun07-hub/tokenguard) audits LLM prompt spend with real BPE tokenizers. MIT-licensed; available on npm as [@houssain/tokenguard](https://www.npmjs.com/package/@houssain/tokenguard).

## Open to

Software testing engagements · AI reliability and evaluation collaborations · AI safety research fellowships · Full-time roles

For Reported or Invented?, feedback on the judge's classification rules and independent reproductions would be especially useful. [Connect on LinkedIn](https://www.linkedin.com/in/houssain-elmarouni).
