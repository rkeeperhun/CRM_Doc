# Get holder info

This action retrives holder informations by the holder ID.

**Action**: `Get holder info`

**Example:**

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Get holder info" Session="{00000000-0000-0000-0000-000000000000}" Terminal_Type="<code>" Global_Type="<code>">
    <Holder_ID>10000000001605</Holder_ID>
    <Include>Holder_Contact, Holder_Address</Include>
</Message>
```
## Params

|Name | data | type | optional |
| --- | --- | --- | --- |
| Holder_ID | the ID | integer | required |
| Include | comma separated list of data you'd like to retrive | string | optional |

### Possible data types to retrive

Main:
- Holders_Contact
- Holders_Address
- Account
<!-- - Holders_Card -->

## Answer examples

### Holder with address & contact

<details>
	<summary>Holder with a single address and contact (click to reveal)</summary>

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Holder Message_ID="0">
    <Deleted>No</Deleted>
    <Group_ID>3</Group_ID>
    <Group_Name>VIP</Group_Name>
    <Division_ID>1</Division_ID>
    <Division_Name>Head subdivision</Division_Name>
    <Holder_ID>10000000001339</Holder_ID>
    <INN></INN>
    <External_Code></External_Code>
    <Unpay_Type_ID></Unpay_Type_ID>
    <Unpay_Type_Name></Unpay_Type_Name>
    <L_Name>Laci</L_Name>
    <F_Name>Farkas</F_Name>
    <M_Name></M_Name>
    <Full_Name>Laci Farkas</Full_Name>
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
    <Holders_Contacts>
        <Holder_Contact>
            <Holder_ID>10000000001339</Holder_ID>
            <Contact>
                <Deleted>No</Deleted>
                <Contact_ID>10000000001381</Contact_ID>
                <Dispatch>No</Dispatch>
                <Type_ID>255</Type_ID>
                <Type_Code></Type_Code>
                <Type_Name>Telefon</Type_Name>
                <Value>+3630888888834545</Value>
                <Type_Class>Phone</Type_Class>
                <Notes></Notes>
            </Contact>
        </Holder_Contact>
    </Holders_Contacts>
    <Holders_Addresses>
        <Holder_Address>
            <Holder_ID>10000000001339</Holder_ID>
            <Address>
                <Deleted>No</Deleted>
                <Address_ID>10000000000012</Address_ID>
                <Type_ID>250</Type_ID>
                <Type_Name>Otthon</Type_Name>
                <Country_ID>1</Country_ID>
                <Country>Magyarország</Country>
                <ZIP>123489</ZIP>
                <Region></Region>
                <City_ID>10000000000002</City_ID>
                <City>Esztergom</City>
                <Street_ID>10000000000003</Street_ID>
                <Street>dwfsdfgsdfg</Street>
                <Metro_Station_ID></Metro_Station_ID>
                <Metro_Station></Metro_Station>
                <House>123</House>
                <Building></Building>
                <Entry></Entry>
                <Floor></Floor>
                <Apartments></Apartments>
                <Entry_Code></Entry_Code>
                <DopInfo></DopInfo>
                <LAT></LAT>
                <LNG></LNG>
            </Address>
        </Holder_Address>
    </Holders_Addresses>
</Holder>
```

</details>

