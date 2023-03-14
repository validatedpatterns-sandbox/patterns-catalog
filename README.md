# DRAFT Pattern Catalog YAML

This repository contains the Pattern Catalog for the [Hybrid Cloud Patterns](https://hybrid-cloud-patterns.io/) project.

## Catalog YAML Specification (Alpha Version)

### Top Level

| Field | Description |
| ----- | ----------- |
| version | Version of the Pattern Catalog specification used |
| organization | Metadata about the organization providing the patterns |
| patterns | List of patterns. Each list item contains metadata about a single pattern. |

### Organization

The top-level organization field should contain

| Field | Description |
| ----- | ----------- |
| name  | Name of the organization |
| description | Description of the organization |
| maintainers | Single email address of the maintainers of the organization. **NOTE:** This could be different than the maintainers of individual patterns.
| url | URL to the organization's page for more information |

### Patterns

The top-level `patterns` field should contain a list of one or more patterns. Each pattern should contain

| Field | Description |
| ----- | ----------- |
| name | Name of the pattern |
| description | One sentence description of the pattern. If this is too long, it will be truncated in the Patterns Catalog UI. |
| longDescription | Longer multi-line description. Can contain Markdown. |
| badge | Text to be displayed on the badge in the Catalog UI. Could be "Validated" or "Community". |
| branch | Default branch of the Git repo to use when deploying the pattern |
| gitRepo | URL to the Git repo for the pattern. This should be an HTTPS URL ending with ".git". |
| maintainers | Single email address of the maintainers of the pattern |
| products | A list of products used by the pattern |
| url | URL to pattern documentation |

#### Products

Each pattern should contain a list of one or more products. Each product should contain

| Field | Description |
| ----- | ----------- |
| name | Name of the product |
| version | Version of the product used. Use major/minor versions here. Do not include patch version. |
