---
status: accepted
date: 2026-11-12
decision-makers: jim@openphase-labs.com
---

# MADR is the record format, numbered sequentially with the number as identity

## Context and Problem Statement

Records are written over years by more than one hand and read by people outside the
project. Readers need to know where to look in any record, writers need to know what
is expected, and both need it without installing anything.

## Decision Drivers

* One shape, so every record reads the same way.
* Legible as plain Markdown on a git host, in a terminal, or in an editor.
* A citation target that never changes.

## Considered Options

* MADR 4.0.0, every section kept, written tersely
* MADR 4.0.0 with its optional sections dropped
* Nygard's original format
* A tool-managed record set

## Decision Outcome

Chosen option: "MADR 4.0.0, every section kept, written tersely", because it gives
rejected options and conformance a named home, and terse content keeps it readable.

Records follow `template.md`. Every section is kept; each holds short statements of
fact, not essay prose.

Records are numbered sequentially from `0001`, four digits, and named
`NNNN-short-kebab-title.md`. The number is the record's permanent identity: never
reused, never reassigned, and how records cite each other.

### Consequences

* Good, because every record answers the same questions in the same places.
* Good, because nothing needs installing to read or write a record.
* Bad, because nothing validates a record's shape; conformance is copying the template.
* Neutral, because spent numbers leave gaps in the sequence, and a gap is not an error.
* Neutral, because the number orders records by date, not by importance.

### Confirmation

Review: a record has the template's sections, in order, and its number is unused.

## Pros and Cons of the Options

### MADR 4.0.0, every section kept, written tersely

* Good, because considered options and their trade-offs are always written down.
* Good, because Confirmation states how the decision is checked.
* Bad, because a short decision still carries every heading.

### MADR 4.0.0 with its optional sections dropped

* Good, because records are shorter.
* Bad, because the sections most easily skipped -- alternatives and confirmation --
  are the ones most needed later.

### Nygard's original format

* Good, because it is minimal.
* Bad, because rejected options have no named home.

### A tool-managed record set

* Good, because indexes and status could be generated and checked.
* Bad, because reading a decision would begin with installing something.

## More Information

* MADR 4.0.0 (Markdown Architectural Decision Records)
* ADR-0001
