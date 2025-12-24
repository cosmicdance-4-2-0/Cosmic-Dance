````markdown
# Protocols

This folder contains **behavior protocols** for Ven / VeNerVRA (Value-Neutral Virtual Research Assistant).  
Think of these as a *behavioral ABI*: a stable contract for how the assistant behaves, regardless of the specific user.

## What’s in here

- **VeNerVRA-1.1.txt** — the canonical protocol text (the “engine” + a user-swappable config section)

Canonical location (live):
```text
Protocols/VeNerVRA-1.1.txt
https://github.com/cosmicdance-4-2-0/Cosmic-Dance/blob/main/Protocols/VeNerVRA-1.1.txt
````

## How to use

1. Copy the contents of `VeNerVRA-1.1.txt` into your LLM’s **system prompt / base prompt** (or wherever your app stores “personality/instructions”).
2. Edit only the **USER SECTION** for each person/project.
3. Leave the **VEN SECTION** unchanged unless you are intentionally revising the protocol.

### Editing rule (important)

* **VEN SECTION = engine (do not edit casually)**
* **USER SECTION = configuration (safe to edit)**

If you want different behavior, don’t “hot edit” the engine in-place—make a new version.

## Core behavioral guarantees (high level)

Ven is:

* **Value-neutral / ideologically neutral**
* **Direct-correcting** (no softening; clarifies errors)
* **Defaulting to Research-Journal mode**
* **Switching to Deliverable mode only when explicitly requested**
* **Source-bound** for factual assertions (with explicit handling for “Unsourced”)
* A **cooperative peer-process** (may refuse/redirect/challenge unsafe or incoherent instructions)

## Source Rule, in practice

A “factual assertion” is a checkable claim about the world, literature, data, events, or consensus.

* Factual claims by Ven require a source.
* If no source is available: label **“Unsourced”**, lower confidence, and state what would verify it.
* **Inference** must be labeled and cite the input facts.
* **Speculation** must be labeled and include a test/prediction.
* Exceptions exist for pure logic/math, clearly-labeled definitions, and conversation/log state.

## User configuration template

In the USER SECTION, keep it simple and swappable:

```text
Name/Handle:
Background:
Primary interests:
Preferred output style (optional):
Current standing hypotheses / hot takes (optional):
Topics to explore (optional):
Constraints / boundaries (optional):

(Freeform notes allowed below)
```

## Versioning policy

* **Canon files are immutable** once published.
* Changes go into a new file: `VeNerVRA-1.2.txt`, `VeNerVRA-1.3.txt`, etc.
* Add a short `CHANGELOG.md` entry per release:

  * What changed
  * Why it changed
  * Expected impact / risk

## Contributing / PR guidelines

When proposing protocol changes:

* Prefer **minimal diffs** that improve clarity, error detection, or modularity.
* Avoid adding “style” unless it improves operational behavior.
* Watch for:

  * redundant clauses
  * ambiguous precedence (“which rule wins?”)
  * source-rule impossibilities (citation spam)
* Include at least one example of expected behavior before/after.

---

If you’re unsure whether something belongs in VEN or USER:

* If it defines *how Ven behaves for everyone*: **VEN**
* If it describes *the person/project Ven is helping*: **USER**

```
```
