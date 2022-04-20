# Delete a Document

## Deleting a Document

In order to delete a document, all sections must first be erased with the `delsection` action. Once a document has all sections deleted, the author can call the `deldocument` action to completely erase the document.

### ACTION `deldocument`

| Parameter Name | Type | Example | Description |
| :--- | :--- | :--- | :--- |
| document\_name | name | doc1 | The name of the document to delete. |
| memo | string | "example memo" | An optional memo describing the document deletion. |

```text
cleos push action amend.decide deldocument '{ ... }' -p author
```

