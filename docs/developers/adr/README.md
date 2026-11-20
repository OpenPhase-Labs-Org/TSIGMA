# Architecture Decision Records

Records of TSIGMA's significant architecture and design decisions, one file per
decision, in the order they were made.

A record states a decision as of its date. It does not describe how the system works
today.

## Index

Numbers are permanent and never reused, so a gap in the sequence is normal.

| # | Title | Status |
|---|-------|--------|
| [0001](0001-why-decisions-are-recorded.md) | Architecture decisions are recorded, and a record states one as of its date | accepted |
| [0002](0002-madr-is-the-record-format.md) | MADR is the record format, numbered sequentially with the number as identity | accepted |
| [0003](0003-when-a-decision-earns-a-record.md) | A decision earns a record when reversing it is expensive or constrains work not yet done | accepted |
| [0004](0004-a-record-is-superseded-never-rewritten.md) | A record is superseded, never rewritten, and the test is whether a reader would build differently | accepted |
| [0005](0005-records-are-cited-and-cite-nothing-outward.md) | Documents and code cite records; records cite nothing outward | accepted |
| [0006](0006-a-host-owned-core-extended-through-plugins.md) | A host-owned core, extended through plugins | undecided |

## Adding a record

Copy [template.md](template.md) to the next number, fill it in, and add a row to the
index.
