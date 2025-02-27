---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "redshift_database Data Source - terraform-provider-redshift"
subcategory: ""
description: |-
  Fetches information about a Redshift database.
---

# redshift_database (Data Source)

Fetches information about a Redshift database.

## Example Usage

```terraform
data "redshift_database" "database" {
  name = "my_database"
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) Name of the database

### Optional

- `datashare_source` (Block List, Max: 1) Configuration for a database created from a redshift datashare. (see [below for nested schema](#nestedblock--datashare_source))

### Read-Only

- `connection_limit` (Number) The maximum number of concurrent connections that can be made to this database. A value of -1 means no limit.
- `id` (String) The ID of this resource.
- `owner` (String) Owner of the database, usually the user who created it

<a id="nestedblock--datashare_source"></a>
### Nested Schema for `datashare_source`

Optional:

- `account_id` (String) The AWS account ID of the producer cluster.
- `namespace` (String) The namespace (guid) of the producer cluster
- `share_name` (String) The name of the datashare on the producer cluster
