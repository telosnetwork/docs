# Edit a Profile

## Update a Display Name

To update a profile's display name call the `editdisplay()` action.

#### Action Parameters

| Field              | Type   | Example  | Description                        |
| ------------------ | ------ | -------- | ---------------------------------- |
| account            | name   | craig.tf | Account name of profile to update. |
| new\_display\_name | string | Craig2   | New display name.                  |

## Update an Avatar

To update a profile's avatar call the `editavatar()` action.

#### Action Parameters

| Field       | Type   | Example              | Description                        |
| ----------- | ------ | -------------------- | ---------------------------------- |
| account     | name   | craig.tf             | Account name of profile to update. |
| new\_avatar | string | imgur.com/image2.png | New avatar image link.             |

## Update a Bio

To update a profile's bio call the `editbio()` action.

#### Action Parameters

| Field    | Type   | Example      | Description                        |
| -------- | ------ | ------------ | ---------------------------------- |
| account  | name   | craig.tf     | Account name of profile to update. |
| new\_bio | string | New Bio Text | New bio text.                      |

## Update a Profile Status

To update a profile's status call the **editstatus()** action.

#### Action Parameters

| Field       | Type   | Example  | Description                        |
| ----------- | ------ | -------- | ---------------------------------- |
| account     | name   | craig.tf | Account name of profile to update. |
| new\_status | string | Busy     | New profile status.                |
