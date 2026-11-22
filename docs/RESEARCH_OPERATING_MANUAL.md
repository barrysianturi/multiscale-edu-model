# Multiscale Education Research Programme — Research Operating Manual

**Version:** v0.1  
**Status:** Active  
**Canonical location:** `docs/RESEARCH_OPERATING_MANUAL.md`

---

## 1. Source of truth

This GitHub repository is the canonical research workspace and also serves as the Obsidian vault.

The three-tool architecture is:

```text
Mendeley = evidence
Obsidian = thinking
GitHub = source of truth
```

### Mendeley
Use for PDFs, bibliographic metadata, citation management, highlights, and short paper-level notes.

### Obsidian
Use for concepts, literature synthesis, Model Atlas notes, research questions, decisions, meetings, and paper thinking.

### GitHub
Use for canonical conventions, code, registries, experiments, simulations, manuscripts, releases, and reproducibility.

---

## 2. Canonical repository structure

```text
multiscale-education/
│
├── README.md
├── CHARTER.md
├── CHANGELOG.md
├── .gitignore
│
├── 00 Home/
├── 01 Research Programme/
├── 02 Concepts/
├── 03 Literature Notes/
├── 04 Model Atlas/
├── 05 Experiments/
├── 06 Papers/
├── 07 Decisions/
├── 08 Meetings/
├── 09 Archive/
│
├── docs/
│   ├── RESEARCH_OPERATING_MANUAL.md
│   ├── ontology/
│   ├── mathematics/
│   └── data/
│
├── registry/
├── src/
├── simulations/
├── configs/
├── tests/
└── templates/
```

The numbered folders are human-facing and Obsidian-facing. The engineering folders hold structured metadata, formal documentation, code, simulation artifacts, configs, and tests.

There must be no duplicate top-level `papers/` or `experiments/` folders. Canonical homes are:

```text
05 Experiments/
06 Papers/
```

---

## 3. Research object IDs

| Object | Prefix | Example |
|---|---|---|
| Model | `MOD` | `MOD-001` |
| Experiment | `EXP` | `EXP-001` |
| Simulation | `SIM` | `SIM-001` |
| Paper | `PAP` | `PAP-001` |
| Dataset | `DAT` | `DAT-001` |
| Research question | `RQ` | `RQ-001` |
| Decision | `DEC` | `DEC-001` |
| Concept | `CON` | `CON-001` |
| Meeting | `MTG` | `MTG-001` |

Rules:
1. IDs are permanent.
2. Never recycle deleted IDs.
3. Use three digits initially.
4. Renaming does not change the ID.
5. Use the same ID across notes, registries, code, papers, and experiments.

---

## 4. File naming

Use:

```text
MOD-014_cunha_heckman_skill_formation.md
EXP-003_peer_network_policy_shock/
PAP-001_multiscale_framework/
DEC-004_decision_kernel_primitive.md
```

Rules:
- ID first
- lowercase descriptive text
- underscores instead of spaces for technical folders/files
- never use `final`, `final2`, `latest`, or `revised_final`

Git stores version history.

---

## 5. Versioning

Use lightweight semantic versioning:

```text
v0.1.0 = first usable working version
v0.2.0 = substantive revision
v0.2.1 = minor correction
v1.0.0 = first stable/public release
```

Meaningful public releases should receive Git tags such as:

```text
PAP-001-v0.1.0
SIM-001-v1.0.0
FRAMEWORK-v1.0.0
```

---

## 6. Status lifecycles

### Models
`Candidate → Mapped → Formalized → Implemented → Validated → Archived`

### Experiments
`Proposed → Designed → Running → Analyzed → Closed`

### Simulations
`Specified → Implemented → Tested → Validated → Released`

### Papers
`Idea → Outline → Drafting → Internal Review → External Review → Preprint → Submitted → Published`

### Research questions
`Open → Active → Answered → Reframed → Dropped`

---

