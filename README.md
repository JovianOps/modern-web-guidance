# Modern Web Guidance (for Gemini & Non-Local Agents)

This repository contains **modern_web_guidance_for_gemini.md**, an agent-compatible version of Google Chrome's Modern Web Guidance tailored for non-local AI agents (Gemini, Claude free, Custom GPTs, and web-based LLMs) that cannot execute or discover local `SKILL.md` files.

## Skill Details

- **Name:** `modern-web-guidance`
- **Description:** Search tool and guidance for modern web development best practices. Mandatory reference for HTML/CSS and client-side JavaScript tasks (dialogs/popovers, tables, dark mode, anchor positioning, container queries, view transitions, scroll-driven animations, forms, accessibility, CWV, sanitization, web components, passkeys).
- **Core File:** [`modern_web_guidance_for_gemini.md`](modern_web_guidance_for_gemini.md)

## How Non-Local Agents Use This

Non-local models (Gemini, Claude, Custom GPTs) do not have local filesystem skill loaders or terminal daemon environments that automatically discover `SKILL.md`. Instead, they only need what the skill does, its name, its description, and the full prompt instructions from [`modern_web_guidance_for_gemini.md`](modern_web_guidance_for_gemini.md).

1. **System Prompt / Custom Instructions / Project Knowledge:**
   Paste or attach [`modern_web_guidance_for_gemini.md`](modern_web_guidance_for_gemini.md) directly into your agent's system prompt, Gem instructions, or project files.
2. **Web Fallback (No Terminal Required):**
   If the agent cannot run terminal commands (`npx`), it browses and references the published guides directly at [https://developer.chrome.com/docs/modern-web-guidance/guides](https://developer.chrome.com/docs/modern-web-guidance/guides).
3. **CLI Execution (When Shell Available):**
   ```bash
   npx -y modern-web-guidance@latest search "<query>" --skill-version 2026_11_10-47b4c80e
   npx -y modern-web-guidance@latest retrieve "<guide-id>"
   ```

## License

Apache-2.0
