# Accounts

The UCS company can create the account types for you. 
When a a new holder is created they are created by adding an account to them from each type.
Accounts can be used to handle loyality points, internal pay balance and others.

## Get the state of the accounts of a Holder

Request:

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Get holder info" Terminal_Type="<code>" Global_Type="<code>">
    <Holder_ID>10000000001621</Holder_ID>
    <Include>Account</Include>
</Message>
```

<details>
	<summary>Response:</summary>

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Holder Message_ID="0">
    <Deleted>No</Deleted>
    <Group_ID>8</Group_ID>
    <Group_Name>WEB</Group_Name>
    <Division_ID>1</Division_ID>
    <Division_Name>Head subdivision</Division_Name>
    <Holder_ID>10000000001621</Holder_ID>
    <INN></INN>
    <External_Code></External_Code>
    <Unpay_Type_ID></Unpay_Type_ID>
    <Unpay_Type_Name></Unpay_Type_Name>
    <L_Name>Testike10</L_Name>
    <F_Name>Testike12</F_Name>
    <M_Name></M_Name>
    <Full_Name>Testike10 Testike12</Full_Name>
    <Birth>1899-12-30</Birth>
    <Gender>Unknown</Gender>
    <Marrital>Unknown</Marrital>
    <Smoke>No</Smoke>
    <Verification>Yes</Verification>
    <Image>No</Image>
    <Language_ID>1038</Language_ID>
    <Language_Name>
        <![CDATA[[HUN] Hungarian (Hungary)]]>
    </Language_Name>
    <Source></Source>
    <Remarks></Remarks>
    <Accounts>
        <Account>
            <Holder_ID>10000000001621</Holder_ID>
            <Account_Number>99.00005.00009400.0001</Account_Number>
            <Status>Active</Status>
            <Account_Class>99</Account_Class>
            <Account_Type_ID>5</Account_Type_ID>
            <Account_Type_Name>Counter</Account_Type_Name>
            <Account_Debit_Enabled>Yes</Account_Debit_Enabled>
            <Account_Debit_Priority></Account_Debit_Priority>
            <Account_Debit_K>1</Account_Debit_K>
            <Account_Credit_Enabled>Yes</Account_Credit_Enabled>
            <Account_Credit_Priority></Account_Credit_Priority>
            <Account_Credit_K>1</Account_Credit_K>
            <Transaction_Debit_ID>51</Transaction_Debit_ID>
            <Transaction_Credit_ID>52</Transaction_Credit_ID>
            <Create>2021-05-16</Create>
            <Expired>2040-02-01</Expired>
            <Credit_Depth>0.00</Credit_Depth>
            <Balance>100.50</Balance>
            <Account_Level_ID></Account_Level_ID>
            <Account_Level_Name></Account_Level_Name>
            <Scheme_ID></Scheme_ID>
            <External_ID></External_ID>
            <Scheme_Name></Scheme_Name>
            <Base_Rate>0.00</Base_Rate>
            <Auto_Change_Levels>No</Auto_Change_Levels>
            <Account_Code>0</Account_Code>
            <Account_Code_Ext>0</Account_Code_Ext>
        </Account>
        <Account>
            <Holder_ID>10000000001621</Holder_ID>
            <Account_Number>02.00008.00009401.0001</Account_Number>
            <Status>Active</Status>
            <Account_Class>2</Account_Class>
            <Account_Type_ID>8</Account_Type_ID>
            <Account_Type_Name>Dolgozói kedvezmény</Account_Type_Name>
            <Account_Debit_Enabled>Yes</Account_Debit_Enabled>
            <Account_Debit_Priority></Account_Debit_Priority>
            <Account_Debit_K>1</Account_Debit_K>
            <Account_Credit_Enabled>Yes</Account_Credit_Enabled>
            <Account_Credit_Priority></Account_Credit_Priority>
            <Account_Credit_K>1</Account_Credit_K>
            <Transaction_Debit_ID>81</Transaction_Debit_ID>
            <Transaction_Credit_ID>82</Transaction_Credit_ID>
            <Create>2021-05-16</Create>
            <Expired>2040-03-01</Expired>
            <Credit_Depth>0.00</Credit_Depth>
            <Balance>0.00</Balance>
            <Account_Level_ID>3</Account_Level_ID>
            <Account_Level_Name>Level1</Account_Level_Name>
            <Scheme_ID>6</Scheme_ID>
            <External_ID>51</External_ID>
            <Scheme_Name>
                <![CDATA[20% Doldozói kedvezmény séma]]>
            </Scheme_Name>
            <Base_Rate>20.00</Base_Rate>
            <Auto_Change_Levels>Yes</Auto_Change_Levels>
            <Account_Code>6</Account_Code>
            <Account_Code_Ext>51</Account_Code_Ext>
        </Account>
        <Account>
            <Holder_ID>10000000001621</Holder_ID>
            <Account_Number>99.00007.00009402.0001</Account_Number>
            <Status>Active</Status>
            <Account_Class>99</Account_Class>
            <Account_Type_ID>7</Account_Type_ID>
            <Account_Type_Name>Expenses check account</Account_Type_Name>
            <Account_Debit_Enabled>Yes</Account_Debit_Enabled>
            <Account_Debit_Priority></Account_Debit_Priority>
            <Account_Debit_K>1</Account_Debit_K>
            <Account_Credit_Enabled>Yes</Account_Credit_Enabled>
            <Account_Credit_Priority></Account_Credit_Priority>
            <Account_Credit_K>1</Account_Credit_K>
            <Transaction_Debit_ID>71</Transaction_Debit_ID>
            <Transaction_Credit_ID>72</Transaction_Credit_ID>
            <Create>2021-05-16</Create>
            <Expired>2040-03-01</Expired>
            <Credit_Depth>0.00</Credit_Depth>
            <Balance>0.00</Balance>
            <Account_Level_ID></Account_Level_ID>
            <Account_Level_Name></Account_Level_Name>
            <Scheme_ID></Scheme_ID>
            <External_ID></External_ID>
            <Scheme_Name></Scheme_Name>
            <Base_Rate>0.00</Base_Rate>
            <Auto_Change_Levels>No</Auto_Change_Levels>
            <Account_Code>0</Account_Code>
            <Account_Code_Ext>0</Account_Code_Ext>
        </Account>
        <Account>
            <Holder_ID>10000000001621</Holder_ID>
            <Account_Number>02.00003.00009403.0001</Account_Number>
            <Status>Active</Status>
            <Account_Class>2</Account_Class>
            <Account_Type_ID>3</Account_Type_ID>
            <Account_Type_Name>Kedvezmények összege</Account_Type_Name>
            <Account_Debit_Enabled>Yes</Account_Debit_Enabled>
            <Account_Debit_Priority></Account_Debit_Priority>
            <Account_Debit_K>1</Account_Debit_K>
            <Account_Credit_Enabled>Yes</Account_Credit_Enabled>
            <Account_Credit_Priority></Account_Credit_Priority>
            <Account_Credit_K>1</Account_Credit_K>
            <Transaction_Debit_ID>31</Transaction_Debit_ID>
            <Transaction_Credit_ID>32</Transaction_Credit_ID>
            <Create>2021-05-16</Create>
            <Expired>2040-02-01</Expired>
            <Credit_Depth>0.00</Credit_Depth>
            <Balance>0.00</Balance>
            <Account_Level_ID>2</Account_Level_ID>
            <Account_Level_Name>Level1</Account_Level_Name>
            <Scheme_ID>2</Scheme_ID>
            <External_ID>36</External_ID>
            <Scheme_Name>VIP Kedvezmény séma</Scheme_Name>
            <Base_Rate>10.00</Base_Rate>
            <Auto_Change_Levels>Yes</Auto_Change_Levels>
            <Account_Code>2</Account_Code>
            <Account_Code_Ext>36</Account_Code_Ext>
        </Account>
        <Account>
            <Holder_ID>10000000001621</Holder_ID>
            <Account_Number>05.00001.00009404.0001</Account_Number>
            <Status>Active</Status>
            <Account_Class>5</Account_Class>
            <Account_Type_ID>1</Account_Type_ID>
            <Account_Type_Name>Vásárlások összege</Account_Type_Name>
            <Account_Debit_Enabled>Yes</Account_Debit_Enabled>
            <Account_Debit_Priority></Account_Debit_Priority>
            <Account_Debit_K>1</Account_Debit_K>
            <Account_Credit_Enabled>Yes</Account_Credit_Enabled>
            <Account_Credit_Priority></Account_Credit_Priority>
            <Account_Credit_K>1</Account_Credit_K>
            <Transaction_Debit_ID>11</Transaction_Debit_ID>
            <Transaction_Credit_ID>12</Transaction_Credit_ID>
            <Create>2021-05-16</Create>
            <Expired>2040-02-01</Expired>
            <Credit_Depth>0.00</Credit_Depth>
            <Balance>0.00</Balance>
        </Account>
        <Account>
            <Holder_ID>10000000001621</Holder_ID>
            <Account_Number>01.00002.00009405.0001</Account_Number>
            <Status>Active</Status>
            <Account_Class>1</Account_Class>
            <Account_Type_ID>2</Account_Type_ID>
            <Account_Type_Name>VIP megtakarítás</Account_Type_Name>
            <Account_Debit_Enabled>Yes</Account_Debit_Enabled>
            <Account_Debit_Priority></Account_Debit_Priority>
            <Account_Debit_K>1</Account_Debit_K>
            <Account_Credit_Enabled>Yes</Account_Credit_Enabled>
            <Account_Credit_Priority></Account_Credit_Priority>
            <Account_Credit_K>1</Account_Credit_K>
            <Transaction_Debit_ID>21</Transaction_Debit_ID>
            <Transaction_Credit_ID>22</Transaction_Credit_ID>
            <Create>2021-05-16</Create>
            <Expired>2040-02-01</Expired>
            <Credit_Depth>0.00</Credit_Depth>
            <Balance>0.00</Balance>
            <Account_Level_ID>1</Account_Level_ID>
            <Account_Level_Name>Level1</Account_Level_Name>
            <Scheme_ID>3</Scheme_ID>
            <External_ID>1</External_ID>
            <Scheme_Name>Bonusz séma</Scheme_Name>
            <Base_Rate>1.00</Base_Rate>
            <Auto_Change_Levels>Yes</Auto_Change_Levels>
            <Account_Code>3</Account_Code>
            <Account_Code_Ext>1</Account_Code_Ext>
        </Account>
    </Accounts>
</Holder>
```

