---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "redshift_database Resource - terraform-provider-redshift"
subcategory: ""
description: |-
  Defines a local database.
---

# redshift_database (Resource)

Defines a local database.

## Example Usage

```terraform
# Example resource declaration of a local database
resource "redshift_database" "db" {
  name = "my_database"
  owner = "my_user"
  connection_limit = 123456 # use -1 for unlimited

  lifecycle {
    prevent_destroy = true
  }
}


# Example resource declaration of a database
# created from a datashare of another redshift cluster
resource "redshift_database" "datashare_db" {
  name = "my_datashare_consumer_db"
  owner = "my_user"
  connection_limit = 123456 # use -1 for unlimited

  datashare_source {
    share_name = "my_datashare"
    account_id = "123456789012" # 12 digit AWS account number of the producer cluster (optional, default is current account)
    namespace = "00000000-0000-0000-0000-000000000000" # producer cluster namespace (uuid)
  }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) Name of the database

### Optional

- `connection_limit` (Number) The maximum number of concurrent connections that can be made to this database. A value of -1 means no limit.
- `datashare_source` (Block List, Max: 1) Configuration for creating a database from a redshift datashare. (see [below for nested schema](#nestedblock--datashare_source))
- `owner` (String) Owner of the database, usually the user who created it

### Read-Only

- `id` (String) The ID of this resource.

<a id="nestedblock--datashare_source"></a>
### Nested Schema for `datashare_source`

Required:

- `namespace` (String) The namespace (guid) of the producer cluster
- `share_name` (String) The name of the datashare on the producer cluster

Optional:

- `account_id` (String) The AWS account ID of the producer cluster.
- `with_permissions` (Boolean) Whether the database requires object-level permissions to access individual database objects