<details>
	<summary>Holder with muliple addresses and contacts (click to reveal)</summary>

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Holder Message_ID="0">
    <Deleted>No</Deleted>
    <Group_ID>3</Group_ID>
    <Group_Name>VIP</Group_Name>
    <Division_ID>1</Division_ID>
    <Division_Name>Head subdivision</Division_Name>
    <Holder_ID>10000000001482</Holder_ID>
    <INN></INN>
    <External_Code></External_Code>
    <Unpay_Type_ID></Unpay_Type_ID>
    <Unpay_Type_Name></Unpay_Type_Name>
    <L_Name>Laci</L_Name>
    <F_Name>Farkas</F_Name>
    <M_Name></M_Name>
    <Full_Name>Laci Farkas</Full_Name>
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
    <Holders_Contacts>
        <Holder_Contact>
            <Holder_ID>10000000001482</Holder_ID>
            <Contact>
                <Deleted>No</Deleted>
                <Contact_ID>10000000001574</Contact_ID>
                <Dispatch>No</Dispatch>
                <Type_ID>255</Type_ID>
                <Type_Code></Type_Code>
                <Type_Name>Telefon</Type_Name>
                <Value>06133107774</Value>
                <Type_Class>Phone</Type_Class>
                <Notes></Notes>
            </Contact>
            <Contact>
                <Deleted>No</Deleted>
                <Contact_ID>10000000001575</Contact_ID>
                <Dispatch>No</Dispatch>
                <Type_ID>255</Type_ID>
                <Type_Code></Type_Code>
                <Type_Name>Telefon</Type_Name>
                <Value>0613320778</Value>
                <Type_Class>Phone</Type_Class>
                <Notes></Notes>
            </Contact>
            <Contact>
                <Deleted>No</Deleted>
                <Contact_ID>10000000001576</Contact_ID>
                <Dispatch>No</Dispatch>
                <Type_ID>255</Type_ID>
                <Type_Code></Type_Code>
                <Type_Name>Telefon</Type_Name>
                <Value>06323770778</Value>
                <Type_Class>Phone</Type_Class>
                <Notes></Notes>
            </Contact>
            <Contact>
                <Deleted>No</Deleted>
                <Contact_ID>10000000001577</Contact_ID>
                <Dispatch>No</Dispatch>
                <Type_ID>255</Type_ID>
                <Type_Code></Type_Code>
                <Type_Name>Telefon</Type_Name>
                <Value>0613322233333</Value>
                <Type_Class>Phone</Type_Class>
                <Notes></Notes>
            </Contact>
        </Holder_Contact>
    </Holders_Contacts>
    <Holders_Addresses>
        <Holder_Address>
            <Holder_ID>10000000001482</Holder_ID>
            <Address>
                <Deleted>No</Deleted>
                <Address_ID>10000000000110</Address_ID>
                <Type_ID>250</Type_ID>
                <Type_Name>Otthon</Type_Name>
                <Country_ID>1</Country_ID>
                <Country>Magyarország</Country>
                <ZIP></ZIP>
                <Region></Region>
                <City_ID>10000000000002</City_ID>
                <City>Esztergom</City>
                <Street_ID>10000000000003</Street_ID>
                <Street>dwfsdfgsdfg</Street>
                <Metro_Station_ID></Metro_Station_ID>
                <Metro_Station></Metro_Station>
                <House>123</House>
                <Building></Building>
                <Entry></Entry>
                <Floor></Floor>
                <Apartments></Apartments>
                <Entry_Code></Entry_Code>
                <DopInfo></DopInfo>
                <LAT></LAT>
                <LNG></LNG>
            </Address>
            <Address>
                <Deleted>No</Deleted>
                <Address_ID>10000000000112</Address_ID>
                <Type_ID>250</Type_ID>
                <Type_Name>Otthon</Type_Name>
                <Country_ID>1</Country_ID>
                <Country>Magyarország</Country>
                <ZIP></ZIP>
                <Region></Region>
                <City_ID>10000000000001</City_ID>
                <City>Budapest</City>
                <Street_ID>10000000000006</Street_ID>
                <Street>Vezér</Street>
                <Metro_Station_ID></Metro_Station_ID>
                <Metro_Station></Metro_Station>
                <House>11</House>
                <Building></Building>
                <Entry></Entry>
                <Floor></Floor>
                <Apartments></Apartments>
                <Entry_Code></Entry_Code>
                <DopInfo></DopInfo>
                <LAT></LAT>
                <LNG></LNG>
            </Address>
        </Holder_Address>
    </Holders_Addresses>
</Holder>
```

</details>

### Holder without address, contact
When you include the `Holder_Contact` & `Holder_Address` in the response but the holder does not have any of them you will get an answer like this.

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Holder Message_ID="0">
    <Deleted>No</Deleted>
    <Group_ID>8</Group_ID>
    <Group_Name>WEB</Group_Name>
    <Division_ID>1</Division_ID>
    <Division_Name>Head subdivision</Division_Name>
    <Holder_ID>10000000001523</Holder_ID>
    <INN></INN>
    <External_Code></External_Code>
    <Unpay_Type_ID></Unpay_Type_ID>
    <Unpay_Type_Name></Unpay_Type_Name>
    <L_Name>Farkas</L_Name>
    <F_Name>Lacika</F_Name>
    <M_Name></M_Name>
    <Full_Name>Dr. Test Farkas</Full_Name>
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
    <Holders_Contacts>
        <Holder_Contact>
            <Holder_ID>10000000001523</Holder_ID>
        </Holder_Contact>
    </Holders_Contacts>
    <Holders_Addresses>
        <Holder_Address>
            <Holder_ID>10000000001523</Holder_ID>
        </Holder_Address>
    </Holders_Addresses>
</Holder>
```

### Holder does not exist

```
<?xml version="1.0" encoding="utf-8" standalone="yes" ?>
<Data Message_ID="0" ErrorCode="SAC-0075" ErrorText="Владелец &quot;10000000001582&quot; не обнаружен" />
```


