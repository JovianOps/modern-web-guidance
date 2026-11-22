# Modern Web Guidance for Non-Local Agents

A portable adaptation of Google's Chrome team's Modern Web Guidance skill for agents that cannot install local skills or run shell commands, including Gemini Gems, Claude, Custom GPTs, and browser-based LLMs.

The skill helps an agent consult current, focused web platform guidance before implementing web UI or client-side JavaScript. It covers modern HTML, CSS, browser APIs, accessibility, performance, security, and compatibility fallbacks. The supplied `SKILL.md` contains the complete workflow and agent-specific details.

Modern Web Guidance is maintained by Google Chrome and the web community. This repository adapts the agent instructions for non-local environments; it is an independent community adaptation and is not an official Google or Chrome product.

## Use with a non-local agent

Add the contents of [`SKILL.md`](SKILL.md) to the agent's persistent instructions, project instructions, or knowledge files. Then ask the agent to consult the relevant guidance before it proposes or changes web UI or client-side code.

- **Gemini Gems:** include `SKILL.md` in the Gem's instructions or uploaded knowledge, depending on the controls available in the current Gemini interface.
- **Claude:** add it to the project's `CLAUDE.md` or the project knowledge/instructions available in your Claude environment.
- **Custom GPTs and other hosted agents:** add it to the custom instructions or knowledge files, and ensure the agent can use a browser or another web search tool.
- **Browser-based LLMs without shell access:** follow the web fallback in `SKILL.md`: find the matching guide at [Chrome's published Modern Web Guidance guides](https://developer.chrome.com/docs/modern-web-guidance/guides), then read the guide before coding.

Interface names and upload options may differ across hosted products. The essential requirement is that the agent receives the skill instructions and can access the current guides through either the CLI or a browser.

## CLI workflow

For agents or environments with a terminal, search first using one focused 2â€“5 word query for each platform capability or UI pattern. Keep framework and product names out of the query. Search results provide guide IDs and descriptions; retrieve the relevant IDs before implementation.

```bash
npx -y modern-web-guidance@latest search "responsive data table" --skill-version 2026_11_10-47b4c80e
npx -y modern-web-guidance@latest retrieve "<guide-id>"
```

For multiple relevant guides, pass their IDs as a comma-separated list to `retrieve`. If search results are empty or weak, rephrase once with a concrete HTML, CSS, or UI primitive; if no relevant guide exists, proceed without retrieving unrelated material. The full query, retrieval, framework adaptation, verification, and disclosure rules are in [`SKILL.md`](SKILL.md).

On Windows, use `npx.cmd` when required by the shell. If `pnpm` is available, the skill allows `pnpx modern-web-guidance@latest ...`. CLI use needs network access. Environments with network approval should authorize the specific Modern Web Guidance command before the first invocation. Set `DISABLE_TELEMETRY=1` to opt out of anonymous CLI usage telemetry.

## Browser support and fallbacks

Guides treat **Baseline Widely Available** features as usable without a fallback by default. For features that are not Baseline Widely Available, follow the guide's fallback recommendations unless the project has an explicit browser support policy. Use the guide's compatibility data against any stated support target; do not add a fallback the project policy rules out. The skill also explains graceful framework adaptation, SSR and bundler considerations, and when to preserve modern platform APIs.

## Upstream project and license

- Upstream project: [GoogleChrome/modern-web-guidance](https://github.com/GoogleChrome/modern-web-guidance)
- Published guides: [developer.chrome.com/docs/modern-web-guidance/guides](https://developer.chrome.com/docs/modern-web-guidance/guides)
- Upstream source repository identifies software code as Apache-2.0 licensed; this adaptation uses Apache-2.0 as well. See [`LICENSE`](LICENSE).

## Contributing

Keep the skill's CLI examples, browser fallback, and compatibility guidance aligned with the upstream project. State clearly when a workflow or product-specific detail is an adaptation, and avoid inventing guide IDs or compatibility claims.
