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

## Get transactions bound to a user account

Request:

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Get transactions info" Terminal_Type="code" Global_Type="code">
<Transaction>
    <Account_Number>99.00005.00009400.0001</Account_Number>
    <Date_From>2021-05-16</Date_From>
    <Date_To>2021-05-18</Date_To>
    <Index>1</Index>
    <Count>10</Count>
    <Include>Transaction_DopInfo, Transaction_Life, Transaction_Bonuses</Include>
</Transaction>
</Message>
```

Response:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Transactions Message_ID="0" IndexFrom="1" IndexTo="2" Count="2">
    <Transaction>
        <Division_ID>1</Division_ID>
        <Transaction_ID>10000000029501</Transaction_ID>
        <Transaction_Time>2021-05-17 22:32:08.79 +02:00</Transaction_Time>
        <Transaction_Bonuses>0.00</Transaction_Bonuses>
        <Summ>-50.00</Summ>
        <Transaction_Type>51</Transaction_Type>
        <Operation_Type>2</Operation_Type>
        <Operation_Type_Name>Списание</Operation_Type_Name>
        <Account_Number>99.00005.00009400.0001</Account_Number>
        <Holder_ID>10000000001621</Holder_ID>
        <Client_ID>7</Client_ID>
        <Client_Type>code</Client_Type>
        <Client_Name>code</Client_Name>
        <External_ID>1234526</External_ID>
        <External_Index>422026</External_Index>
        <External_Date>2021-05-17T00:00:00</External_Date>
        <Remarks>Add points</Remarks>
    </Transaction>
    <Transaction>
        <Division_ID>1</Division_ID>
        <Transaction_ID>10000000029500</Transaction_ID>
        <Transaction_Time>2021-05-17 22:30:08.79 +02:00</Transaction_Time>
        <Transaction_Bonuses>0.00</Transaction_Bonuses>
        <Summ>100.50</Summ>
        <Transaction_Type>52</Transaction_Type>
        <Operation_Type>2</Operation_Type>
        <Operation_Type_Name>Начисление</Operation_Type_Name>
        <Account_Number>99.00005.00009400.0001</Account_Number>
        <Holder_ID>10000000001621</Holder_ID>
        <Client_ID>7</Client_ID>
        <Client_Type>code</Client_Type>
        <Client_Name>code</Client_Name>
        <External_ID>123456</External_ID>
        <External_Index>42206</External_Index>
        <External_Date>2021-05-17T00:00:00</External_Date>
        <Remarks>Add points</Remarks>
    </Transaction>
</Transactions>
```


Notes:

- If an empty Client_ID parameter is passed, the server will automatically substitute the software classifier identifier, determined by Terminal_Type. The Unit_ID parameter will also be processed. That is, in such cases, only "own" transactions will be issued.
- If an empty Transaction_Parent parameter is passed, the server will select unparent transactions.
- When specifying the Transaction_Life parameter and setting the Transaction_Life_From or Transaction_Life_To values, the output list of transactions is generated in the "burning bonuses" mode. That is, the list includes only bonuses with a lifespan in ascending order. In this case, the Account_Number parameter is required. In the case when several transactions have accrued bonuses with the same lifetime, the transactions are combined (a list of identifiers will be presented in Transaction_ID) and only Summ, Summ_Spend and Transaction_Life remain.
- If the Transaction_Bonuses parameter is specified, information about the bonuses accrued for the transaction will be added to the response.
- Account_Number, Card_Code, Transaction_ID, Holder_ID, External_ID - one of the listed parameters must be filled in without fail.

## Add new transaction

WIP...
