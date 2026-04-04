---
name: drug-drug
description: >
  Evidence-based Drug-Drug Interaction (DDI) assessment skill modeled after the Micromedex Drug-Reax
  methodology. Trigger this skill whenever the user types /drug-drug, mentions "drug interaction",
  "DDI", "drug-drug", "can I take X with Y", "interaction between", "交互作用", "併用",
  or asks whether two medications can be used together. This skill performs systematic literature
  retrieval via PubMed, CrossRef, and WebSearch, then produces a structured assessment report
  with Severity, Documentation, Onset, Mechanism, Clinical Effects, and Management —
  mirroring the Micromedex Drug-Reax classification framework. Even casual questions like
  "is it safe to combine A and B" should trigger this skill.
---

# Drug-Drug Interaction (DDI) Evidence-Based Assessment

## Overview

This skill replicates the Micromedex Drug-Reax System methodology through real-time literature
retrieval and structured evidence appraisal, producing a report with classification grades
comparable to established drug information compendia.

## Trigger

- `/drug-drug DrugA DrugB`
- Any query mentioning two drug names and asking about interaction, safety, or concomitant use
- Keywords: DDI, interaction, contraindication, concomitant, 交互作用, 併用

---

## Workflow (execute strictly in order)

### Step 0: Drug Name Resolution

Extract two drug names from user input. If the user provides brand names, resolve to
INN/generic names. If only one drug is provided or names are ambiguous, ask the user to clarify.

### Step 1: Literature Search

Execute **at least 5 distinct searches** to ensure adequate coverage:

1. **PubMed Search** (via web_search)
   - `site:pubmed.ncbi.nlm.nih.gov "DrugA" "DrugB" interaction`
   - `site:pubmed.ncbi.nlm.nih.gov "DrugA" "DrugB" pharmacokinetic`
   - `site:pubmed.ncbi.nlm.nih.gov "DrugA" "DrugB" CYP450`

2. **CrossRef Search** (via web_fetch)
   - `https://api.crossref.org/works?query=DrugA+DrugB+drug+interaction&rows=10&sort=relevance`

3. **General WebSearch**
   - `DrugA DrugB drug interaction clinical significance`
   - `DrugA DrugB interaction mechanism CYP enzyme`
   - `DrugA DrugB interaction case report adverse event`

4. **FDA Label / DailyMed**
   - `site:dailymed.nlm.nih.gov DrugA interaction`
   - `DrugA DrugB FDA drug interaction warning`

5. **PubMed MCP Tool** (if PubMed MCP server is connected)
   - Use `PubMed:search_articles` with `"DrugA" AND "DrugB" AND "drug interaction"`
   - Use `PubMed:get_article_metadata` for key articles

### Step 2: Evidence Appraisal

Read `references/evidence-grading.md` for complete grading criteria.

For each retrieved article, extract:
- Study design (RCT / cohort / case-control / case report / in vitro / review)
- Sample size
- Key findings (AUC fold-change, Cmax change, clinical events)
- Interaction mechanism described
- Credibility assessment

### Step 3: Structured Classification

Classify using the Micromedex Drug-Reax framework. See `references/evidence-grading.md` for
detailed decision trees.

#### 3a. Severity

| Grade | Definition |
|-------|-----------|
| **Contraindicated** | Drugs are contraindicated for concurrent use |
| **Major** | Interaction may be life-threatening and/or require medical intervention to minimize or prevent serious adverse effects |
| **Moderate** | Interaction may result in exacerbation of the patient's condition and/or require a change in therapy |
| **Minor** | Interaction would have limited clinical effects; may augment side effects but generally does not require a change in therapy |

#### 3b. Documentation

| Grade | Definition |
|-------|-----------|
| **Excellent** | Controlled studies have clearly established the existence of the interaction |
| **Good** | Documentation strongly suggests the interaction exists, but well-controlled studies are lacking |
| **Fair** | Available documentation is poor, but pharmacologic considerations lead clinicians to suspect the interaction exists; or documentation is good for a pharmacologically similar drug |
| **Poor** | Documentation is very limited, e.g., only isolated case reports or theoretical rationale |
| **Unlikely** | No reasonable pharmacologic basis for the interaction |

#### 3c. Onset

| Grade | Definition |
|-------|-----------|
| **Rapid** | Clinical effects of the interaction occur within 24 hours |
| **Delayed** | Clinical effects of the interaction occur after 24 hours |
| **Not specified** | Onset not clearly documented in the literature |

#### 3d. Mechanism

Classify the interaction mechanism into:

**Pharmacokinetic (PK):**
- CYP450 enzyme inhibition (specify isoform: CYP3A4, CYP2D6, CYP2C19, CYP2C9, CYP1A2, etc.)
- CYP450 enzyme induction
- P-glycoprotein (P-gp) / transporter-related
- Protein binding displacement
- Renal tubular secretion competition
- Absorption-level (pH alteration, chelation, etc.)

**Pharmacodynamic (PD):**
- Additive effect (e.g., QTc prolongation, bleeding risk, CNS depression)
- Synergistic effect
- Antagonistic effect

### Step 4: Report Generation

Produce the final report in the following format:

```markdown
# Drug-Drug Interaction Assessment Report

## Drug Pair

- **Drug A:** [Generic Name] ([Brand Names])
- **Drug B:** [Generic Name] ([Brand Names])

## Interaction Summary

[One-sentence summary of the core interaction]

## Structured Classification

| Parameter     | Grade          | Note              |
|---------------|----------------|-------------------|
| Severity      | [Grade]        | [note]            |
| Documentation | [Grade]        | [note]            |
| Onset         | [Grade]        | [note]            |
| Mechanism     | [PK/PD]        | [detail]          |

## Mechanism Details

[Detailed pharmacological mechanism including enzymes/transporters/receptors involved]

## Clinical Effects

[Description of potential clinical consequences, including PK data (AUC/Cmax changes) if available]

## Management Recommendations

[Specific clinical management recommendations:]

- Whether to avoid concomitant use
- Dose adjustments required
- Monitoring parameters
- Alternative drug suggestions

## Evidence Sources

[Key references: Author, Journal, Year, PMID/DOI]

## Disclaimer

> This report was generated by AI through literature retrieval and structured appraisal.
> It is for clinical reference only and cannot replace certified drug information systems
> such as Micromedex or Lexicomp. All clinical decisions should be made by qualified
> healthcare professionals with access to complete patient information.
```

---

## Key Principles

1. **Search first**: Always search before answering. Even if training data contains relevant information, verify through real-time search for the latest evidence.
2. **Multi-source cross-validation**: Use at least PubMed + CrossRef + WebSearch (three sources).
3. **Conservative grading**: When evidence is insufficient, err on the side of higher severity and lower documentation grade (err on the side of caution).
4. **Mechanism is king**: Even without clinical studies, if the pharmacologic mechanism is clear (e.g., known CYP inhibitor + known CYP substrate), document it and assign at least Fair documentation.
5. **Transparency**: The report must clearly indicate which information comes from high-quality studies vs. which is inferred or theoretical.
6. **Context matters**: Note dose-dependent or population-specific differences when evidence supports them (e.g., high-dose vs. low-dose regimens may carry different risk profiles).
7. **Language**: The report body defaults to English. If the user writes in another language, respond in that language but keep drug names, grade labels, and pharmacological terms in English.

## Reference Files

- `references/evidence-grading.md`: Complete evidence grading criteria, decision trees, CYP450 quick reference, and common PD interaction patterns
