# bonsai/oem

Production provider registry and real-world manufacturing test benchmark.

## Boundary

- `bonsai/costume-generation` defines **what to make**.
- `bonsai/oem` defines **where, how, for how much, and how testable it is to make**.
- `bonsai/textile` defines normalized textile production data and intermediate representations.

The OEM layer is intentionally provider-oriented. A provider may be a factory, embroidery shop, print-on-demand network, contract manufacturer, or manual production service.

## Core ontology

`Product + Process + Customization + Provider + Constraint + Cost + Integration + Fulfillment + Evidence`

A product and a process are separate concepts. For example:

```yaml
product:
  category: socks
manufacturing:
  process:
    - embroidery
design:
  placement:
    type: one_point
```

Do not create `one_point_socks` as a product class.

## Provider lifecycle

```text
candidate
  -> price_checked
  -> shipping_checked
  -> budget_pass / budget_fail
  -> ordered
  -> received
  -> evaluated
```

A price is not considered a real-world result until shipping and tax are verified. Evidence should be recorded separately from assumptions.

## MVP benchmark

The first benchmark is:

**10,000 JPY, shipping included, tax included, one real production test.**

The benchmark is not a claim that every provider fits the budget. Unknown totals remain `candidate` until checkout or an equivalent quotation verifies them.

Initial test families:

- one-point embroidered socks
- custom embroidered socks
- full-color POD socks
- personalized/name towels
- original tenugui

## Repository structure

```text
ontology/
  production-provider.yaml
providers/
  index.yaml
tests/
  budget-10000.yaml
```

## Evidence-first rule

Each provider record should distinguish:

- documented capability
- documented MOQ
- documented integration
- listed/base price
- verified shipping
- verified tax
- verified total
- actual order result

This makes OEM data usable by agents without pretending that an advertised base price is a completed production experiment.
