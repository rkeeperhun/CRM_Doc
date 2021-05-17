# Search holders 2

This action execute a search in the CRM database.

**Action**: `Search holders 2`

**Example:**

Simple:

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Search holders 2" Terminal_Type="<code>" Global_Type="<code>">
    <Include>Holder_Address,Holder_Contact</Include>
    <Count>5</Count>
    <Index>1</Index>
    <Item Mode="Clear"/>
    <Item Mode="Add">
        <Holders>
            <Full_Name Value="*Laci*"/>
        </Holders>
        <Contacts>
            <Phone Value="+36 30 111 1111"></Phone>
        </Contacts>
    </Item>
</Message>
```

## Search notes


In **string** fields (Login, L_Name, F_Name, M_Name, Full_Name, Phone, Email, City, Street, House), the following replacement characters can be embedded in the values:

- `?` - one arbitrary character
- `*` - a set of arbitrary characters For example,

Eg.: search by surname "St? lov" will give Stulov, Stolov, etc. search by name: "Al *" will return Alexey, Alexander, Alla, etc.

In **integer** (Card_Code) fields, the following replacement characters can be embedded in values:

- `?` - will replace one arbitrary character
- `*` - replaces many arbitrary characters
- `[or]` - numbers at the edges of the set are included in this set
- `(or)` - numbers at the edges of the set are not included in this set; or (or) - union of subsets
- `and (and)` - intersection of subsets,
- `not (not)` - exclude from the set For example, map search:

Eg.: 

- "`1 ?? and * 0 or 55`" - all cards of the first hundred ending in "0", and another card 55 
- "`[1..100)`" - all cards of the first hundred, excluding card 100
- "`>=1000 and <5000`" - all cards are greater than 1000 (inclusive), but less than 5000 '

In the **date fields** (Birth_Day), you can embed zero characters in the values:
Eg.: a search for February "`0000-02-00`" will give everyone who has a birthday in February, etc.


## Search structure notes

Inside the `<Item Mode="Add">` section, the search is performed according to the "AND" principle. These sections that go in a row add the found owners to the general list.

Sort fields can be added to `<Include>`: *Sort_L_Name, Sort_F_Name, Sort_M_Name, Sort_Full_Name, Sort_Birth*. When sorting by birthday, dates that are not filled in will appear at the end of the list.

## Response examples


## Further request examples

Complex search request:

```
<? xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Search holders 2" Terminal_Type="<code>" Global_Type="<code>">
	<Include>Account,Holder_Contact,Holder_Address,Holder_Card</Include>
	<Account_Filter>
		<Account_Class> 2 </Account_Class>
		<Account_Type_ID> 1 </Account_Type_ID> 
	</Account_Filter>
	<Count>25</Count>
	<Index>1</Index>
	<Item Mode="Clear"/>
	<Item Mode="Add">
		<Holders>
			<External_Code Value="Aber *"/>
			<L_Name Value="Istvan *"/>
			<F_Name Value="Aber"/>
			<M_Name Value="Laszlo"/>
			<Full_Name Value="Aber *"/>
			<Birth_Day Value_From="0000-02-01" Value_To="0000-02-07"/> <Image Value="True"/>
			<Group_ID Value="32"/> 
		</Holders>
		<Cards>
			<Card_Code Value="12345 *"/>
			<Carrier_Data Value="987654"/>
			<Group_ID Value="27"/>
			<Group_ID Value="15"/>
		</Cards>
		<Contacts>
			<Phone Value="12345" IsNumber="True"/>
			<EMail Value="mail@mail.com"/>
		</Contacts>
		<Addresses>
			<City Value="Budapest"/>
			<Street Value="Kis utca"/>
			<House Value="20"/>
		</Addresses>
	</Item>
	<Item Mode="Clear"/>
