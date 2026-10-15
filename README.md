# netpath-testing

An experimental network-path diagnostic tool written in
[Valen](https://github.com/valen-lang/Valen).

This project has two goals:

1. Produce a useful, self-hostable traceroute/MTR-style program.
2. Learn where Valen is ready—or not yet ready—for practical systems and
   networking software.

The initial behavioral reference is
[Hopscout](https://github.com/ABowlOfEleven/hopscout). This is an independent
rewrite: implementation code will be developed in Valen rather than copied.

## Project status

Early experiment and design scaffold. Valen itself is still a prototype, so
compiler limitations and missing library support are expected findings rather
than surprises.

## Planned phases

- Establish a reproducible Valen toolchain and minimal CLI.
- Implement address parsing, probing, hop statistics, and text/CSV output.
- Add reverse-DNS and ASN enrichment behind clear interfaces.
- Add geolocation with provider provenance, configurable data sources, and
  explicit uncertainty.
- Experiment with detecting implausible GeoIP results using topology, verified
  infrastructure site mappings, and latency bounds.
- Compare functionality and operational behavior with Hopscout.

## GeoIP experiment

The motivating case is Microsoft backbone addresses that a public GeoIP
provider maps to London even though PTR site codes and Vancouver-origin RTTs
place the routers at Microsoft's CO7 Columbia campus in Quincy, Washington.

Unlike a design that stores one provider's city as fact, this project will aim
to retain:

- provider and lookup timestamp;
- confidence/precision;
- contradictory evidence;
- an `unknown` or `conflicting` result when evidence cannot be reconciled.

See [docs/PROJECT.md](docs/PROJECT.md) for the initial scope and success
criteria.

## License

Apache-2.0. See [LICENSE](LICENSE).

