# Manage Metadata

## Profile Metadata

Apps can use the profile metadata feature to write custom metadata text (JSON, HTML, YAML, etc) on a profile for use in their application.

## Write Metadata to a Profile

To write new metadata to a profile call the `writemeta()` action. The writer is responsible for paying RAM costs to store the metadata.

#### Action Parameters

| Field   | Type   | Example      | Description                           |
| ------- | ------ | ------------ | ------------------------------------- |
| writer  | name   | craig.tf     | Account name writing data to profile. |
| account | name   | testaccounta | Account name of profile for metadata. |
| data    | string | {"id": 5}    | Metadata to store.                    |

## Delete Metadata from Profile

To delete metadata from a profile call the `delmeta()` action. This action will return the RAM costs back to the writer.

#### Action Parameters

| Field   | Type | Example      | Description                              |
| ------- | ---- | ------------ | ---------------------------------------- |
| writer  | name | craig.tf     | Name of account that wrote the metadata. |
| account | name | testaccounta | Name of account assigned the metadata.   |