</Message>
```

The sample query displays 25 owners starting from the 1st. If you do not specify the Count parameter, then by default it will be set to 50.

Walking in the index:

```
<? xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Search holders 2" Terminal_Type="<code>" Global_Type="<code>">
	<Count>10</Count>
	<Index>1</Index>
</Message>
```

Receiving the section `<Item Mode="Clear"/>` in the request, the server starts generating a new data set. The xml response will contain `Search_GUID`, which must be specified in subsequent requests to work with this search set.

```
<? xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Search holders 2" Terminal_Type="<code>" Global_Type="<code>">
	<Search_GUID>{46666E09-AC6B-4B5A-B282-7B55E82571BD}</Search_GUID>
	<Count>10</Count>
	<Index>11</Index>
</Message>
```

## Response examples

1. Searching for `Full_Name` like `*Laci*`. Request the first 5 item from all matches. Returning the `Holder_Address` & `Holder_Contact` details besides the default holder details.

<details>
	<summary>Request code</summary>

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Search holders 2" Terminal_Type="<code>" Global_Type="<code>">
    <Include>Holder_Address,Holder_Contact</Include>
    <Count>5</Count>
    <Index>1</Index>
    <Item Mode="Clear"/>
    <Item Mode="Add">
        <Holders>
            <Full_Name Value="*Laci*"/>
        </Holders>
    </Item>
    <Item Mode="Clear"/>
</Message>
```

</details>

