---
status: accepted
date: 2026-11-12
decision-makers: jim@openphase-labs.com
---

# Documents and code cite records; records cite nothing outward

## Context and Problem Statement

A record outlives the file layout, module names, design documents, the repository's
host, and the project's accounts on other services. A reference that has rotted reads
as authoritative and sends the reader somewhere wrong, and because a record is frozen,
nothing will come back to fix it.

## Decision Drivers

* A record stays correct when the repository, its host, or its layout changes.
* Every reference in a record resolves for as long as the record exists.
* Restructuring code or documents never requires touching a record.

## Considered Options

* One-way citation, with no URLs in records
* Records link to the documents and code they govern
* URLs allowed for stable external references
* A separate index of which documents cite which records

## Decision Outcome

Chosen option: "One-way citation, with no URLs in records", because it is the only
option where every reference a record makes cannot rot.

Documents and code cite records. Records do not cite documents, code, plans, tickets,
or working state.

A record may cite:

* another record, by number;
* an external standard or specification, by identifier -- MADR 4.0.0, RFC 7807,
  NTCIP 1202, MPL-2.0;
* a name the decision itself establishes -- a module, schema, field, term, or path the
  record defines.

An external artifact is named, never located: its identity is its name and version.
A repository URL, a git host, an organisation's account, or a filesystem path the
record does not itself establish is not cited.

Records carry no URLs.

### Consequences

* Good, because renaming the repository, changing host, restructuring directories, or
  deleting a document never touches a record.
* Good, because following citations from record to record never leads out of the set.
* Bad, because the reader resolves an identifier themselves.
* Neutral, because a record never shows what cites it; a document states which records
  it rests on.

### Confirmation

Review: a record contains no URL, and every citation is a record number, a standard's
identifier, or a name the record itself establishes.

## Pros and Cons of the Options

### One-way citation, with no URLs in records

* Good, because nothing a record points at can move out from under it.
* Bad, because the reader does the lookup.

### Records link to the documents and code they govern

* Good, because the link is useful the day it is written.
* Bad, because every restructuring becomes a records-maintenance task, and frozen
  records cannot be maintained.

### URLs allowed for stable external references

* Good, because the reader is one click from the source.
* Bad, because every link looks permanent to the person adding it; the exception has
  no bound.

### A separate index of which documents cite which records

* Good, because a reader could find what depends on a record.
* Bad, because it is a second artifact maintained by hand that goes stale without failing.

## More Information

* ADR-0001
* ADR-0004
