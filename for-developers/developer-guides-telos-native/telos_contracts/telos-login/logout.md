# Logout

## Logout a User

To log a user out, call the `logoutuser` action on the `telos.login` contract.

### ACTION `logoutuser`

| Parameter Name | Type | Example | Description |
| :--- | :--- | :--- | :--- |
| account\_name | name | testaccount1 | Name of the Telos account to log out. |

{% tabs %}
{% tab title="Cleos" %}
```text
cleos push action telos.login logoutuser '{ ... }' -p user
```
{% endtab %}

{% tab title="eosjs" %}
```

```
{% endtab %}
{% endtabs %}



