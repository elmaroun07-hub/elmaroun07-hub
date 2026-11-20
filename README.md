# Houssain El Marouni | Elmaroun Hub

**Builder · SaaS · Open source · AI safety research**

I build software that refuses to invent a number, and I research the AI agents that do.

I'm a solo technical founder in Tétouan, Morocco. Everything I work on traces back to one failure class: a missing input that silently becomes a plausible answer. I build products that make that failure visible, publish the tools as open source, and measure how often AI agents fall into it.

[LinkedIn](https://www.linkedin.com/in/houssain-elmarouni) · [Research repo](https://github.com/elmaroun07-hub/reported-or-invented) · [Apart Research project](https://apartresearch.com/sprints/projects/reported-or-invented-a-onesentence-instruction-stops-agents-inventing-data-after-silent-tool-failures-a-toolside-note-mostly-does-no-nt5i6ei5rh) · [Merged PRs](https://github.com/career-ops-hq/career-ops/pulls?q=is%3Apr+is%3Amerged+author%3Aelmaroun07-hub)

## What I do

| | |
| --- | --- |
| 🔬 **AI safety research** | I measure whether AI agents report a silent tool failure or pass bad data on as fact, across frameworks, with every run published. |
| 🏗️ **SaaS** | I build products where every number is traced to its source and a missing input is shown, never guessed. |
| 🌍 **Open source** | I publish my tools and fix the same class of bug in other people's projects, test first. |

## 🔬 AI safety research: Reported or Invented?

[**reported-or-invented**](https://github.com/elmaroun07-hub/reported-or-invented) tests what an AI agent does when a tool fails without saying so: an empty body, a truncated list or zeroed fields behind an HTTP 200. Failures are injected at the HTTP layer with mitmproxy against a deterministic mock API, and a rule-based judge labels each answer: honest, accepted (bad data passed on as fact) or invented (values the tool never returned).

**Four frameworks, one model** (gpt-oss-20b, temperature 0, 48 affected runs each):

| Framework | Passed bad data on as fact | Stated values the data never contained |
| --- | --- | --- |
| LangGraph | 25/48 (52%) | 4/48 (8%) |
| Google ADK | 27/48 (56%) | 6/48 (12%) |
| OpenAI Agents SDK | 32/48 (67%) | 11/48 (23%) |
| crewAI | 38/48 (79%) | 17/48 (35%) |

With real data, every framework answered 12 of 12 runs correctly with no false alarms. On crewAI, Gemini 3.5 Flash-Lite passed bad data on as fact in 44 of 48 runs (92%).

**Apart Research sprint (AI × Epistemics).** I tested two fixes across the same four frameworks. One sentence added to the agent's instructions took invented values from 38 to 0 and bad data passed on as fact from 122 to 83 of about 190 runs, replicating a known prompt-level fix. A note added to the tool's response when data is missing mostly did not help: still 26 invented and 110 passed on as fact. → [Project page](https://apartresearch.com/sprints/projects/reported-or-invented-a-onesentence-instruction-stops-agents-inventing-data-after-silent-tool-failures-a-toolside-note-mostly-does-no-nt5i6ei5rh)

**Next tier (runs published):** does the agent go on to act after a silent read failure, in refund, escalation and incident tasks? The 1,008 judged runs are in [`results/action-tier/`](https://github.com/elmaroun07-hub/reported-or-invented/tree/main/results/action-tier).

All raw and judged runs are committed; the repo has 180 tests; release [v0.2.0](https://github.com/elmaroun07-hub/reported-or-invented/releases). These are small, preliminary measurements, not a general ranking of frameworks.

## 🏗️ SaaS: Voltura

[**Voltura**](https://github.com/elmaroun07-hub/Voltura) is an energy-intelligence platform for summer heat poverty in Spain's oldest housing.

- Scored **32,431 residential buildings in Córdoba** for summer heat risk from public registers (Catastro, 81,972 energy certificates, INE Census 2021, IGN elevation), with an uncertainty band on every score and each score traced to its sources.
- Solar and battery estimates from NASA POWER, with carbon and tariff figures cited to REE, Eurostat and DESNZ. A country without official figures shows "pending", never an invented rate.
- The AI optimizer writes prose only. The numbers are computed in code, and a validator rejects any number that wasn't in the model's input.
- Code public (MIT). [**voltura-proof**](https://github.com/elmaroun07-hub/voltura-proof) runs the heat-risk index, building-code and NASA regression suites with no database, network or keys.

The hosted service is paused for now; the code, methodology and tests are all public.

## 🌍 Open source

**My tools**

- [**reported-or-invented**](https://github.com/elmaroun07-hub/reported-or-invented): silent tool-failure harness for AI agents (MIT)
- [**tokenguard**](https://github.com/elmaroun07-hub/tokenguard): LLM prompt-spend audit with real BPE tokenizers, on npm as [@houssain/tokenguard](https://www.npmjs.com/package/@houssain/tokenguard) (MIT)
- [**Voltura**](https://github.com/elmaroun07-hub/Voltura): full platform source (MIT)

**Merged into [career-ops](https://github.com/career-ops-hq/career-ops)** (member of career-ops-hq):

| PR | Fix |
| --- | --- |
| [#4504](https://github.com/career-ops-hq/career-ops/pull/4504) | Gemini API failures showed up as "New offers: 0" with a success exit; now reported, with non-zero exit and a scan-level test. |
| [#5817](https://github.com/career-ops-hq/career-ops/pull/5817) | The OpenRouter runner told models to use tools it never sent; the prompt now says so and drops the unavailable steps. |
| [#6169](https://github.com/career-ops-hq/career-ops/pull/6169) | A fixed 2-second wait read 0 of 20 Workday postings; the runner now tries job-board APIs first, then waits for the description. Released in v1.40.0. |
| [#6017](https://github.com/career-ops-hq/career-ops/pull/6017) | A 15-second model timeout dropped slow answers and blacklisted free models; raised to 120 s. |
| [#6018](https://github.com/career-ops-hq/career-ops/pull/6018) | A failed package-index download surfaced as a misleading "unable to locate package"; the CV test image now retries and fails on the real error. |
| [docs #89](https://github.com/career-ops-hq/career-ops-docs/pull/89) | Scan guide: check unverified-zero warnings before blaming the title filter (en/es/fr/de). |

**Elsewhere**

- **career-ops:** [issue #4416](https://github.com/career-ops-hq/career-ops/issues/4416) proposed telling an unverified zero from a real empty result, implemented in [#4441](https://github.com/career-ops-hq/career-ops/pull/4441); in review I found a page-cap bug and proposed the one-line fix, merged as written.
- **Google ADK:** [PR #8097](https://github.com/google/adk-python/pull/8097) (open) makes `RestApiTool` tell the model when a 2xx body is empty or not JSON.
- **Mastra:** [issue #25237](https://github.com/mastra-ai/mastra/issues/25237) reported an empty trajectory reaching workflow scorers, with a failing-test reproduction; fixed upstream in [#25269](https://github.com/mastra-ai/mastra/pull/25269).

## The bug that shaped my work

Voltura looked up NASA POWER data with keys like `2022JAN`, while the response used `202201`. Every lookup missed, and a `|| 4.0` fallback gave Fuengirola and Tétouan the same 4,203 kWh estimate while still naming NASA as the source, overstating savings by 13.5%.

Since then I work the same way everywhere: make missing evidence visible, trace every number to its input, and keep a regression test that fails if the original defect comes back.

I build with AI coding assistants (Claude Code, Codex) under my direction, and check every published number against its source.

## Open to

AI safety research fellowships · AI reliability and evaluation roles · Software testing and silent-failure audits for AI-agent teams · Full-time roles, remote or with relocation

Feedback on the judge's rules or an independent reproduction of Reported or Invented? is very welcome. [Connect on LinkedIn](https://www.linkedin.com/in/houssain-elmarouni).
