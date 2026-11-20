---
status: undecided
date: 2026-11-13
decision-makers: jim@openphase-labs.com
---

# A host-owned core, extended through plugins

## Context and Problem Statement

TSIGMA ingests traffic-signal event data from sources that cannot be trusted to be
correct: controllers with wrong clocks, stale configuration, swapped hardware, and
vendors that violate their own published formats. It must also be extensible by third
parties whose plugins may be proprietary and whose defects TSIGMA cannot inspect or fix.
Before deciding what extends the system, the thing being extended has to be defined.

## Decision Drivers

* Data integrity is the product; an analytic over silently corrupted events is worse
  than none.
* Third parties extend the system without modifying it.
* A plugin's defect or crash cannot corrupt the store.

## Considered Options

* A host-owned core, extended through out-of-process plugins
* In-process plugin registration
* Each acquisition path persisting for itself
* The spine decomposed into independently deployed services

## Decision Outcome

Chosen option: "A host-owned core, extended through out-of-process plugins", because it
keeps validation and persistence whole, in one place, behind one boundary.

The **core** is the non-plugin TSIGMA codebase. At runtime it is the **host**, and it
owns:

* **the data plane** -- database connections, credentials, sessions, and the schema;
* **the integrity spine** -- consume, validate, flag, persist;
* **lifecycle** -- ordered startup and shutdown;
* **configuration and audit**;
* **the API surface**, including its auth enforcement.

**Acquisition is outside the spine.** Reaching a device and decoding its format is a
plugin's work, and one plugin does both. A poller and its decoder are the same thing:
each controller format has exactly one decoder, so a Q-Free poller cannot use a McCain
decoder. Plugins are always separate processes, on the same host or another. The host's
first sight of any event is when it consumes it.

**The spine is whole and in one place.** Events reach the database only through the
host's consumer. One point resolves identity, one point applies validation, one route
leads into the store.

No plugin has database access.

Plugins are leaves. They acquire and transform; they do not modify the core or extend it
at points it has not declared. Extend through plugins; never modify core code to add a
capability.

### Consequences

* Good, because nothing reaches the store without passing the host's validation,
  including data from a plugin nobody at the agency can read.
* Good, because a plugin crash is that plugin's crash, and a plugin that stops
  publishing shows as a gap.
* Bad, because the host cannot verify completeness against a source it never saw; what
  it guarantees begins at consume.
* Bad, because a plugin that needs data the host does not expose waits until the host
  exposes it.
* Good, because a poller's checkpoint needs no database access: the host passes each
  endpoint's high-water mark in, and the plugin returns the new one.
* Neutral, because every new capability raises a "core or plugin?" question that is
  answered again each time.

### Confirmation

Review: no plugin holds database credentials, no code path outside the host's consumer
writes events to the database, and no plugin runs in the host's process.

## Pros and Cons of the Options

### A host-owned core, extended through out-of-process plugins

* Good, because validation and persistence have one owner at one boundary.
* Good, because plugins are isolated from the host's process and from each other.
* Bad, because the core must stay small by discipline; nothing enforces it.

### In-process plugin registration

* Good, because it is the simplest to build.
* Bad, because it gives no crash or dependency isolation and cannot host a proprietary
  plugin.
* Bad, because nothing structural stops a component from bypassing validation.

### Each acquisition path persisting for itself

* Good, because it removes a hop between acquisition and the store.
* Bad, because identity and validation live in as many places as there are formats,
  and each can lapse independently.

### The spine decomposed into independently deployed services

* Good, because it gives maximal isolation.
* Bad, because it splits validate and persist across network boundaries, the one thing
  this decision keeps whole.

## More Information

* ADR-0001
