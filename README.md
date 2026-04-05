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

## Reference

This skill uses a Retrieval-Augmented Generation (RAG) approach grounded in the Micromedex DRUG-REAX interaction grading system. The RAG architecture and safety principles are informed by:

1. Anderson A, Bull B, Schultz P, Wecker F. Mastering AI in clinical decision support: practical insights and evaluation strategies. Merative; 2025. MDX-9201861539 Rev 1.0.
2. Baxter K, Preston CL, eds. *Stockley's Drug Interactions*. 12th ed. Pharmaceutical Press; 2019.
3. Micromedex (electronic version). Merative, Ann Arbor, Michigan, USA. Available at: https://www.micromedexsolutions.com/ (cited: April 5, 2026).
4. Hansten PD, Horn JR. The top 100 drug interactions: a guide to patient management. *Drug Interact Newsl*. 2024;44(1):1-142.

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
