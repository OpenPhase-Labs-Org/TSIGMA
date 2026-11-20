# TSIGMA

**Traffic Signal Intelligence: Gathering Metrics & Analytics**

An open source platform for collecting, storing, and analyzing traffic signal
performance data -- an open source implementation of Automated Traffic Signal
Performance Measures (ATSPM).

## Status

Early. This repository is a ground-up rewrite, in Go, and contains no working
software yet. Decisions are recorded under `docs/developers/adr/` as they are made; until a
capability is recorded there, treat any description of it as intent, not fact.

## Lineage

TSIGMA is born from UDOT's ATSPM 4.x and 5.x, and from Kimley-Horn's continued
updates to 4.x. The measures, the high-resolution event semantics, and the
operational patterns come from that work; TSIGMA re-implements them, it does not
originate them.

## Why it exists

Traffic operations is a closed ecosystem. TSIGMA's plugins target a published
interface, the TSIGMA Contract, rather than an implementation detail of any one
product, so an agency can choose its host, its vendors, and its plugins
independently of each other -- and keep its data when it changes any of them.

## License

Mozilla Public License 2.0. See [LICENSE](LICENSE).
