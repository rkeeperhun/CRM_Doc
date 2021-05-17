# Addresses

There are predefined address types eg.: home, workplace. The UCS compnay can create them.
These has their own type ids which you have use when you'd like to create a new address and link it to a Holder.
One holder can have more addresses.

## Possible items

| Name | type | info |
| --- | --- | --- |
| Type_ID (type) | Integer | required, [how to get it](#get-address-types) |
| Country_ID (country) | Integer | system adds it |
| ZIP (index) | Integer | |
| Region (region / region) | String (40)  | |
| City_ID (city) | Int64 | system adds it |
| Street_ID (street) | Int64 | system adds it |
| House (house) | String (10) | |
| Building (building) | String (10)  | |
| Entry (entrance) | String (10) | |
| Floor | String (10) | |
| Apartments (apartment) | String (10)  | |
| Entry_Code (doorphone code) | String (10)  | |
| DopInfo (additional information) | String (500)  | |
| Deleted (delete flag) | String ["True" - delete, "False" - do not delete] | |
| Country | String (60) | |
| City (city) | String (60)  | |
| Street (street) | String (100) | |

## Add new address

Addresses only exists as a linked item to a holder, thus creating a new address only possible when you edit a Holder. You need to define the new address item as part of the edit XML request.

Request: 

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Edit holders" Terminal_Type="<code>" Global_Type="<code>">
    <Include>Holder_Address</Include>
    <Holder>
        <Holder_ID>10000000001620</Holder_ID>
        <Addresses>
            <Address>
                <City>Csobanka</City>
                <Street>Kiss utca</Street>
                <House>12 es fel</House>
            </Address>
        </Addresses>
    </Holder>
</Message>
```

Response:
The `Holder_Address` is added to the `Include` thus all the linked addresses (including the new one) is added to the Holder.

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Holder Message_ID="0">
    <Deleted>No</Deleted>
    <Group_ID>8</Group_ID>
    <Group_Name>WEB</Group_Name>
    <Division_ID>1</Division_ID>
    <Division_Name>Head subdivision</Division_Name>
    <Holder_ID>10000000001620</Holder_ID>
    <INN></INN>
    <External_Code></External_Code>
    <Unpay_Type_ID></Unpay_Type_ID>
    <Unpay_Type_Name></Unpay_Type_Name>
    <L_Name>Testike7</L_Name>
    <F_Name>Testike12</F_Name>
    <M_Name></M_Name>
    <Full_Name>Testike7 Testike12</Full_Name>
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
    <Holders_Addresses>
        <Holder_Address>
            <Holder_ID>10000000001620</Holder_ID>
            <Address>
                <Deleted>No</Deleted>
                <Address_ID>10000000000237</Address_ID>
                <Type_ID>250</Type_ID>
                <Type_Name>Otthon</Type_Name>
                <Country_ID>1</Country_ID>
                <Country>Magyarország</Country>
                <ZIP></ZIP>
                <Region></Region>
                <City_ID>10000000000018</City_ID>
                <City>Csobanka</City>
                <Street_ID>10000000000045</Street_ID>
                <Street>Kiss utca</Street>
                <Metro_Station_ID></Metro_Station_ID>
                <Metro_Station></Metro_Station>
                <House>12 es fel</House>
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

*Note*
When you add a new address, the address lines are (extremly) normalized when checking if the new address already exist and linked to the user. By (extreamly) noramlized I mean that the string fields are lowercased and every whitespace charatcer (including from the middle) is removed for the check. This means that in case only the whitespaces or the letter case is different between an exisitng and a new address, then the new address won't be added to the system.
☝️(extream) normalization is used during the comparision, but the fields as saved unchanged. So if you pass the street all uppercase (KISS UTCA), then it will be saved that way. But when next time you try to save the same address with all lower case (kiss utca), then the CRM won't register a new address.

## Get a Holder's addresses

Request:

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Get holder info" Terminal_Type="<code>" Global_Type="<code>">
    <Holder_ID>10000000001621</Holder_ID>
    <Include>Holder_Address</Include>
</Message>
```

<details>
    <summary>Response content</summary>

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
    <Holders_Contacts>
        <Holder_Contact>
            <Holder_ID>10000000001621</Holder_ID>
        </Holder_Contact>
    </Holders_Contacts>
    <Holders_Addresses>
        <Holder_Address>
            <Holder_ID>10000000001621</Holder_ID>
        </Holder_Address>
    </Holders_Addresses>
</Holder>
```

</details>

Further details in the [Get Holder info](../holder_actions/get_holder_info.md) page.

## Search by address

When you search by address, the response will contain all Holders with an address like you're looking for! And all addresses of the given Holder will be listed in the response not just the one you searched for.

More details about the [Search options](../search_holders_2.md).

Request:

```
<? xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Search holders 2" Terminal_Type="<code>" Global_Type="<code>">
    <Include>Holder_Address,Holder_Contact</Include>
    <Count>5</Count>
    <Index>1</Index>
    <Item Mode="Clear"/>
    <Item Mode="Add">
        <Addresses>
            <City Value="Esztergom" />
        </Addresses>
    </Item>
    <Item Mode="Clear"/>
</Message>
```

<details>
    <summary>Response content</summary>

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Holders Message_ID="0" IndexFrom="6" IndexTo="10" Count="11" Search_GUID="{AF5B8E0C-C836-4E61-85B2-22807F08CF25}">
    <Holder>
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
    <Holder>
        <Deleted>No</Deleted>
        <Group_ID>3</Group_ID>
        <Group_Name>VIP</Group_Name>
        <Division_ID>1</Division_ID>
        <Division_Name>Head subdivision</Division_Name>
        <Holder_ID>10000000001498</Holder_ID>
        <INN></INN>
        <External_Code></External_Code>
        <Unpay_Type_ID></Unpay_Type_ID>
        <Unpay_Type_Name></Unpay_Type_Name>
        <L_Name>Barna</L_Name>
        <F_Name>Kovács</F_Name>
        <M_Name></M_Name>
        <Full_Name>Barna Kovács</Full_Name>
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
        <Holders_Addresses>
            <Holder_Address>
                <Holder_ID>10000000001498</Holder_ID>
                <Address>
                    <Deleted>No</Deleted>
                    <Address_ID>10000000000117</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP>0001</ZIP>
                    <Region></Region>
                    <City_ID>10000000000010</City_ID>
                    <City>Alap varos</City>
                    <Street_ID>10000000000028</Street_ID>
                    <Street>Szugló</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>79</House>
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
                    <Address_ID>10000000000172</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP></ZIP>
                    <Region></Region>
                    <City_ID>10000000000020</City_ID>
                    <City>Bicske (Galagonyás 1.-es dűlő)</City>
                    <Street_ID>10000000000061</Street_ID>
                    <Street>Utca Utca</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>3</House>
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
                    <Address_ID>10000000000181</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP></ZIP>
                    <Region></Region>
                    <City_ID>10000000000002</City_ID>
                    <City>Esztergom</City>
                    <Street_ID>10000000000067</Street_ID>
                    <Street>Teszt</Street>
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
                <Address>
                    <Deleted>No</Deleted>
                    <Address_ID>10000000000194</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP></ZIP>
                    <Region></Region>
                    <City_ID>10000000000012</City_ID>
                    <City>Budapest III</City>
                    <Street_ID>10000000000071</Street_ID>
                    <Street>Utca</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>3</House>
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
    <Holder>
        <Deleted>No</Deleted>
        <Group_ID>3</Group_ID>
        <Group_Name>VIP</Group_Name>
        <Division_ID>1</Division_ID>
        <Division_Name>Head subdivision</Division_Name>
        <Holder_ID>10000000001506</Holder_ID>
        <INN></INN>
        <External_Code></External_Code>
        <Unpay_Type_ID></Unpay_Type_ID>
        <Unpay_Type_Name></Unpay_Type_Name>
        <L_Name>Imre</L_Name>
        <F_Name>Ficsór</F_Name>
        <M_Name></M_Name>
        <Full_Name>Imre Ficsór</Full_Name>
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
        <Holders_Addresses>
            <Holder_Address>
                <Holder_ID>10000000001506</Holder_ID>
                <Address>
                    <Deleted>No</Deleted>
                    <Address_ID>10000000000122</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP>0001</ZIP>
                    <Region></Region>
                    <City_ID>10000000000010</City_ID>
                    <City>Alap varos</City>
                    <Street_ID>10000000000027</Street_ID>
                    <Street>Teszt</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>83</House>
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
                    <Address_ID>10000000000129</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP>0001</ZIP>
                    <Region></Region>
                    <City_ID>10000000000010</City_ID>
                    <City>Alap varos</City>
                    <Street_ID>10000000000015</Street_ID>
                    <Street>Szugló utca</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>83.-85.</House>
                    <Building></Building>
                    <Entry>5.-ös ajtó</Entry>
                    <Floor>1. emelet</Floor>
                    <Apartments></Apartments>
                    <Entry_Code></Entry_Code>
                    <DopInfo></DopInfo>
                    <LAT></LAT>
                    <LNG></LNG>
                </Address>
                <Address>
                    <Deleted>No</Deleted>
                    <Address_ID>10000000000133</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP>1039</ZIP>
                    <Region></Region>
                    <City_ID>10000000000012</City_ID>
                    <City>Budapest III</City>
                    <Street_ID>10000000000033</Street_ID>
                    <Street>Szugló Utca</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>83.-85.</House>
                    <Building></Building>
                    <Entry>5.-ös ajtó</Entry>
                    <Floor>1. emelet</Floor>
                    <Apartments></Apartments>
                    <Entry_Code></Entry_Code>
                    <DopInfo></DopInfo>
                    <LAT></LAT>
                    <LNG></LNG>
                </Address>
                <Address>
                    <Deleted>No</Deleted>
                    <Address_ID>10000000000134</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP>2022</ZIP>
                    <Region></Region>
                    <City_ID>10000000000002</City_ID>
                    <City>Esztergom</City>
                    <Street_ID>10000000000034</Street_ID>
                    <Street>Szugló Utca</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>83.-85.</House>
                    <Building></Building>
                    <Entry>5.-ös ajtó</Entry>
                    <Floor>1. emelet</Floor>
                    <Apartments></Apartments>
                    <Entry_Code></Entry_Code>
                    <DopInfo></DopInfo>
                    <LAT></LAT>
                    <LNG></LNG>
                </Address>
                <Address>
                    <Deleted>No</Deleted>
                    <Address_ID>10000000000135</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP>0</ZIP>
                    <Region></Region>
                    <City_ID>10000000000013</City_ID>
                    <City>Budapest II</City>
                    <Street_ID>10000000000035</Street_ID>
                    <Street>Szugló Utca</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>83.-85.</House>
                    <Building></Building>
                    <Entry>5.-ös ajtó</Entry>
                    <Floor>1. emelet</Floor>
                    <Apartments></Apartments>
                    <Entry_Code></Entry_Code>
                    <DopInfo></DopInfo>
                    <LAT></LAT>
                    <LNG></LNG>
                </Address>
            </Holder_Address>
        </Holders_Addresses>
    </Holder>
    <Holder>
        <Deleted>No</Deleted>
        <Group_ID>3</Group_ID>
        <Group_Name>VIP</Group_Name>
        <Division_ID>1</Division_ID>
        <Division_Name>Head subdivision</Division_Name>
        <Holder_ID>10000000001509</Holder_ID>
        <INN></INN>
        <External_Code></External_Code>
        <Unpay_Type_ID></Unpay_Type_ID>
        <Unpay_Type_Name></Unpay_Type_Name>
        <L_Name></L_Name>
        <F_Name>bundus</F_Name>
        <M_Name></M_Name>
        <Full_Name>bundus</Full_Name>
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
        <Holders_Addresses>
            <Holder_Address>
                <Holder_ID>10000000001509</Holder_ID>
                <Address>
                    <Deleted>No</Deleted>
                    <Address_ID>10000000000125</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP></ZIP>
                    <Region></Region>
                    <City_ID>10000000000010</City_ID>
                    <City>Alap varos</City>
                    <Street_ID>10000000000020</Street_ID>
                    <Street>Felhévizi</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>1</House>
                    <Building>3</Building>
                    <Entry>4</Entry>
                    <Floor>5</Floor>
                    <Apartments>2</Apartments>
                    <Entry_Code>6</Entry_Code>
                    <DopInfo>7</DopInfo>
                    <LAT></LAT>
                    <LNG></LNG>
                </Address>
                <Address>
                    <Deleted>No</Deleted>
                    <Address_ID>10000000000165</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP></ZIP>
                    <Region></Region>
                    <City_ID>10000000000012</City_ID>
                    <City>Budapest III</City>
                    <Street_ID>10000000000033</Street_ID>
                    <Street>Szugló Utca</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>83-85</House>
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
                    <Address_ID>10000000000169</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP></ZIP>
                    <Region></Region>
                    <City_ID>10000000000012</City_ID>
                    <City>Budapest III</City>
                    <Street_ID>10000000000033</Street_ID>
                    <Street>Szugló Utca</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>83</House>
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
                    <Address_ID>10000000000171</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP></ZIP>
                    <Region></Region>
                    <City_ID>10000000000002</City_ID>
                    <City>Esztergom</City>
                    <Street_ID>10000000000060</Street_ID>
                    <Street>Fő Utca</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>83</House>
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
                    <Address_ID>10000000000176</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP></ZIP>
                    <Region></Region>
                    <City_ID>10000000000002</City_ID>
                    <City>Esztergom</City>
                    <Street_ID>10000000000063</Street_ID>
                    <Street>Fő</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>4</House>
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
                    <Address_ID>10000000000179</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP></ZIP>
                    <Region></Region>
                    <City_ID>10000000000012</City_ID>
                    <City>Budapest III</City>
                    <Street_ID>10000000000065</Street_ID>
                    <Street>Fő</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>2</House>
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
                    <Address_ID>10000000000180</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP></ZIP>
                    <Region></Region>
                    <City_ID>10000000000002</City_ID>
                    <City>Esztergom</City>
                    <Street_ID>10000000000066</Street_ID>
                    <Street>Kossuth</Street>
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
    <Holder>
        <Deleted>No</Deleted>
        <Group_ID>8</Group_ID>
        <Group_Name>WEB</Group_Name>
        <Division_ID>1</Division_ID>
        <Division_Name>Head subdivision</Division_Name>
        <Holder_ID>10000000001520</Holder_ID>
        <INN></INN>
        <External_Code></External_Code>
        <Unpay_Type_ID></Unpay_Type_ID>
        <Unpay_Type_Name></Unpay_Type_Name>
        <L_Name>Test</L_Name>
        <F_Name>Laci</F_Name>
        <M_Name></M_Name>
        <Full_Name>Test Laci</Full_Name>
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
        <Holders_Addresses>
            <Holder_Address>
                <Holder_ID>10000000001520</Holder_ID>
                <Address>
                    <Deleted>No</Deleted>
                    <Address_ID>10000000000142</Address_ID>
                    <Type_ID>250</Type_ID>
                    <Type_Name>Otthon</Type_Name>
                    <Country_ID>1</Country_ID>
                    <Country>Magyarország</Country>
                    <ZIP>2034</ZIP>
                    <Region></Region>
                    <City_ID>10000000000002</City_ID>
                    <City>Esztergom</City>
                    <Street_ID>10000000000041</Street_ID>
                    <Street>Szallitasi utca</Street>
                    <Metro_Station_ID></Metro_Station_ID>
                    <Metro_Station></Metro_Station>
                    <House>szal-10</House>
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
</Holders>
``` 

</details>

## Get address types

To list all available address types and see their Typ_ID.

Request: 

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Get addresses types info" Terminal_Type="<code>" Global_Type="<code>"> </Message>
```

Response example:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Addresses_Types Message_ID="0">
    <Address_Type>
        <Address_Type_ID>251</Address_Type_ID>
        <Address_Type_Name>Munkahely</Address_Type_Name>
    </Address_Type>
    <Address_Type>
        <Address_Type_ID>250</Address_Type_ID>
        <Address_Type_Name>Otthon</Address_Type_Name>
    </Address_Type>
</Addresses_Types>
```