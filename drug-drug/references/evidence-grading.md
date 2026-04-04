# Evidence Grading Reference for Drug-Drug Interaction Assessment

## Table of Contents
1. [Severity Rating Decision Tree](#severity)
2. [Documentation Rating Decision Tree](#documentation)
3. [Onset Classification](#onset)
4. [Mechanism Classification Taxonomy](#mechanism)
5. [Literature Appraisal Checklist](#appraisal)
6. [Search Strategy Templates](#search)
7. [CYP450 Quick Reference](#cyp450)
8. [Common PD Interaction Patterns](#pd-patterns)

---

## 1. Severity Rating Decision Tree {#severity}

Follow this decision tree in order:

```
Q1: Does the prescribing information for either drug explicitly state
    "Contraindicated" for concurrent use?
  ├─ YES → Severity = Contraindicated
  └─ NO → Q2

Q2: Could the interaction potentially cause any of the following?
    - Death
    - Life-threatening adverse reaction (e.g., Torsades de Pointes,
      severe hemorrhage, hepatic failure, respiratory arrest)
    - Hospitalization or prolonged hospitalization
    - Permanent disability or injury
  ├─ YES → Severity = Major
  └─ NO → Q3

Q3: Could the interaction potentially cause any of the following?
    - Exacerbation of the underlying condition
    - Need for a change in drug therapy or dose adjustment
    - Additional monitoring requirements
    - Moderate adverse effects (not life-threatening)
  ├─ YES → Severity = Moderate
  └─ NO → Q4

Q4: Are clinical effects limited and unlikely to require a change in therapy?
  ├─ YES → Severity = Minor
  └─ NO → Re-evaluate, or label Unknown
```

### Additional Severity Considerations

**AUC Change Magnitude Reference** (for PK interactions):
- AUC increase ≥ 5-fold: Usually Major (especially with NTI drugs)
- AUC increase 2–5-fold: Major or Moderate (depends on therapeutic window)
- AUC increase 1.25–2-fold: Usually Moderate
- AUC increase < 1.25-fold: Usually Minor or not clinically significant

**Narrow Therapeutic Index (NTI) Drugs** — upgrade severity by one level when involved:
- warfarin, digoxin, phenytoin, carbamazepine, lithium,
  theophylline, cyclosporine, tacrolimus, sirolimus,
  aminoglycosides, vancomycin, methotrexate

---

## 2. Documentation Rating Decision Tree {#documentation}

```
Q1: Are there well-designed controlled studies (RCT or controlled PK study)
    that clearly establish the interaction exists?
  ├─ YES → Documentation = Excellent
  └─ NO → Q2

Q2: Is there any of the following evidence?
    - Multiple observational studies (cohort / case-control) with consistent results
    - Prospective uncontrolled PK study with clear results
    - Multiple well-documented case series
  ├─ YES → Documentation = Good
  └─ NO → Q3

Q3: Is there any of the following evidence?
    - A few case reports with plausible causality
    - Clear in vitro data but no clinical validation
    - Reasonable pharmacologic mechanism (known CYP pathway) but no
      studies on this specific drug pair
    - Good documentation for a pharmacologically similar drug (class effect)
  ├─ YES → Documentation = Fair
  └─ NO → Q4

Q4: Is there only the following evidence?
    - A single case report with unclear causality
    - Theoretical speculation only
    - Animal studies without human data
  ├─ YES → Documentation = Poor
  └─ NO → Q5

Q5: Is there no reasonable pharmacologic basis for the interaction?
  ├─ YES → Documentation = Unlikely
  └─ NO → Label Unknown and explain rationale
```

---

## 3. Onset Classification {#onset}

| Classification | Definition | Examples |
|---|---|---|
| **Rapid** | Clinical effects appear within 24 hours of co-administration | CYP inhibition-mediated acute toxicity; PD additive effects (e.g., dual QTc prolongation); absorption-level interference |
| **Delayed** | Clinical effects appear after more than 24 hours | CYP induction (typically 7–14 days to maximum effect); protein binding displacement with redistribution; accumulation of long half-life drugs |
| **Not specified** | Time course not clearly reported in the literature | Most interactions supported only by in vitro data |

---

## 4. Mechanism Classification Taxonomy {#mechanism}

### 4a. Pharmacokinetic (PK) Mechanisms

#### Absorption
- **pH alteration**: Acid-suppressive agents affecting pH-dependent absorption
- **Chelation/Complexation**: Metal ion chelation (e.g., antacids + fluoroquinolones)
- **Altered GI motility**: Changes in GI transit affecting absorption rate
- **P-gp inhibition/induction at gut**: Altered oral bioavailability via intestinal P-gp

#### Distribution
- **Protein binding displacement**
  - Clinical significance usually limited (increased free drug → increased clearance)
  - Exception: high protein binding + narrow therapeutic index drugs

#### Metabolism — most common PK mechanism
- **CYP inhibition**:
  - Reversible: competitive, non-competitive, uncompetitive
  - Mechanism-based (MBI / time-dependent): irreversible, effects persist longer
- **CYP induction**:
  - Typically mediated by PXR, CAR, AhR receptors
  - Takes 7–14 days to reach maximum effect
  - Effects also take days to weeks to resolve after discontinuation
- **UGT inhibition/induction**: Phase II glucuronidation
- **Other Phase I/II enzymes**: MAO, aldehyde oxidase, sulfotransferases

#### Excretion
- **Renal tubular secretion**: OAT, OCT transporter competition
- **Renal blood flow**: Drugs affecting GFR
- **Biliary excretion**: OATP, MRP, BCRP transporters

### 4b. Pharmacodynamic (PD) Mechanisms

| Pattern | Description | Clinical Example |
|---|---|---|
| **Additive** | Effects add directly | Dual CNS depressants → excessive sedation |
| **Synergistic** | Combined effect > sum of individual effects | Trimethoprim + Sulfamethoxazole |
| **Antagonistic** | Effects cancel each other | Beta-agonist + Beta-blocker |
| **QTc additive** | QTc prolongation risk stacking | Amiodarone + Fluoroquinolone |
| **Bleeding additive** | Bleeding risk stacking | Warfarin + NSAID |
| **Serotonergic additive** | Serotonin toxicity risk | SSRI + MAOi |
| **Nephrotoxic additive** | Nephrotoxicity stacking | Aminoglycoside + Vancomycin |
| **Hepatotoxic additive** | Hepatotoxicity stacking | Methotrexate + Alcohol |
| **Antifolate additive** | Folate depletion stacking | Methotrexate + Trimethoprim |

---

## 5. Literature Appraisal Checklist {#appraisal}

### 5a. Study Design Hierarchy (Oxford CEBM-adapted)
1. Systematic Review / Meta-analysis of DDI studies
2. RCT / Randomized PK crossover study
3. Prospective cohort / Non-randomized PK study
4. Retrospective cohort / Case-control study
5. Case series (≥3 cases)
6. Case report (1–2 cases)
7. In vitro study only
8. Expert opinion / Pharmacological reasoning

### 5b. Per-Article Data Extraction
- [ ] Study design
- [ ] Sample size (n)
- [ ] Drug doses used
- [ ] PK parameter changes (AUC ratio, Cmax ratio) — if PK study
- [ ] Clinical adverse event description — if available
- [ ] Mechanism explanation
- [ ] Author conclusions
- [ ] DOI / PMID

### 5c. Rapid Bias Assessment
- Conflicts of interest (industry-sponsored?)
- Sample representativeness
- Appropriate control group
- Statistical methods adequacy

---

## 6. Search Strategy Templates {#search}

### PubMed via web_search
```
Query 1: site:pubmed.ncbi.nlm.nih.gov "{DrugA}" "{DrugB}" interaction
Query 2: site:pubmed.ncbi.nlm.nih.gov "{DrugA}" "{DrugB}" pharmacokinetic
Query 3: site:pubmed.ncbi.nlm.nih.gov "{DrugA}" "{DrugB}" CYP
Query 4: site:pubmed.ncbi.nlm.nih.gov "{DrugA}" "{DrugB}" adverse
```

### PubMed MCP Tool (if connected)
```
search_articles: "({DrugA}) AND ({DrugB}) AND (drug interaction OR pharmacokinetic)"
search_articles: "({DrugA}) AND ({DrugB}) AND (cytochrome P450 OR CYP)"
```

### CrossRef API via web_fetch
```
https://api.crossref.org/works?query={DrugA}+{DrugB}+drug+interaction&rows=10&sort=relevance
https://api.crossref.org/works?query={DrugA}+{DrugB}+pharmacokinetic&rows=5&sort=relevance
```

### General WebSearch
```
Query 1: {DrugA} {DrugB} drug interaction clinical significance
Query 2: {DrugA} {DrugB} CYP metabolism interaction mechanism
Query 3: {DrugA} {DrugB} interaction case report
Query 4: {DrugA} metabolism CYP enzyme substrate inhibitor
Query 5: {DrugB} metabolism CYP enzyme substrate inhibitor
```

### FDA / DailyMed
```
Query 1: site:dailymed.nlm.nih.gov {DrugA} drug interactions
Query 2: {DrugA} {DrugB} FDA label interaction warning
```

---

## 7. CYP450 Quick Reference Table {#cyp450}

### Major CYP Enzymes — Common Substrates / Inhibitors / Inducers

| CYP | Notable Substrates | Notable Inhibitors | Notable Inducers |
|---|---|---|---|
| **3A4** | midazolam, simvastatin, cyclosporine, tacrolimus, fentanyl, apixaban | ketoconazole, itraconazole, clarithromycin, ritonavir, grapefruit juice | rifampin, carbamazepine, phenytoin, St. John's wort |
| **2D6** | codeine, tramadol, tamoxifen, metoprolol, fluoxetine | fluoxetine, paroxetine, bupropion, quinidine | (no clinically significant inducers) |
| **2C19** | omeprazole, clopidogrel, voriconazole, diazepam | fluconazole, fluvoxamine, omeprazole | rifampin, St. John's wort |
| **2C9** | warfarin, phenytoin, losartan, celecoxib | fluconazole, amiodarone, metronidazole | rifampin |
| **1A2** | theophylline, caffeine, tizanidine, olanzapine | fluvoxamine, ciprofloxacin | smoking, omeprazole (mild) |
| **2B6** | efavirenz, bupropion, methadone | ticlopidine | rifampin |
| **2E1** | acetaminophen (minor), ethanol | disulfiram | ethanol (chronic), isoniazid |

### FDA-Recommended Index Substrates / Inhibitors / Inducers
(Full list: FDA Guidance "In Vitro Drug Interaction Studies" 2020)

- **Strong CYP3A4 Inhibitor**: itraconazole, ketoconazole, clarithromycin, ritonavir
- **Moderate CYP3A4 Inhibitor**: erythromycin, fluconazole, diltiazem, verapamil
- **Weak CYP3A4 Inhibitor**: cimetidine
- **Strong CYP3A4 Inducer**: rifampin, carbamazepine, phenytoin
- **Moderate CYP3A4 Inducer**: efavirenz, bosentan

---

## 8. Common PD Interaction Patterns {#pd-patterns}

### 8a. QTc Prolongation Risk
High-risk combinations: any two "Known Risk" drugs (CredibleMeds classification)
- Known Risk drugs include: amiodarone, sotalol, haloperidol, methadone,
  ondansetron, moxifloxacin, droperidol
- Risk factors: hypokalemia, hypomagnesemia, female sex, cardiac disease, advanced age

### 8b. Serotonin Syndrome Risk
High-risk combination patterns:
- MAOi + any serotonergic agent → Contraindicated (usually)
- SSRI/SNRI + Tramadol / Fentanyl / Linezolid → Major
- SSRI + Triptans → Moderate (debated)
- Symptoms: clonus, agitation, diaphoresis, hyperthermia, hyperreflexia

### 8c. Bleeding Risk
- Warfarin/DOAC + NSAID → Major
- Dual antiplatelet + Anticoagulant → Major
- SSRI + Anticoagulant → Moderate (SSRIs impair platelet function)

### 8d. CNS Depression
- Opioid + Benzodiazepine → Major (FDA Black Box Warning)
- Opioid + Gabapentinoid → Moderate–Major
- Multiple CNS depressants → cumulative additive effect

### 8e. Hyperkalemia Risk
- ACEi/ARB + K-sparing diuretic → Moderate–Major
- ACEi/ARB + Trimethoprim → Moderate
- Multiple RAAS blockers → Major

### 8f. Antifolate Stacking
- Methotrexate + Trimethoprim/Sulfamethoxazole → Major
- Methotrexate + Phenytoin → Moderate
- Any combination of DHFR inhibitors → assess additively

---

## Final Notes

- When search results are insufficient, expand to class-effect searches for pharmacologically similar drugs.
- If no literature is found at all, explicitly report "No direct literature identified" and provide an assessment based on pharmacologic reasoning alone.
- Always include the disclaimer that this report cannot replace certified drug information systems.
- When a drug pair has multiple interaction pathways, assess each pathway separately and take the most severe overall grade.
- Pay attention to dose-dependent and population-specific differences (e.g., pediatric vs. adult, renal impairment, genetic polymorphisms).