## 7. Model Atlas standard

Every significant model should record:

```text
ID
Model name
Citation
Discipline
Scale
Timescale
Agents
State variables
Actions
Information
Decision rule
Transition rule
Interaction structure
Observables
Parameters
Empirical basis
Identification strategy
Key assumptions
Known results
Limitations
Framework mapping
Implementation status
Connections
```

Framework mapping:

```text
X = states
A = actions
Pi = decision rule
F = dynamics
G = interaction/network structure
P = policy/institutional environment
C = cross-scale mapping
O = observation/measurement process
```

---

## 8. Experiment standard

Every experiment must record:

```text
Experiment ID
Research question
Hypothesis
Related model(s)
Model/code version
Dataset or simulation population
Treatment/intervention
Control/comparator
Outcome variables
Analysis plan
Random seeds
Parameters
Exclusion rules
Results
Interpretation
Limitations
Git commit
Status
```

Minimum reproducibility requirement:

```text
repository commit
+ configuration
+ data reference
+ documented environment
```

must reproduce the result.

---

## 9. Simulation standard

Each simulation receives a `SIM-XXX` ID and lives under:

```text
simulations/SIM-XXX/
```

Recommended contents:

```text
README.md
config.yaml
run.py
analysis.py
outputs/
tests/
```

Its README should document objective, model, assumptions, states, parameters, initialization, seeds, outputs, validation checks, limitations, related experiments, related papers, Git commit, and version.

---

## 10. Dataset convention

Every dataset receives a `DAT-XXX` ID.

Raw data should generally stay outside Git if sensitive, large, or restricted.

Each dataset should record:

```text
Dataset ID
Name
Source
Storage location
Unit of observation
Coverage
Raw-data policy
Processing pipeline
Data dictionary
Privacy/legal constraints
Related papers/experiments
```

Core rule:

```text
raw → processed → analysis → outputs
```

Raw data is immutable.

---

## 11. Paper convention

Every paper receives a `PAP-XXX` ID and lives under:

```text
06 Papers/PAP-XXX_short_title/
```

Recommended contents:

```text
README.md
manuscript.tex
references.bib
figures/
tables/
appendix/
reproducibility/
```

The README should contain title, status, research question, contribution, related model IDs, related experiment IDs, related simulation IDs, current version, target venue, and next action.

---

## 12. Decision log

Major scientific or architectural decisions receive `DEC-XXX`.

Record:

```text
Decision
Date
Context
Alternatives considered
Rationale
Consequences
Evidence
What would cause reversal?
Related objects
```

Examples:
- `DEC-001` — Use decision kernels rather than universal utility maximization
- `DEC-002` — Cross-scale consistency does not require literal microscopic simulation
- `DEC-003` — Raw data is immutable

---

## 13. Research questions

Every major research question receives `RQ-XXX`.

Record:
- question
- why it matters
- scale
- relevant disciplines
- current answer
- competing hypotheses
- required evidence
- related models
- related experiments
- status

The programme should be organized around questions, not only papers.

---

## 14. Concept notes

Concept notes synthesize multiple sources; they are not paper summaries.

Recommended structure:
- definition
- intuition
- formal representation
- evidence
- competing interpretations
- relevant scales
- connections
- open questions
- programme implications

---

## 15. Literature workflow

For an important paper:

```text
Paper
→ Mendeley
→ read/highlight
→ source-level note in 03 Literature Notes
→ update relevant concept/model notes
→ update Model Atlas if applicable
→ link to relevant research questions
```

Mendeley stores the evidence object. Obsidian stores your synthesis.

---

## 16. AI-assisted research rules

AI may be used heavily for:
- literature extraction
- code scaffolding
- symbolic derivation
- documentation
- test generation
- sensitivity analysis
- comparison across papers
- drafting

But:

> AI output is never itself scientific evidence.

Literature workflow:

```text
source paper → AI extraction → human verification → notes/registry
```

