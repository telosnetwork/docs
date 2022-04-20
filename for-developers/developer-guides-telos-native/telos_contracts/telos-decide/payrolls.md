# Payrolls

## What is a Payroll?

A payroll is a treasury-specific funding mechanism that can stream funds into a claiming bucket at a customizable rate. Funds can be added to a payroll by anyone, and treasuries can have multiple payrolls running simultaneously. Claims from a payroll can be targeted to an individual recipient or a specific group of users.

All treasuries are granted the `worker` payroll by default, which can be used to pay workers for performing valuable platform optimization. Think of the worker payroll as a community fund to pay for treasury-wide housekeeping.

## Contributing to a Payroll

Any user can submit funds to any payroll. To do so, simply call the `addfunds()` action on the `telos.decide` contract.

### ACTION `addfunds`

| Parameter Name | Parameter Type | Example |
| :--- | :--- | :--- |
| from | name | craig.tcd |
| treasury\_symbol | symbol | 4,VOTE |
| quantity | asset | 100.0000 TLOS |

## Customizing Pay Rate

A treasury manager can adjust the pay rate and pay periods for any payroll within their treasury. Fine tuning these settings allows payrolls to predictably incentivize labor for the given purpose of the payroll.

### ACTION `editpayrate`

| Parameter Name | Parameter Type | Example |
| :--- | :--- | :--- |
| treasury\_symbol | symbol | 4,VOTE |
| period\_length | uint32\_t | 86400 |
| per\_period | asset | 50.0000 TLOS |

## Table Breakdown

Table: `payrolls`

Scope: `treasury_symbol`

| Field Name | Field Type | Description |
| :--- | :--- | :--- |
| payroll\_name | name |  |
| payroll\_funds | asset |  |
| period\_length | uint32\_t | Length of a pay period in seconds. |
| per\_period | asset | Funds released into claimable\_pay per period. |
| last\_claim\_time | time\_point\_sec | Last time funds were claimed. |
| claimable\_pay | asset | Funds currently claimable. |
| payee | name | Account name or Group eligible to claim funds. |

