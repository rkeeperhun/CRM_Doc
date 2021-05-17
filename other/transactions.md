# Transactions

| Name | type | info |
| --- | --- | --- |
| Remarks | String [255] | |
| Dop_Info | Blob | |
| Transaction_Time | time | (required with time zone : 1999-12-12 12: 30: 30.12 +03: 00 ) conducting a transaction (transactions of different execution times at the checkout can be found in a transaction batch) |
| Transaction_Life | time | lifetime (date inclusive) of accrued bonuses, only for bonus accounts (optional) |
| Transaction_Delay | date and time | when bonuses were recorded on the account balance, only for bonus accounts (not required field) |
| External_ID | string | external identifier of the operation, for example, check number |
| External_Index | string | additional external identifier |
| External_Date | date | external date of the operation, for example, the date of the work shift |

Below are 3 parameters by which you can fully identify an external operation. Filling in the parameter is mandatory when conducting transactions, in the case of using return operations in the system. That is, the combination of these parameters must uniquely identify the returned operation (in this case, External_ID is required).

## Add new transaction

WIP...
