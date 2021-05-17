# Edit holders

This action edits a holder in the CRM. The item `Holder_ID` is required to target the holder that is editable!

**Action**: `Edit holders`

**Example:**

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Edit holders" Terminal_Type="<code>" Global_Type="<code>">
    <Include>Holder_Address</Include>
    <Holder>
        <Holder_ID>10000000001196</Holder_ID>
        <Addresses>
            <Address>
                <Country>Magyarország</Country>
                <City>Csobanka</City>
                <ZIP>1046</ZIP>
                <Street>Naggy utca</Street>
                <House>12 es fel</House>
                <Entry>2es entry</Entry>
                <Building>1es building</Building>
                <Floor>1es Floor</Floor>
                <Apartments>2es Apartments</Apartments>
            </Address>
        </Addresses>
    </Holder>
</Message>
```


## Params

The full list of params can be found in the holder actions file.

[Link to the params listed to the holders](../holder_actions.md#holder-data-items)

The `Holder_ID` field is required for the edit action.

---

Besides the default params you can attach other data blocks to the Holder during edit. Data blocks like address, contact, account, card ...

### Add contact to holder

To add contact info to the new user during creation, just define the `Contacts` block in the message as well.

<details>
	<summary>Request example</summary>

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Add holders" Terminal_Type="<code>" Global_Type="<code>">
    <Holder>
        <Holder_ID>10000000001196</Holder_ID>
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

### Add address to holder

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