<details>
	<summary>Response content</summary>

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Holders Message_ID="0" IndexFrom="1" IndexTo="5" Count="22" Search_GUID="{A4DA3C6A-0AFA-468D-AC3E-39248C552D0B}">
    <Holder>
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
                    <Type_ID>3</Type_ID>
                    <Type_Code>3</Type_Code>
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
    <Holder>
        <Deleted>No</Deleted>
        <Group_ID>3</Group_ID>
        <Group_Name>VIP</Group_Name>
        <Division_ID>1</Division_ID>
        <Division_Name>Head subdivision</Division_Name>
        <Holder_ID>10000000001375</Holder_ID>
        <INN></INN>
        <External_Code></External_Code>
        <Unpay_Type_ID></Unpay_Type_ID>
        <Unpay_Type_Name></Unpay_Type_Name>
        <L_Name>ez mar a previewrol</L_Name>
        <F_Name>laci</F_Name>
        <M_Name></M_Name>
        <Full_Name>ez mar a previewrol laci</Full_Name>
        <Birth>2012-06-06</Birth>
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
                <Holder_ID>10000000001375</Holder_ID>
                <Contact>
                    <Deleted>No</Deleted>
                    <Contact_ID>10000000001419</Contact_ID>
                    <Dispatch>No</Dispatch>
                    <Type_ID>251</Type_ID>
                    <Type_Code>1</Type_Code>
                    <Type_Name>E-mail (egyedi, hírlevéllel)</Type_Name>
                    <Value>jasdbfjhgsadfjh@ajsdfasdfg.hu</Value>
                    <Type_Class>Email</Type_Class>
                    <Notes></Notes>
                </Contact>
                <Contact>
                    <Deleted>No</Deleted>
                    <Contact_ID>10000000001420</Contact_ID>
                    <Dispatch>No</Dispatch>
                    <Type_ID>3</Type_ID>
                    <Type_Code>3</Type_Code>
                    <Type_Name>Telefon</Type_Name>
                    <Value>+82 34658726348576243</Value>
                    <Type_Class>Phone</Type_Class>
                    <Notes></Notes>
                </Contact>
            </Holder_Contact>
        </Holders_Contacts>
        <Holders_Addresses>
            <Holder_Address>
                <Holder_ID>10000000001375</Holder_ID>
            </Holder_Address>
        </Holders_Addresses>
    </Holder>
    <Holder>
        <Deleted>No</Deleted>
        <Group_ID>3</Group_ID>
        <Group_Name>VIP</Group_Name>
        <Division_ID>1</Division_ID>
        <Division_Name>Head subdivision</Division_Name>
        <Holder_ID>10000000001386</Holder_ID>
        <INN></INN>
        <External_Code></External_Code>
        <Unpay_Type_ID></Unpay_Type_ID>
        <Unpay_Type_Name></Unpay_Type_Name>
        <L_Name>sokadikdk</L_Name>
        <F_Name>lacitester</F_Name>
        <M_Name></M_Name>
        <Full_Name>lacitester sokadikdk</Full_Name>
        <Birth>1899-12-30</Birth>
        <Gender>Unknown</Gender>
        <Marrital>Unknown</Marrital>
        <Smoke>No</Smoke>
        <Verification>Yes</Verification>
        <Image>No</Image>
        <Language_ID>0</Language_ID>
        <Language_Name>Unknown</Language_Name>
        <Source></Source>
        <Remarks></Remarks>
        <Holders_Contacts>
            <Holder_Contact>
                <Holder_ID>10000000001386</Holder_ID>
                <Contact>
                    <Deleted>No</Deleted>
                    <Contact_ID>10000000001445</Contact_ID>
                    <Dispatch>No</Dispatch>
                    <Type_ID>251</Type_ID>
                    <Type_Code>1</Type_Code>
                    <Type_Name>E-mail (egyedi, hírlevéllel)</Type_Name>
                    <Value>ajksdhjkaSGDJHgasjhdshd@av.sa</Value>
                    <Type_Class>Email</Type_Class>
                    <Notes></Notes>
                </Contact>
                <Contact>
                    <Deleted>No</Deleted>
                    <Contact_ID>10000000001446</Contact_ID>
                    <Dispatch>No</Dispatch>
                    <Type_ID>3</Type_ID>
                    <Type_Code>3</Type_Code>
                    <Type_Name>Telefon</Type_Name>
                    <Value>+12 834812345</Value>
                    <Type_Class>Phone</Type_Class>
                    <Notes></Notes>
                </Contact>
            </Holder_Contact>
        </Holders_Contacts>
        <Holders_Addresses>
            <Holder_Address>
                <Holder_ID>10000000001386</Holder_ID>
            </Holder_Address>
        </Holders_Addresses>
    </Holder>
    <Holder>
        <Deleted>No</Deleted>
        <Group_ID>3</Group_ID>
        <Group_Name>VIP</Group_Name>
        <Division_ID>1</Division_ID>
        <Division_Name>Head subdivision</Division_Name>
        <Holder_ID>10000000001394</Holder_ID>
        <INN></INN>
        <External_Code></External_Code>
        <Unpay_Type_ID></Unpay_Type_ID>
        <Unpay_Type_Name></Unpay_Type_Name>
        <L_Name>lacilocaltest3</L_Name>
        <F_Name>lacilocaltest3</F_Name>
        <M_Name></M_Name>
        <Full_Name>lacilocaltest3 lacilocaltest3</Full_Name>
        <Birth>1899-12-30</Birth>
        <Gender>Unknown</Gender>
        <Marrital>Unknown</Marrital>
        <Smoke>No</Smoke>
        <Verification>Yes</Verification>
        <Image>No</Image>
        <Language_ID>0</Language_ID>
        <Language_Name>Unknown</Language_Name>
        <Source></Source>
        <Remarks></Remarks>
        <Holders_Contacts>
            <Holder_Contact>
                <Holder_ID>10000000001394</Holder_ID>
                <Contact>
                    <Deleted>No</Deleted>
                    <Contact_ID>10000000001456</Contact_ID>
                    <Dispatch>No</Dispatch>
                    <Type_ID>251</Type_ID>
                    <Type_Code>1</Type_Code>
                    <Type_Name>E-mail (egyedi, hírlevéllel)</Type_Name>
                    <Value>lacilocaltest3@lacilocaltest3.hu</Value>
                    <Type_Class>Email</Type_Class>
                    <Notes></Notes>
                </Contact>
                <Contact>
                    <Deleted>No</Deleted>
                    <Contact_ID>10000000001457</Contact_ID>
                    <Dispatch>No</Dispatch>
                    <Type_ID>3</Type_ID>
                    <Type_Code>3</Type_Code>
                    <Type_Name>Telefon</Type_Name>
                    <Value>+12 34123523452345</Value>
                    <Type_Class>Phone</Type_Class>
                    <Notes></Notes>
                </Contact>
            </Holder_Contact>
        </Holders_Contacts>
        <Holders_Addresses>
            <Holder_Address>
                <Holder_ID>10000000001394</Holder_ID>
            </Holder_Address>
        </Holders_Addresses>
    </Holder>
    <Holder>
        <Deleted>No</Deleted>
        <Group_ID>3</Group_ID>
        <Group_Name>VIP</Group_Name>
        <Division_ID>1</Division_ID>
        <Division_Name>Head subdivision</Division_Name>
        <Holder_ID>10000000001402</Holder_ID>
        <INN></INN>
        <External_Code></External_Code>
        <Unpay_Type_ID></Unpay_Type_ID>
        <Unpay_Type_Name></Unpay_Type_Name>
        <L_Name>Test</L_Name>
        <F_Name>Lacisokadik</F_Name>
        <M_Name></M_Name>
        <Full_Name>Lacisokadik Test</Full_Name>
        <Birth>2001-01-01</Birth>
        <Gender>Unknown</Gender>
        <Marrital>Unknown</Marrital>
        <Smoke>No</Smoke>
        <Verification>Yes</Verification>
        <Image>No</Image>
        <Language_ID>0</Language_ID>
        <Language_Name>Unknown</Language_Name>
        <Source></Source>
        <Remarks></Remarks>
        <Holders_Contacts>
            <Holder_Contact>
                <Holder_ID>10000000001402</Holder_ID>
                <Contact>
                    <Deleted>No</Deleted>
                    <Contact_ID>10000000001474</Contact_ID>
                    <Dispatch>No</Dispatch>
                    <Type_ID>251</Type_ID>
                    <Type_Code>1</Type_Code>
                    <Type_Name>E-mail (egyedi, hírlevéllel)</Type_Name>
                    <Value>nsdfjhvasdfvhsdfv@asdgfjhsdf.hu</Value>
                    <Type_Class>Email</Type_Class>
                    <Notes></Notes>
                </Contact>
                <Contact>
                    <Deleted>No</Deleted>
                    <Contact_ID>10000000001475</Contact_ID>
                    <Dispatch>No</Dispatch>
                    <Type_ID>3</Type_ID>
                    <Type_Code>3</Type_Code>
                    <Type_Name>Telefon</Type_Name>
                    <Value>+18 345634785628</Value>
                    <Type_Class>Phone</Type_Class>
                    <Notes></Notes>
                </Contact>
            </Holder_Contact>
        </Holders_Contacts>
        <Holders_Addresses>
            <Holder_Address>
                <Holder_ID>10000000001402</Holder_ID>
            </Holder_Address>
        </Holders_Addresses>
    </Holder>
</Holders>
```
</details>

2. Searching for Holders with address like. Request the second 5 item from all matches. Returning the `Holder_Address` details besides the default holder details.

<details>
	<summary>Request code</summary>

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

</details>

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


## Side notes

- It should be taken into account that when the CRM server is restarted, the search data sets are reset to zero.
- If you `Include` any extra data to the response (eg.: `Holder_Address`, `Holder_Contact`, ...) and the found Holder has multiple item of those (eg.: Contact-Phone, Contact-email), all of the requested Include item will be added to the response.
- :point_up: even if you search based on an additional data (like: email) all the `Holder_Contact` object will be listed for the found user, not just the one the search was explicitly targeted. So in case you search based on an email address and the found Holder has email contact, phone contact, facebookname contatc, then all of these contact items will be listed to the result for the holder if the `Holder_Contact` is added to the `Include` param.