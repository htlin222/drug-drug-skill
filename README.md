# drug-drug

[![Build & Release Skill](https://github.com/htlin222/drug-drug-skill/actions/workflows/release.yml/badge.svg)](https://github.com/htlin222/drug-drug-skill/actions/workflows/release.yml)
[![GitHub Release](https://img.shields.io/github/v/release/htlin222/drug-drug-skill?include_prereleases&label=skill%20version)](https://github.com/htlin222/drug-drug-skill/releases/latest)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Skills Protocol](https://img.shields.io/badge/protocol-vercel--labs%2Fskills-blue)](https://github.com/vercel-labs/skills)
[![Compatible Agents](https://img.shields.io/badge/agents-40%2B-green)](https://github.com/vercel-labs/skills#supported-agents)

> Evidence-based Drug-Drug Interaction (DDI) assessment skill modeled after the Micromedex Drug-Reax methodology.

## Install

```bash
npx skills add htlin222/drug-drug-skill
npx skills add -g htlin222/drug-drug-skill        # global
npx skills add htlin222/drug-drug-skill --agent claude-code  # specific agent
```

## What it does

This skill performs systematic Drug-Drug Interaction assessments using real-time literature retrieval from PubMed, CrossRef, and web sources. It produces structured reports following the Micromedex Drug-Reax classification framework, including:

- **Severity grading**: Contraindicated / Major / Moderate / Minor
- **Documentation grading**: Excellent / Good / Fair / Poor / Unlikely
- **Onset classification**: Rapid / Delayed / Not specified
- **Mechanism analysis**: Pharmacokinetic (CYP450, P-gp, renal) and Pharmacodynamic (additive, synergistic, antagonistic)
- **Clinical management recommendations** with monitoring parameters and alternatives

Triggered by `/drug-drug DrugA DrugB` or natural language queries about drug interactions.

## Example

See [`example.md`](example.md) for a complete DDI assessment of **Methotrexate (MTX)** and **Trimethoprim/Sulfamethoxazole (TMP/SMX)**.

## Skill structure

```
drug-drug/
├── references
│   └── evidence-grading.md
└── SKILL.md
```

## Protocol

This skill follows the [vercel-labs/skills](https://github.com/vercel-labs/skills) protocol.
Each push to `main` triggers a GitHub Action that packages the skill as a `.skill` file
and creates a release tagged with the commit SHA.

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
