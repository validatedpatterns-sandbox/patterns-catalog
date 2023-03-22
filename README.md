# Patterns Catalog

The catalog in this repository contains the information on the latest patterns, 
both validated and community, that are maintained in the hybrid-cloud-patterns
repo.

There are two possible uses for this catalog:

* Backstage
* Validated Patterns operator

The [Patterns Operator] is adding a Patterns Catalog feature. This feature
provides a custom OpenShift console plugin that allows users to view and
deploy available patterns from a catalog.

The catalog is populated from one or more YAML files called *Pattern Catalog
Definitions*. A Pattern Catalog Definition file contains metadata about the
organization providing the patterns and metadata about the patterns themselves.

This repository contains the default Pattern Catalog Definition file for the
[Hybrid Cloud Patterns] project. It is automatically imported when the Patterns
Operator is installed.

If your organization wants to create their own Pattern Catalog Definition, you
should:

* Fork this repo
* Update catalog.yaml
* Create a [PatternCatalogSource] on your cluster pointed to your forked
  catalog.yaml
* After a few moments the patterns from your catalog.yaml file should appear in
  the Pattern Catalog.

If you are using your own Pattern Catalog Definition, it's possible to delete
the default PatternCatalogSource:

```bash
oc delete patterncatalogsource default -n patterns-operator
```

## Example Catalog YAML

Example containing a single pattern.

```yaml
version: alpha
organization:
  name: Hybrid Cloud Patterns
  description: >
    Open source repository of cloud native solution patterns. This repository
    is maintained by Red Hat with contributions from customers and partners.
  maintainers:
    - name: Validated Patterns Team
      email: team-validated-patterns@redhat.com
  url: https://github.com/hybrid-cloud-patterns
patterns:
  - name: Multi-cloud GitOps
    description: A simple architecture for managing multiple clusters using GitOps
    longDescription: >
      This pattern demonstrates a simple architecture for managing multiple
      clusters using GitOps. It can be used as a good starting point for
      experimenting with other products in a multi-cluster architecture.
    branch: main
    gitRepo: https://github.com/hybrid-cloud-patterns/multicloud-gitops.git
    maintainers:
      - name: Validated Patterns Team
        email: team-validated-patterns@redhat.com
    products:
      - Red Hat Advanced Cluster Management
      - Red Hat OpenShift GitOps
      - Hashicorp Vault
    type: Validated
    url: https://hybrid-cloud-patterns.io/patterns/multicloud-gitops/
```

## Pattern Catalog Definition Specification (Alpha Version)

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
| maintainers | List of maintainers for the organization. **NOTE:** This could be different than the maintainers of individual patterns.
| url | URL to the organization's page for more information |

#### Maintainers

Organization should contain a list of one or more maintainers. Each maintainer should contain

| Field | Description |
| ----- | ----------- |
| name  | Name of the maintainer |
| email | Email address of the maintainer |

### Patterns

The top-level `patterns` field should contain a list of one or more patterns. Each pattern should contain

| Field | Description |
| ----- | ----------- |
| name | Name of the pattern |
| description | One sentence description of the pattern. If this is too long, it will be truncated in the Patterns Catalog UI. |
| longDescription | Longer multi-line description. Can contain Markdown. |
| branch | Default branch of the Git repo to use when deploying the pattern |
| gitRepo | URL to the Git repo for the pattern. This should be an HTTPS URL ending with ".git". |
| maintainers | List of maintainers for the pattern |
| products | A list of products used by the pattern. Each product should be a string with the proper name of the product (No abbreviations). |
| type | Pattern type. Hybrid Cloud Patterns uses the types "Community" and "Validated". Type will be displayed as a badge on the pattern. |
| url | URL to pattern documentation |

#### Maintainers

Each pattern should contain a list of one or more maintainers. Each maintainer should contain

| Field | Description |
| ----- | ----------- |
| name  | Name of the maintainer |
| email | Email address of the maintainer |

[Hybrid Cloud Patterns]: https://hybrid-cloud-patterns.io/
[PatternCatalogSource]: https://github.com/RyanMillerC/patterns-catalog/blob/main/default-patterncatalogsource.yaml
[Patterns Operator]: https://github.com/RyanMillerC/patterns-operator
