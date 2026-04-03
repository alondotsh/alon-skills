# Alon Skills

[简体中文](./README.zh.md)

Public agent skills by Alon for Claude, Codex, Gemini, and OpenClaw.

## Install

Install any skill in this repository with:

```bash
npx skills add alondotsh/alon-skills --skill <skill-name>
```

Install all skills from this repository for the current/default agent:

```bash
npx skills add alondotsh/alon-skills --skill '*'
```

## Available Skills

### `alon-github-security-audit`

Audit a GitHub repository or local codebase for malicious code, backdoors, suspicious network behavior, credential theft patterns, obfuscation, and supply-chain risk.

Install:

```bash
npx skills add alondotsh/alon-skills --skill alon-github-security-audit
```

### `alon-search-skill-plus`

Search agent skills across trusted directories, ClawHub, and GitHub adaptation candidates with explicit ranking and safety filters.

Install:

```bash
npx skills add alondotsh/alon-skills --skill alon-search-skill-plus
```

## Compatibility

This repository is intended for agent hosts that support the open `SKILL.md` format, including:

- Claude
- Codex
- Gemini
- OpenClaw

## About Alon

These public skills come from Alon's real daily workflows.

Alon is actively exploring the future of agent skills and is open to connecting with people who want to build useful skills.

- GitHub: https://github.com/alondotsh
- ClawHub: https://clawhub.ai/u/alondotsh
- X: https://x.com/alondotsh
- WeChat Official Account: alondotsh