</details>

## Add funds to a Holder's account
Further data about the [transactions](transactions.md)

Request:

```
<? xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Transaction" Terminal_Type="<code>" Global_Type="<code>">
<Transaction>
	<Account_Number>99.00005.00009400.0001</Account_Number>
	<External_ID>123456</External_ID>
	<External_Index>42206</External_Index>
	<External_Date>2021-05-17</External_Date>
	<Amount>100.50</Amount>
	<Transaction_Time>2021-05-17 22:30:08.79 +02:00</Transaction_Time>
	<Remarks>Add points</Remarks>
</Transaction>
</Message>
```

Response:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Transactions Message_ID="0">
    <Transaction>
        <Account_Number>99.00005.00009400.0001</Account_Number>
        <Transaction_ID>10000000029500</Transaction_ID>
    </Transaction>
</Transactions>
```

## Withdrawing funds from an account

Request:

```
<? xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Transaction" Terminal_Type="<code>" Global_Type="<code>">
<Transaction>
	<Account_Number>99.00005.00009400.0001</Account_Number>
	<External_ID>123456</External_ID>
	<External_Index>42206</External_Index>
	<External_Date>2021-05-17</External_Date>
	<Amount>-50.50</Amount>
	<Transaction_Time>2021-05-17 22:32:08.79 +02:00</Transaction_Time>
	<Remarks>Remove points</Remarks>
