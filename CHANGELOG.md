# Changelog

All notable changes to the packages in this repository are documented here.

Add your entry under `## Unreleased` in the same pull request that makes the
change. See [CONTRIBUTING.md](CONTRIBUTING.md#changelog) for details.

## Unreleased

### Templates

- `docs/markdown`: Generates Markdown documentation for a semantic convention
  registry - namespace-first pages for attributes, spans, metrics, events, and
  entities, plus embeddable snippet tables and configurable cross-registry
  links.
- `docs/markdown`: Add the `markdown.omit_enum_table` annotation to skip the
  enum values table where a signal pins the attribute to one value.
- `docs/markdown`: Add `entity-refinements.md` and `metric-refinements.md` pages
  for namespaces that define entity or metric refinements, listed in the
  namespace `README.md`. Each refinement links to the signal it refines and
  shows the attributes it adds or changes; refined entities and metrics list
  their **Known refinements**.
- `docs/markdown`: Fix table-of-contents anchor links for multi-word section
  headings (`Entity refinements`, `Metric refinements`) — spaces are now
  replaced with hyphens so `#entity-refinements` resolves correctly in GitHub
  Markdown.
- `diagnostic_templates/gh_workflow_command`: New diagnostic template that emits
  Weaver policy violations as `::error` GitHub Actions workflow commands and
  other diagnostics as an expandable `::group` block. Filters
  `UnstableFileFormat` advisories so CI output stays actionable.

### Policies

- `check/backwards-compatibility`: Checks a registry against a baseline registry
  for breaking changes.
- `check/naming_conventions`: Enforces OpenTelemetry semantic convention naming
  rules.
- `check/stability`: Enforces stability rules for attribute definition and
  usage.
- `check/entity_associations`: Checks that entity associations in a registry are
  well formed. Skips the current materialized form, whose referential integrity
  weaver already validates during resolution, and stays a back-compatible check
  for the old bare-string form.
