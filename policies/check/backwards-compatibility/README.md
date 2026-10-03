# Backwards Compatibility Policies

This package provides backwards compatibility guarantees required by OpenTelemetry projects.

Stability: Development
Owners: @open-telemetry/specs-semconv-maintainers

## Details

This package checks the current registry against a baseline registry and reports
breaking changes to attributes, metrics, entities, events, spans, and public
attribute groups.

## Usage

```bash
$ weaver registry check \
    -p https://github.com/open-telemetry/opentelemetry-weaver-packages.git[policies/check/backwards-compatibility] \
    -r {your repository} \
    --baseline-registry {your_baseline_version}
```

## Exceptions

When a signal becomes a refinement, put the removal exception on its replacement:

```yaml
span_refinements:
  - id: span.aws.lambda.server
    ref: faas.server
    annotations:
      compatibility:
        policy_exceptions:
          - span_removed
```

Use the finding ID without the `compatibility_` prefix:

| Signal | Exception |
| --- | --- |
| Span | `span_removed` |
| Metric | `metric_removed` |
| Event | `event_removed` |
| Entity | `entity_removed` |

The refinement must have the same signal kind and match the former name or type.
Its ID may include the kind prefix, such as `span.` or `metric.`.
The example suppresses removal of `aws.lambda.server` only.

Other compatibility checks still run. Baseline annotations do not suppress findings.