</Transaction>
</Message>
```

<details>
	<summary>Response:</summary>

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Holder Message_ID="0">
    <Deleted>No</Deleted>
    <Group_ID>8</Group_ID>
    <Group_Name>WEB</Group_Name>
    <Division_ID>1</Division_ID>
    <Division_Name>Head subdivision</Division_Name>
    <Holder_ID>10000000001621</Holder_ID>
    <INN></INN>
    <External_Code></External_Code>
    <Unpay_Type_ID></Unpay_Type_ID>
    <Unpay_Type_Name></Unpay_Type_Name>
    <L_Name>Testike10</L_Name>
    <F_Name>Testike12</F_Name>
    <M_Name></M_Name>
    <Full_Name>Testike10 Testike12</Full_Name>
    <Birth>1899-12-30</Birth>
    <Gender>Unknown</Gender>
    <Marrital>Unknown</Marrital>
    <Smoke>No</Smoke>
    <Verification>Yes</Verification>
    <Image>No</Image>
    <Language_ID>1038</Language_ID>
    <Language_Name>
        <![CDATA[[HUN] Hungarian (Hungary)]]>
    </Language_Name>
    <Source></Source>
    <Remarks></Remarks>
    <Accounts>
        <Account>
            <Holder_ID>10000000001621</Holder_ID>
            <Account_Number>99.00005.00009400.0001</Account_Number>
            <Status>Active</Status>
            <Account_Class>99</Account_Class>
            <Account_Type_ID>5</Account_Type_ID>
            <Account_Type_Name>Counter</Account_Type_Name>
            <Account_Debit_Enabled>Yes</Account_Debit_Enabled>
            <Account_Debit_Priority></Account_Debit_Priority>
            <Account_Debit_K>1</Account_Debit_K>
            <Account_Credit_Enabled>Yes</Account_Credit_Enabled>
            <Account_Credit_Priority></Account_Credit_Priority>
            <Account_Credit_K>1</Account_Credit_K>
            <Transaction_Debit_ID>51</Transaction_Debit_ID>
            <Transaction_Credit_ID>52</Transaction_Credit_ID>
            <Create>2021-05-16</Create>
            <Expired>2040-02-01</Expired>
            <Credit_Depth>0.00</Credit_Depth>
            <Balance>50.50</Balance>
            <Account_Level_ID></Account_Level_ID>
            <Account_Level_Name></Account_Level_Name>
            <Scheme_ID></Scheme_ID>
            <External_ID></External_ID>
            <Scheme_Name></Scheme_Name>
            <Base_Rate>0.00</Base_Rate>
            <Auto_Change_Levels>No</Auto_Change_Levels>
            <Account_Code>0</Account_Code>
            <Account_Code_Ext>0</Account_Code_Ext>
        </Account>
        <Account>
            <Holder_ID>10000000001621</Holder_ID>
            <Account_Number>02.00008.00009401.0001</Account_Number>
            <Status>Active</Status>
            <Account_Class>2</Account_Class>
            <Account_Type_ID>8</Account_Type_ID>
            <Account_Type_Name>Dolgozói kedvezmény</Account_Type_Name>
            <Account_Debit_Enabled>Yes</Account_Debit_Enabled>
            <Account_Debit_Priority></Account_Debit_Priority>
            <Account_Debit_K>1</Account_Debit_K>
            <Account_Credit_Enabled>Yes</Account_Credit_Enabled>
            <Account_Credit_Priority></Account_Credit_Priority>
            <Account_Credit_K>1</Account_Credit_K>
            <Transaction_Debit_ID>81</Transaction_Debit_ID>
            <Transaction_Credit_ID>82</Transaction_Credit_ID>
            <Create>2021-05-16</Create>
            <Expired>2040-03-01</Expired>
            <Credit_Depth>0.00</Credit_Depth>
            <Balance>0.00</Balance>
            <Account_Level_ID>3</Account_Level_ID>
            <Account_Level_Name>Level1</Account_Level_Name>
            <Scheme_ID>6</Scheme_ID>
            <External_ID>51</External_ID>
            <Scheme_Name>
                <![CDATA[20% Doldozói kedvezmény séma]]>
            </Scheme_Name>
            <Base_Rate>20.00</Base_Rate>
            <Auto_Change_Levels>Yes</Auto_Change_Levels>
            <Account_Code>6</Account_Code>
            <Account_Code_Ext>51</Account_Code_Ext>
        </Account>
        <Account>
            <Holder_ID>10000000001621</Holder_ID>
            <Account_Number>99.00007.00009402.0001</Account_Number>
            <Status>Active</Status>
            <Account_Class>99</Account_Class>
            <Account_Type_ID>7</Account_Type_ID>
            <Account_Type_Name>Expenses check account</Account_Type_Name>
            <Account_Debit_Enabled>Yes</Account_Debit_Enabled>
            <Account_Debit_Priority></Account_Debit_Priority>
            <Account_Debit_K>1</Account_Debit_K>
            <Account_Credit_Enabled>Yes</Account_Credit_Enabled>
            <Account_Credit_Priority></Account_Credit_Priority>
            <Account_Credit_K>1</Account_Credit_K>
            <Transaction_Debit_ID>71</Transaction_Debit_ID>
            <Transaction_Credit_ID>72</Transaction_Credit_ID>
            <Create>2021-05-16</Create>
            <Expired>2040-03-01</Expired>
            <Credit_Depth>0.00</Credit_Depth>
            <Balance>0.00</Balance>
            <Account_Level_ID></Account_Level_ID>
            <Account_Level_Name></Account_Level_Name>
            <Scheme_ID></Scheme_ID>
            <External_ID></External_ID>
            <Scheme_Name></Scheme_Name>
            <Base_Rate>0.00</Base_Rate>
            <Auto_Change_Levels>No</Auto_Change_Levels>
            <Account_Code>0</Account_Code>
            <Account_Code_Ext>0</Account_Code_Ext>
        </Account>
        <Account>
            <Holder_ID>10000000001621</Holder_ID>
            <Account_Number>02.00003.00009403.0001</Account_Number>
            <Status>Active</Status>
            <Account_Class>2</Account_Class>
            <Account_Type_ID>3</Account_Type_ID>
            <Account_Type_Name>Kedvezmények összege</Account_Type_Name>
            <Account_Debit_Enabled>Yes</Account_Debit_Enabled>
            <Account_Debit_Priority></Account_Debit_Priority>
            <Account_Debit_K>1</Account_Debit_K>
            <Account_Credit_Enabled>Yes</Account_Credit_Enabled>
            <Account_Credit_Priority></Account_Credit_Priority>
            <Account_Credit_K>1</Account_Credit_K>
            <Transaction_Debit_ID>31</Transaction_Debit_ID>
            <Transaction_Credit_ID>32</Transaction_Credit_ID>
            <Create>2021-05-16</Create>
            <Expired>2040-02-01</Expired>
            <Credit_Depth>0.00</Credit_Depth>
            <Balance>0.00</Balance>
            <Account_Level_ID>2</Account_Level_ID>
            <Account_Level_Name>Level1</Account_Level_Name>
            <Scheme_ID>2</Scheme_ID>
            <External_ID>36</External_ID>
            <Scheme_Name>VIP Kedvezmény séma</Scheme_Name>
            <Base_Rate>10.00</Base_Rate>
            <Auto_Change_Levels>Yes</Auto_Change_Levels>
            <Account_Code>2</Account_Code>
            <Account_Code_Ext>36</Account_Code_Ext>
        </Account>
        <Account>
            <Holder_ID>10000000001621</Holder_ID>
            <Account_Number>05.00001.00009404.0001</Account_Number>
            <Status>Active</Status>
            <Account_Class>5</Account_Class>
            <Account_Type_ID>1</Account_Type_ID>
            <Account_Type_Name>Vásárlások összege</Account_Type_Name>
            <Account_Debit_Enabled>Yes</Account_Debit_Enabled>
            <Account_Debit_Priority></Account_Debit_Priority>
            <Account_Debit_K>1</Account_Debit_K>
            <Account_Credit_Enabled>Yes</Account_Credit_Enabled>
            <Account_Credit_Priority></Account_Credit_Priority>
            <Account_Credit_K>1</Account_Credit_K>
            <Transaction_Debit_ID>11</Transaction_Debit_ID>
            <Transaction_Credit_ID>12</Transaction_Credit_ID>
            <Create>2021-05-16</Create>
            <Expired>2040-02-01</Expired>
            <Credit_Depth>0.00</Credit_Depth>
            <Balance>0.00</Balance>
        </Account>
        <Account>
            <Holder_ID>10000000001621</Holder_ID>
            <Account_Number>01.00002.00009405.0001</Account_Number>
            <Status>Active</Status>
            <Account_Class>1</Account_Class>
            <Account_Type_ID>2</Account_Type_ID>
            <Account_Type_Name>VIP megtakarítás</Account_Type_Name>
            <Account_Debit_Enabled>Yes</Account_Debit_Enabled>
            <Account_Debit_Priority></Account_Debit_Priority>
            <Account_Debit_K>1</Account_Debit_K>
            <Account_Credit_Enabled>Yes</Account_Credit_Enabled>
            <Account_Credit_Priority></Account_Credit_Priority>
            <Account_Credit_K>1</Account_Credit_K>
            <Transaction_Debit_ID>21</Transaction_Debit_ID>
            <Transaction_Credit_ID>22</Transaction_Credit_ID>
            <Create>2021-05-16</Create>
            <Expired>2040-02-01</Expired>
            <Credit_Depth>0.00</Credit_Depth>
            <Balance>0.00</Balance>
            <Account_Level_ID>1</Account_Level_ID>
            <Account_Level_Name>Level1</Account_Level_Name>
            <Scheme_ID>3</Scheme_ID>
            <External_ID>1</External_ID>
            <Scheme_Name>Bonusz séma</Scheme_Name>
            <Base_Rate>1.00</Base_Rate>
            <Auto_Change_Levels>Yes</Auto_Change_Levels>
            <Account_Code>3</Account_Code>
            <Account_Code_Ext>1</Account_Code_Ext>
        </Account>
    </Accounts>
</Holder>
```

