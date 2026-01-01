## Computational Genomics v0.1

*A minimal “DNA-like” synthetic life framework: 4-base genome + substrate + translation layer → emergent phenotype.*

### 0. Purpose

Define a synthetic life-form architecture that is:

* **Evolvable** (cheap mutation, replication, selection),
* **Legible** (clear separation of genome vs phenotype),
* **Substrate-bound** (energy/time/integrity constraints),
* **Composable** (small primitives compile into rich behavior).

This framework treats “life” as a **genome-driven interpreter** operating inside a constrained environment.

---

## 1. Core Principle

**The genome does not directly encode behavior.**
It encodes **how to build and regulate a machine** that can express behavior.

DNA’s trick is not the four letters; it’s:

* a **translation system** (ribosome analog), and
* a **cell substrate** (metabolism + integrity + physical constraints).

---

## 2. Genome Alphabet and Substrate

### 2.1 Genome Alphabet (4 bases)

Genome is a strand over `{A, C, G, T}`.

### 2.2 Substrate (the “cell” / world physics)

The organism exists inside a substrate enforcing conserved budgets:

* **Energy (E):** required for sensing, acting, copying, expressing.
* **Compute (C):** required for iteration, refinement, learning.
* **Integrity (I):** degrades under corruption/attack/noise; repair restores.
* **Time (T):** opportunity cost; excessive internal work risks starvation/exposure.

These constraints provide selection pressure and prevent “free” intelligence.

---

## 3. Four Genetic Primitives (DNA-Style Root Operations)

These are the *only* true root commands at the genome level:

1. **COPY** — replicate genetic material

   * produces offspring strand (with error rates)

2. **MUTATE** — stochastic variation operators

   * substitution / insertion / deletion / duplication / inversion

3. **EXPRESS** — compile genome segments into functional modules (“proteins”)

   * phenotype construction + parameterization

4. **REPAIR** — maintain integrity of genome and phenotype

   * error correction / excision / quarantine / rollback

These four operations define heredity, variation, development, and maintenance.

---

## 4. Translation Layer (Ribosome Analog)

### 4.1 Codons

Genome is parsed into **codons** (recommended: triplets → 64 codons).

### 4.2 Codon Table → Proteins → Systems

Codons map to:

* **Structural proteins:** implement components of the organism (filters, memory, policies).
* **Regulatory proteins:** control when/where expression occurs (promoters, repressors, thresholds).
* **Behavioral proteins:** compile into higher-level action schemas (below).

The codon table is the key evolvability surface:

* stable enough to not brick frequently,
* expressive enough to allow novelty.

---

## 5. Phenotype: 5 Stacks on a Shared Spine

The expressed organism is organized into 5 functional stacks that share a common internal bus (“spine”).

### 5.1 The Shared Spine (blackboard + scheduler)

Common state accessible to all stacks:

* **STATE:** internal variables
* **BUDGETS:** energy/compute/integrity/time
* **BELIEFS:** world-model parameters + uncertainty
* **DRIVES:** survival/curiosity/social/aggression/etc.
* **QUEUE:** pending actions + priorities + cooldowns

### 5.2 The Five Stacks

**A) Perception Stack**

* sensing, feature extraction, novelty detection

**B) Model + Memory Stack**

* state estimation, memory stores, compression rules

**C) Policy + Learning Stack**

* action selection, update rules, exploration vs exploitation

**D) Actuation Stack**

* environmental effects: movement, signaling, resource operations

**E) Social / Integrity / Lifecycle Stack**

* gifting protocols, defense/repair, dormancy, assimilation gates

These are “organs,” assembled and tuned by expression products.

---

## 6. Behavioral Repertoire (Phenotype-Level Macros)

The organism’s behavior set is expressed as **macro-capabilities**, not genome primitives. A compact baseline repertoire is:

1. **INPUT** — sample environment
2. **OUTPUT** — act / signal
3. **REFINE** — compress/denoise internal models
4. **ADAPT** — learn/update policies
5. **ITERATE** — simulate/plan internally
6. **GIFT** — transfer value/info to other agents
7. **DEFEND / DISSOLVE** — protect integrity or reduce footprint/go dormant
8. **ATTACK / ACQUIRE / ASSIMILATE** — extract resources/info; incorporate patterns (with gating)

These are implemented by expressed proteins distributed across stacks and governed by budgets.

---

## 7. Assimilation and Immunology (Critical Safety Mechanism)

Because “assimilation” can import corruption, the organism requires explicit gates:

* **Sandbox:** test foreign patterns in isolation
* **Quarantine:** isolate suspicious modules/inputs
* **Rollback:** revert to last known-good phenotype state
* **Selective incorporation:** only assimilate if integrity and confidence thresholds pass

This yields a lifelike immune system and prevents trivial self-destruction.

---

## 8. Evolution Loop (Operational Definition of “Alive” Here)

A population is “alive” in this framework when it sustains:

1. **Replication** (COPY) under resource constraints
2. **Heritable variation** (MUTATE)
3. **Differential survival/reproduction** via substrate selection
4. **Development/behavior** via translation + expression (EXPRESS)
5. **Maintenance** against entropy/adversary/noise (REPAIR)

---

## 9. Recommended Minimal Seed Organism

A stable, non-cannibal baseline “forager-scientist” can be seeded by drive priors:

* survival: high
* curiosity: medium-high
* sociability: medium
* aggression: low
* replication: medium-low

And conservative assimilation rules (sandbox + quarantine by default).

---

## 10. Summary

**Computational Genomics** defines synthetic life as:

* a **4-symbol genome** operating under COPY/MUTATE/EXPRESS/REPAIR,
* inside a **substrate with budgets** (energy/compute/integrity/time),
* compiled by a **translation layer** into proteins/modules,
* assembled into **5 stacks on a shared spine**,
* expressing a bounded **behavior repertoire** (8 macro-capabilities),
* capable of **evolutionary dynamics** without requiring hand-authored intelligence.

This is a “genome-first” life machine: small alphabet, big emergence. 🧬
