# Propose an Amendment

## Draft a Proposal

To draft a proposal call the `draftprop` action.

### ACTION `draftprop`

| Parameter Name | Type | Example | Description |
| :--- | :--- | :--- | :--- |
| title | string | "Proposal A" | The title of the proposal. |
| subtitle | string | "A proposal to update doc1" | The subtitle of the proposal. |
| ballot\_name | name | propaballot | The Telos Decide ballot name for the proposal. |
| proposer | name | testaccount1 | The Telos account of the proposer. |
| document\_name | name | doc1 | The document affected by the proposal. |
| new\_content | map&lt;name, string&gt; | { sectionc: "New Section C Text", sectiond: "New Section" } | The new content for the document broken down by section name and the content to write to the section. |

```text
cleos push action amend.decide draftprop '{ ... }' -p proposer
```

## Launch a Proposal

Once a proposal draft is complete, the proposer must launch the proposal. This will lock the proposal details in and deploy a ballot for the amendment on Telos Decide.

### ACTION `launchprop`

| Parameter Name | Type | Example | Description |
| :--- | :--- | :--- | :--- |
| ballot\_name | name | propaballot | The Telos Decide ballot name. |

{% tabs %}
{% tab title="Cleos" %}
```text
cleos push action amend.decide launchprop '{ ... }' -p proposer
```
{% endtab %}

{% tab title="eosjs" %}
```

```
{% endtab %}
{% endtabs %}

## End a Proposal

Once voting has concluded on the amendment, the proposer must end the proposal with the `endprop` action.

### ACTION `endprop`

| Parameter Name | Type | Example | Description |
| :--- | :--- | :--- | :--- |
| ballot\_name | name | propaballot | The Telos Decide ballot name. |

{% tabs %}
{% tab title="Cleos" %}
```text
cleos push action amend.decide endprop '{ ... }' -p proposer
```
{% endtab %}

{% tab title="eosjs" %}
```

```
{% endtab %}
{% endtabs %}

## Amend a Successful Proposal

If a proposal was approved after calling the `endprop` action, the actual document text can be updated with the `amendprop` action. This will loop over the approved content from the proposal and apply it to the appropriate document sections.

### ACTION `amendprop`

| Parameter Name | Type | Example | Description |
| :--- | :--- | :--- | :--- |
| ballot\_name | name | propaballot | The Telos Decide ballot name |
| amender | name | testaccounta | The account amending the document. |

{% tabs %}
{% tab title="Cleos" %}
```text
cleos push action amend.decide amendprop '{ ... }' -p amender
```
{% endtab %}

{% tab title="eosjs" %}
```

```
{% endtab %}
{% endtabs %}

## Cancel or Delete a Proposal

To cancel a proposal that is currently open for voting, call the `cancelprop` action.

### ACTION `cancelprop`

| Parameter Name | Type | Example | Description |
| :--- | :--- | :--- | :--- |
| ballot\_name | name | propaballot | The Telos Decide ballot name |
| memo | string | "memo here" | An optional memo describing the cancellation. |

```text
cleos push action amend.decide cancelprop '{ ... }' -p proposer
```

To fully delete a cancelled proposal or a proposal draft, call the `deleteprop` action.

### ACTION `deleteprop`

| Parameter Name | Type | Example | Description |
| :--- | :--- | :--- | :--- |
| ballot\_name | name | propaballot | The Telos Decide ballot name |

```text
cleos push action amend.decide deleteprop '{ ... }' -p proposer
```

