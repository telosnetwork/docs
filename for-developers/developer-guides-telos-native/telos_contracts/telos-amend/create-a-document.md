# Create a Document

## Create a new Document

Documents are broken down into named sections which hold the contents of the document. Sections can be raw text, IPFS links, API links, or any combination thereof. A document can be roughly visualized with the layout below:

#### Document Title

Document Subtitle

| section\_name | content |
| :--- | :--- |
| sectiona | Text here |
| sectionb | More text here |
| sectionc | A little more text |

To begin, the document author must call the `newdocument` action on the `amend.decide` contract.

### ACTION `newdocument`

#### Fee: 50.000 TLOS

| Parameter Name | Type | Example | Description |
| :--- | :--- | :--- | :--- |
| title | string | "Doc1" | The title of the document |
| subtitle | string | "A small example document" | The subtitle of the document |
| document\_name | name | doc1 | The name identifier for the document |
| author | name | testaccount1 | The telos account of the author |
| initial\_sections | map&lt;name, string&gt; | { sectiona : "Text here", sectionb: "More text here", sectionc: "A little more text" } ... | The document broken down into a mapping of section names to section content.  |

{% tabs %}
{% tab title="Cleos" %}
```text
cleos push action amend.decide newdocument '{ ... }' -p author
```
{% endtab %}

{% tab title="eosjs" %}
```
(async () => {
  const result = await api.transact({
    actions: [{
      account: 'amend.decide',
      name: 'newdocument',
      authorization: [{
        actor: '...',
        permission: 'active',
      }],
      data: {
        title: 'Doc1',
        subtitle: 'A small example document',
        document_name: 'doc1',
        author: 'testaccount1',
        initial_sections: [
          {
            "key": "sectiona",
            "value": "Text here"
          },
          {
            "key": "sectionb",
            "value": "More text here"
          },
          {
            "key": "sectionc",
            "value": "A little more text"
          }
        ]
      },
    }]
  }, {
    blocksBehind: 3,
    expireSeconds: 30,
  });
  console.dir(result);
})();
```
{% endtab %}
{% endtabs %}

## Editing Title and Subtitle

At any time, the author may alter the document title or the subtitle. To do so, the author must call the `editheader` action on the `amend.decide` contract. To leave a title or subtitle the same, simply copy the existing text into the appropriate parameter.

### ACTION `editheader`

| Parameter Name | Type | Example | Description |
| :--- | :--- | :--- | :--- |
| document\_name | name | doc1 | The name of the document header to edit. |
| new\_title | string | "New Title" | The new document title. |
| new\_subtitle | string | "New Subtitle" | The new document subtitle. |

{% tabs %}
{% tab title="Cleos" %}
```text
cleos push action amend.decide editheader '{ ... }' -p author
```
{% endtab %}

{% tab title="eosjs" %}
```
(async () => {
  const result = await api.transact({
    actions: [{
      account: 'amend.decide',
      name: 'editheader',
      authorization: [{
        actor: '...',
        permission: 'active',
      }],
      data: {
        document_name: 'doc1',
        new_title: 'New Title',
        new_subtitle: 'New Subtitle'
      },
    }]
  }, {
    blocksBehind: 3,
    expireSeconds: 30,
  });
  console.dir(result);
})();
```
{% endtab %}
{% endtabs %}

## Changing Authors

A document author may relinquish authorship to another account with the `updateauthor` action. 

### ACTION `updateauthor`

| Parameter Name | Type | Example | Description |
| :--- | :--- | :--- | :--- |
| document\_name | name | doc1 | The name of the document to change the author for. |
| new\_author | name | newauthor1 | The name of the Telos account of the new author. |

{% tabs %}
{% tab title="Cleos" %}
```text
cleos push action amend.decide updateauthor '{ ... }' -p author
```
{% endtab %}

{% tab title="eosjs" %}
```
(async () => {
  const result = await api.transact({
    actions: [{
      account: 'amend.decide',
      name: 'updateauthor',
      authorization: [{
        actor: '...',
        permission: 'active',
      }],
      data: {
        document_name: 'doc1',
        new_author: 'newauthor1'
      },
    }]
  }, {
    blocksBehind: 3,
    expireSeconds: 30,
  });
  console.dir(result);
})();
```
{% endtab %}
{% endtabs %}

## 

