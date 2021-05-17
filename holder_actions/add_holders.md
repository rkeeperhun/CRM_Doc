# Add holders

This action creates a new holder in the CRM.

**Action**: `Add holders`

**Example:**

The following example is the bare minimum which is needed to create a new holder in the system.
The right `Group_ID` is provided by the UCS company.

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Add holders" Terminal_Type="<code>" Global_Type="<code>">
    <Holder>
        <Group_ID>8</Group_ID>
        <F_Name>Testike5</F_Name>
        <L_Name>Testike7</L_Name>
    </Holder>
</Message>
```

<details>
	<summary>Extended Add Holders example</summary>

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Add holders" Terminal_Type="<code>" Global_Type="<code>">
    <Holder>
        <Group_ID>8</Group_ID>
        <F_Name>Testike5</F_Name>
        <L_Name>Testike7</L_Name>
        <M_Name>Test</M_Name>
        <Full_Name>Dr. Testike5 Test Testike7</Full_Name>
        <Birth>1998-12-12</Birth>
        <Gender>Female</Gender>
        <Smoke>Yes</Smoke>
        <Verification>No</Verification>
        <Language_ID>#0419</Language_ID>
        <Remarks>She is going to be a very good customer!</Remarks>
    </Holder>
    <Contacts>
        <Contact>
            <Type_ID>251</Type_ID>
            <Value>farkas3i@kjabsdijf.hu</Value>
        </Contact>
    </Contacts>
</Message>
```

</details>

## Params

The full list of the default params can be found in the holder actions file.

[Link to the default params listed to the holders](../holder_actions.md#holder-data-items)

The `F_Name` and `L_Name` fields are required. Useing the `Group_ID` field is highly suggested.

---

Besides the default params you can attach other data blocks to the Holder during creation. Data blocks like address, contact, account, card ...

### Add contact 

To add contact info to the new user during creation, just define the `Contacts` block in the message as well.

<details>
	<summary>Request example</summary>

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Add holders" Terminal_Type="<code>" Global_Type="<code>">
    <Holder>
        <Group_ID>8</Group_ID>
        <F_Name>Testike5</F_Name>
        <L_Name>Testike7</L_Name>
    </Holder>
    <Contacts>
        <Contact>
            <Type_ID>251</Type_ID>
            <Value>farkas3i@kjabsdijf.hu</Value>
        </Contact>
    </Contacts>
</Message>
```

</details>

You can read further details (eg.: accepted params) about the contact items here. [Link to contacts](../other/contacts.md)

### Add address 

To add address info to the new user during creation, just define the `Addresses` block in the message as well.

<details>
	<summary>Request example</summary>

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Add holders" Terminal_Type="<code>" Global_Type="<code>">
    <Holder>
        <Group_ID>8</Group_ID>
        <F_Name>Testike5</F_Name>
        <L_Name>Testike7</L_Name>
    </Holder>
	<Addresses>
        <Address>
            <City>Csobanka</City>
            <Street>Kiss utca</Street>
            <House>12 es fel</House>
        </Address>
    </Addresses>
</Message>
```

</details>

You can read further details (eg.: accepted params) about the address items here. [Link to contacts](../other/addresses.md)