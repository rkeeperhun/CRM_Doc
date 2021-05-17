# Contacts

There are predefined contatc types eg.: email, Phone, Skype. The UCS compnay can create them.
These has their own type ids which you have use when you'd like to create a new contact and link it to a Holder.
One holder can have more contacts.

## Possible items

| Name | type | info |
| --- | --- | --- |
| Type_ID | integer | provided by the UCS company |
| Value | string | email/phone/other |

## Add new contact to a holder

Contacts only exists as a linked item to a holder, thus creating a new contact only possible when you edit a Holder. You need to define the new contact item as part of the edit XML request.

Request: 

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Edit holders" Terminal_Type="<code>" Global_Type="<code>">
    <Include>Holder_Contact</Include>
    <Holder>
        <Holder_ID>10000000001620</Holder_ID>
        <Contacts>
            <Contact>
                <Type_ID>251</Type_ID>
                <Value>farkas3i@kjabsdijf.hu</Value>
            </Contact>
        </Contacts>
    </Holder>
</Message>
```

Response:
The `Holder_Contact` is added to the `Include` thus all the linked contacts (including the new one) is added to the Holder.

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
    <Holders_Contacts>
        <Holder_Contact>
            <Holder_ID>10000000001620</Holder_ID>
            <Contact>
                <Deleted>No</Deleted>
                <Contact_ID>10000000001693</Contact_ID>
                <Dispatch>No</Dispatch>
                <Type_ID>251</Type_ID>
                <Type_Code>1</Type_Code>
                <Type_Name>E-mail (egyedi, hírlevéllel)</Type_Name>
                <Value>farkas3i@kjabsddfasdfijf.hu</Value>
                <Type_Class>Email</Type_Class>
                <Notes></Notes>
            </Contact>
        </Holder_Contact>
    </Holders_Contacts>
</Holder>
```

*Note*
Either the Email or the phone should be unique system wide (UCS company can set it). If you try to reregister the same emai/phone to another Holder you will get the following error message.

<details>
    <summary>See the error message</summary>

```
<?xml version="1.0" encoding="utf-8" standalone="yes" ?>
<Data Message_ID="0" ErrorCode="SAC-0122" ErrorText="Электронная почта &quot;farkas3i@kjabsddfasdfijf.hu&quot; уже встречается в списках контактов.

Заведение одной и той же почты более чем 1 раз(а) запрещено.
Обратитесь к администратору." />
```

</details>

## Get a Holder's contacts

Request:

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Get holder info" Terminal_Type="<code>" Global_Type="<code>">
    <Holder_ID>10000000001620</Holder_ID>
    <Include>Holder_Contact</Include>
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
    <Holders_Contacts>
        <Holder_Contact>
            <Holder_ID>10000000001620</Holder_ID>
            <Contact>
                <Deleted>No</Deleted>
                <Contact_ID>10000000001693</Contact_ID>
                <Dispatch>No</Dispatch>
                <Type_ID>251</Type_ID>
                <Type_Code>1</Type_Code>
                <Type_Name>E-mail (egyedi, hírlevéllel)</Type_Name>
                <Value>farkas3i@kjabsddfasdfijf.hu</Value>
                <Type_Class>Email</Type_Class>
                <Notes></Notes>
            </Contact>
        </Holder_Contact>
    </Holders_Contacts>
</Holder>
```

</details>

## Get contact types

To list all available contact types and see their Typ_ID.

Request: 

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Get contacts types info" Terminal_Type="<code>" Global_Type="<code>"> </Message>
```

Response example:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Contacts_Types Message_ID="0">
    <Contact_Type>
        <Contact_Type_ID>251</Contact_Type_ID>
        <Contact_Type_Name>E-mail (egyedi, hírlevéllel)</Contact_Type_Name>
        <Contact_Type_Code>1</Contact_Type_Code>
        <Contact_Type_Phone>No</Contact_Type_Phone>
        <Contact_Type_Class>Email</Contact_Type_Class>
        <Contact_Type_EMail>Yes</Contact_Type_EMail>
        <Contact_Type_Skype>No</Contact_Type_Skype>
        <Contact_Type_Social_Network>No</Contact_Type_Social_Network>
        <Contact_Type_Dispatch>Yes</Contact_Type_Dispatch>
    </Contact_Type>
    <Contact_Type>
        <Contact_Type_ID>3</Contact_Type_ID>
        <Contact_Type_Name>Telefon</Contact_Type_Name>
        <Contact_Type_Code>3</Contact_Type_Code>
        <Contact_Type_Phone>Yes</Contact_Type_Phone>
        <Contact_Type_Class>Phone</Contact_Type_Class>
        <Contact_Type_EMail>No</Contact_Type_EMail>
        <Contact_Type_Skype>No</Contact_Type_Skype>
        <Contact_Type_Social_Network>No</Contact_Type_Social_Network>
        <Contact_Type_Dispatch>No</Contact_Type_Dispatch>
    </Contact_Type>
</Contacts_Types>
```