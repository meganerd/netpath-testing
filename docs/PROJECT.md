# Project charter

## Purpose

Build a working network-path diagnostic program while evaluating Valen as a
language for native networking tools. The project favors open formats,
self-hostable dependencies, and inspectable behavior.

## First usable milestone

A command-line program that accepts an IPv4 target and produces a stable hop
table with:

- hop number and responding address;
- sent/received counts and packet loss;
- last, average, best, worst, and standard-deviation latency;
- reverse-DNS name when available;
- deterministic CSV output;
- useful errors for missing privileges and unsupported platforms.

## Compatibility strategy

Hopscout is a behavioral reference, not a source-code base. Tests should use
captured fixtures and black-box observations so the rewrite remains independent
and its design can follow Valen's strengths.

## Valen learning log

Record compiler version/commit, build commands, workarounds, missing standard
library capabilities, and any required foreign-function interfaces. Prefer
small executable spikes before committing the architecture to an unverified
language feature.

## GeoIP principles

Geolocation enrichment must be optional and must not claim false precision.
Every result should carry its provider, lookup time, claimed precision, and
confidence. Conflicts between GeoIP, PTR/site evidence, and latency plausibility
should be visible to users and preserved in machine-readable output.

The first regression case uses:

- `51.10.34.13` / `be9.owr02.co7.ntwk.msn.net`
- `51.10.6.234` / `po1013.rwa03.co7.ntwk.msn.net`

Both were returned as London by ip-api despite topology and site evidence
placing CO7 in Quincy, Washington.

## Non-goals for the first milestone

- GUI or world map
- privileged helper/service separation
- feature-for-feature Hopscout parity
- silently overriding uncertain provider data with hostname guesses