Code workflow:

```text
formal specification → AI-generated code → tests → validation → accepted implementation
```

Mathematics:

```text
AI derivation → independent check → symbolic/numerical verification where possible
```

LLM-generated human behavior must always be labeled synthetic.

---

## 17. Evidence hierarchy

Default programme ordering:

```text
credible causal evidence
> validated structural evidence
> replicated observational regularities
> calibrated simulation
> unvalidated simulation
> AI-generated behavior
```

This hierarchy is defeasible, but deviations must be justified.

---

## 18. Scientific admission rule

A new component enters the framework only if it contributes to at least one of:

1. recovering established theory;
2. reproducing a robust empirical regularity;
3. generating a falsifiable prediction;
4. improving prediction;
5. explaining an otherwise unexplained mechanism;
6. materially changing a policy conclusion.

Conceptually:

```text
Add component Z only if
expected scientific value > added complexity cost.
```

---

## 19. Modularity

Every scale-specific component should be replaceable without rebuilding the entire system.

Examples:
- learner model can change without rewriting school choice;
- network formation can change without rewriting measurement;
- policy modules should operate through common interfaces.

---

## 20. Git conventions

Recommended branches:

```text
main
feature/<short-name>
paper/<PAP-ID>
experiment/<EXP-ID>
```

Good commits:

```text
Add MOD-014 framework mapping
Implement SIM-001 learner transition
Revise PAP-001 cross-scale proposition
Fix EXP-003 random seed handling
```

Bad commits:

```text
update
changes
stuff
final
```

---

## 21. Reproducibility rules

Every computational result used in a paper should record:
- Git commit
- environment
- dependency versions
- configuration
- data ID
- seed
- analysis script
- output path

---

## 22. Citation keys

Preferred citation-key pattern:

```text
AuthorYearKeyword
```

Examples:

```text
Cunha2007Technology
Todd2003Production
Heckman2025Microdynamics
```

---

## 23. Obsidian linking

Use links heavily:

```text
[[MOD-014 Cunha-Heckman Skill Formation]]
[[RQ-003 Cross-scale learner aggregation]]
[[CON-008 Dynamic Complementarity]]
[[DEC-001 Decision Kernels]]
```

Use tags sparingly.

---

## 24. Backup

At minimum:
- GitHub for code, notes, registries, and manuscripts
- Mendeley cloud for references/PDFs
- one external or cloud backup for research data
- no irreplaceable artifact in only one location

---

## 25. Weekly maintenance

Once per week:
1. process Mendeley Inbox;
2. assign IDs to new major objects;
3. update registries;
4. record important decisions;
5. update active research questions;
6. commit and push;
7. review next milestone.

Target: 30–45 minutes.

---

## 26. Definition of Done for T002

T002 is complete when:

- [ ] private GitHub repository exists
- [ ] repository structure is created
- [ ] this manual is committed
- [ ] repository root opens successfully as Obsidian vault
- [ ] Mendeley collections are created
- [ ] ID conventions are adopted
- [ ] all registries exist
- [ ] templates are installed
- [ ] reproducibility rules are documented
- [ ] AI-use rules are documented
- [ ] one model is processed end-to-end
- [ ] one dummy experiment is processed end-to-end
- [ ] another researcher could understand where every object belongs

---

## 27. End-to-end acceptance test

Before T002 is marked Done:

```text
source paper
→ Mendeley
→ literature note
→ Model Atlas note
→ MOD-001
→ registry/models.csv
→ minimal implementation
→ SIM-001
→ EXP-001
→ result
→ Git commit
→ linked Obsidian note
```

If every step is traceable in both directions, the infrastructure works.

---

## 28. Change control

When a convention changes:
1. update this manual;
2. update `CHANGELOG.md`;
3. create a `DEC-XXX` entry if scientifically important;
4. do not silently rewrite historical conventions.

The operating system may evolve, but only explicitly.