</details>

## Get account types

Request:

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Get accounts types info" Terminal_Type="<code>" Global_Type="<code>"> </Message>
```

Response example:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Accounts_Types Message_ID="0">
    <Account_Type>
        <Status>Active</Status>
        <Account_Class>1</Account_Class>
        <Account_Type_ID>2</Account_Type_ID>
        <Account_Type_Name>VIP megtakarítás</Account_Type_Name>
        <Date_From>2019-02-22</Date_From>
        <Date_To>2040-02-01</Date_To>
        <Accounts_Levels>
            <Account_Level>
                <Account_Level_ID>1</Account_Level_ID>
                <Account_Level_Name>Level1</Account_Level_Name>
                <Account_Level_No>1</Account_Level_No>
                <Status>Active</Status>
            </Account_Level>
        </Accounts_Levels>
    </Account_Type>
    <Account_Type>
        <Status>Active</Status>
        <Account_Class>2</Account_Class>
        <Account_Type_ID>3</Account_Type_ID>
        <Account_Type_Name>Kedvezmények összege</Account_Type_Name>
        <Date_From>2019-02-22</Date_From>
        <Date_To>2040-02-01</Date_To>
        <Accounts_Levels>
            <Account_Level>
                <Account_Level_ID>2</Account_Level_ID>
                <Account_Level_Name>Level1</Account_Level_Name>
                <Account_Level_No>1</Account_Level_No>
                <Status>Active</Status>
            </Account_Level>
        </Accounts_Levels>
    </Account_Type>
    <Account_Type>
        <Status>Active</Status>
        <Account_Class>2</Account_Class>
        <Account_Type_ID>8</Account_Type_ID>
        <Account_Type_Name>Dolgozói kedvezmény</Account_Type_Name>
        <Date_From>2019-04-24</Date_From>
        <Date_To>2040-03-01</Date_To>
        <Accounts_Levels>
            <Account_Level>
                <Account_Level_ID>3</Account_Level_ID>
                <Account_Level_Name>Level1</Account_Level_Name>
                <Account_Level_No>1</Account_Level_No>
                <Status>Active</Status>
            </Account_Level>
        </Accounts_Levels>
    </Account_Type>
    <Account_Type>
        <Status>Active</Status>
        <Account_Class>3</Account_Class>
        <Account_Type_ID>9</Account_Type_ID>
        <Account_Type_Name>teszt</Account_Type_Name>
        <Date_From>2020-08-11</Date_From>
        <Date_To>2021-08-11</Date_To>
    </Account_Type>
    <Account_Type>
        <Status>Active</Status>
        <Account_Class>5</Account_Class>
        <Account_Type_ID>1</Account_Type_ID>
        <Account_Type_Name>Vásárlások összege</Account_Type_Name>
        <Date_From>2019-02-22</Date_From>
        <Date_To>2040-02-01</Date_To>
    </Account_Type>
    <Account_Type>
        <Status>Active</Status>
        <Account_Class>99</Account_Class>
        <Account_Type_ID>5</Account_Type_ID>
        <Account_Type_Name>Counter</Account_Type_Name>
        <Date_From>2019-02-22</Date_From>
        <Date_To>2040-02-01</Date_To>
    </Account_Type>
    <Account_Type>
        <Status>Active</Status>
        <Account_Class>99</Account_Class>
        <Account_Type_ID>7</Account_Type_ID>
        <Account_Type_Name>Expenses check account</Account_Type_Name>
        <Date_From>2019-03-01</Date_From>
        <Date_To>2040-03-01</Date_To>
    </Account_Type>
</Accounts_Types>
```