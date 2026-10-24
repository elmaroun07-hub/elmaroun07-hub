# Houssain El Marouni

I find where software silently invents a number: an error turned into a zero, or a fallback that passes every test while the output still names a real source. Next, I want to find where AI models do the same.

Software testing · Tétouan, Morocco · [LinkedIn](https://www.linkedin.com/in/houssain-elmarouni)

## Merged upstream

**[career-ops](https://github.com/career-ops-hq/career-ops)** is an open-source job scanner with 70k+ stars.

- [#4504](https://github.com/career-ops-hq/career-ops/pull/4504) (merged): Gemini API errors used to end the Hacker News scan as "New offers: 0" with exit code 0. The scan now counts and prints the errors and exits 1 when every call fails. The PR includes a scan-level regression test.
- [#4416](https://github.com/career-ops-hq/career-ops/issues/4416) → [#4441](https://github.com/career-ops-hq/career-ops/pull/4441) (merged): I proposed that a portal is recorded as an empty board only if a request actually succeeded. Anything else is now recorded as unverified_zero. While reviewing #4441, I found that the audit's page cap never reached the providers, and the PR adopted my one-line fix.

**[career-ops-docs](https://github.com/career-ops-hq/career-ops-docs)**

- [#89](https://github.com/career-ops-hq/career-ops-docs/pull/89) (merged): the scan guide, in English, Spanish, French and German, now sends readers to the unverified-zero warning before they blame the title filter.

**[mastra](https://github.com/mastra-ai/mastra)** is a TypeScript AI agent framework.

- [#25237](https://github.com/mastra-ai/mastra/issues/25237): I reported, with a failing-test reproduction, that experiment trajectory scorers received an empty trajectory for workflow targets. It was fixed upstream in [#25269](https://github.com/mastra-ai/mastra/pull/25269).

## Own work

**[Voltura](https://voltura-web.onrender.com/cribado)** screens Spain's housing for summer heat risk. In Córdoba it scores 32,431 residential buildings from public records (the land registry, 81,972 energy certificates, the 2021 census and terrain data), each score with an uncertainty band and its sources. It also models solar and battery savings from NASA POWER irradiance. The production repo is private; [voltura-proof](https://github.com/elmaroun07-hub/voltura-proof) holds three of its test suites with the code they run, and they run with no database, network or keys.

The bug that shaped how I work: NASA keys were built as `2022JAN` while the real keys are `202201`, so every lookup missed. A `|| 4.0` fallback then gave Fuengirola and Tétouan the same 4,203 kWh, while the response still named NASA POWER as the source. The fix removed a 13.5% overstatement.

**[tokenguard](https://github.com/elmaroun07-hub/tokenguard)** audits LLM prompt spend with real BPE tokenizers. It is MIT-licensed and on npm as [@houssain/tokenguard](https://www.npmjs.com/package/@houssain/tokenguard).

## Open to

Software testing engagements · AI safety research fellowships · full-time roles
