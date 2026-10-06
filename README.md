Houssain El Marouni

I find where software silently invents a number: an error turned into a zero, or a fallback that passes every test while the output still names a real source. Next, I want to find where AI models do the same.

Software testing · Tétouan, Morocco · LinkedIn

Merged upstream

career-ops is an open-source job scanner with 70k+ stars.

#4504 (merged): Gemini API errors used to end the Hacker News scan as "New offers: 0" with exit code 0. The scan now counts and prints the errors and exits 1 when every call fails. The PR includes a scan-level regression test.
#4416 → #4441 (merged): I proposed that a portal is recorded as an empty board only if a request actually succeeded. Anything else is now recorded as unverified_zero. While reviewing #4441, I found that the audit's page cap never reached the providers, and the PR adopted my one-line fix.

career-ops-docs

#89 (merged): the scan guide, in English, Spanish and French, now sends readers to the unverified-zero warning before they blame the title filter.

mastra is a TypeScript AI agent framework.

#25237: I reported, with a failing-test reproduction, that experiment trajectory scorers received an empty trajectory for workflow targets. It was fixed upstream in #25269.
Own work

Voltura models solar and battery savings from NASA POWER irradiance and grid carbon-intensity data. It is live at voltura-web.onrender.com, and the code is private. The bug that shaped how I work: NASA keys were built as 2022JAN while the real keys are 202201, so every lookup missed. A || 4.0 fallback then gave Fuengirola and Tétouan the same 4,203 kWh, while the response still named NASA POWER as the source. The fix removed a 13.5% overstatement. Write-up

tokenguard audits LLM prompt spend with real BPE tokenizers. It is MIT-licensed and on npm as @houssain/tokenguard.

Open to

Software testing engagements · AI safety research fellowships · full-time roles
