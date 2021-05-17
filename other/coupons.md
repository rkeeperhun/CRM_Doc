# Coupons

The UCS company can create the various coupon types for you. 


## Add coupon to Holder

| Name | type | info |
| --- | --- | --- |
| External_ID | string | extrenal indentifier |
| Coupon_Type_ID | integer | required, [one of the IDs from the Get Coupon types list](#get-coupon-types) |
| Holder_ID | integer | the identifier of the owner who will own the coupon (this parameter is optional). If not specified, the coupon will be non-personalized. |
| Terminals_Types | - | empty list to use the default of the coupon |
| Status | string | can be Active, in which case the coupon will be activated upon issue |
| Offered | date | start (and end date) of the coupon. If the parameters are not specified, then the coupon is meant for an unlimited period. |
| Expired | date | (start and) end date of the coupon. If the parameters are not specified, then the coupon is meant for an unlimited period. |
<!-- | Terminals_Types | string | required, provided by the UCS company | -->
<!-- In the case of an empty list (<Terminals_Types />), the classifiers will be taken from the list of coupon type classifiers. If the All attribute is specified (<Terminals_Types All = "True">), the coupon will be available at all points. If a certain list of classifiers is presented, then the coupon will be valid exclusively for classifiers from this list. -->

```
<? xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Add coupons" Terminal_Type="<code>" Global_Type="<code>">
<Coupon>
	<Coupon_Type_ID>1</Coupon_Type_ID>
	<Status>Active</Status>
	<External_ID>123</External_ID>
	<Holder_ID>1</Holder_ID>
	<Offered>2021-05-01</Offered>
	<Expired>2022-01-31</Expired>
	<Notes></Notes>
	<Terminals_Types></Terminals_Types>
</Coupon>
</Message>
```

Response:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Coupons Message_ID="0">
    <Coupon>
        <Coupon_ID>9220015687528583695</Coupon_ID>
        <Coupon_Code>5687528583695</Coupon_Code>
    </Coupon>
</Coupons>
```

## Get Holder's coupons

Request:

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Get holder info" Terminal_Type="<code>" Global_Type="<code>">
    <Holder_ID>10000000001621</Holder_ID>
    <Include>Holder_Coupon</Include>
</Message>
```

<details>
	<summary>None empty response</summary>

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
    <Holders_Coupons IndexFrom="1" IndexTo="1"  Count="1">
        <Holder_Coupon>
            <Holder_ID>10000000001621</Holder_ID>
            <Coupon>
                <Coupon_ID>9220015687528583695</Coupon_ID>
                <Coupon_Code>5687528583695</Coupon_Code>
                <Coupon_Class>1</Coupon_Class>
                <Coupon_Type_ID>4</Coupon_Type_ID>
                <Coupon_Type_Name>
                    <![CDATA[Regisztrációs 10% Kupon]]>
                </Coupon_Type_Name>
                <Coupon_Type_Flags>39</Coupon_Type_Flags>
                <Is_Confirm_Manager>No</Is_Confirm_Manager>
                <Holder_ID>10000000001621</Holder_ID>
                <Timing_Scheme_ID>1</Timing_Scheme_ID>
                <Status>Active</Status>
                <Offered>2021-05-01</Offered>
                <Expired>2022-01-31</Expired>
                <Notes>Coupons note for 10000000001621</Notes>
                <Discounts>
                    <Discount>
                        <Discount_ID>1</Discount_ID>
                        <Discount_Name>
                            <![CDATA[10% Online Regisztráció Kupon séma]]>
                        </Discount_Name>
                        <Discount_Rate>10.00</Discount_Rate>
                        <External_ID>37</External_ID>
                    </Discount>
                </Discounts>
                <Terminals_Types>
                    <Terminal_Type>
                        <Terminal_Type_ID>4</Terminal_Type_ID>
                        <Terminal_Type_Name>WEB</Terminal_Type_Name>
                        <Terminal_Type_Type>WEB</Terminal_Type_Type>
                        <Terminal_Type_TimeBegin>07:00:00</Terminal_Type_TimeBegin>
                        <Terminal_Type_TimeZone>+02:00</Terminal_Type_TimeZone>
                    </Terminal_Type>
                </Terminals_Types>
            </Coupon>
        </Holder_Coupon>
    </Holders_Coupons>
</Holder>
```	

</details>

<details>
	<summary>Empty response</summary>

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
    <Holders_Coupons  Count="0">
        <Holder_Coupon>
            <Holder_ID>10000000001621</Holder_ID>
        </Holder_Coupon>
    </Holders_Coupons>
</Holder>
```

</details>

## Get coupon info

Request:

```
<? xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Get coupon info" Terminal_Type="<code>" Global_Type="<code>">
<Coupon_ID>9220015687528583695</Coupon_ID>
</Message>
```

Response:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Coupons Message_ID="0">
    <Coupon>
        <Coupon_ID>9220015687528583695</Coupon_ID>
        <Coupon_Code>5687528583695</Coupon_Code>
        <Coupon_Class>1</Coupon_Class>
        <Coupon_Type_ID>4</Coupon_Type_ID>
        <Coupon_Type_Name>
            <![CDATA[Regisztrációs 10% Kupon]]>
        </Coupon_Type_Name>
        <Coupon_Type_Flags>39</Coupon_Type_Flags>
        <Is_Confirm_Manager>No</Is_Confirm_Manager>
        <Holder_ID>10000000001621</Holder_ID>
        <Timing_Scheme_ID>1</Timing_Scheme_ID>
        <Status>Active</Status>
        <Offered>2021-05-01</Offered>
        <Expired>2022-01-31</Expired>
        <Notes>Coupons note for 10000000001621</Notes>
        <Discounts>
            <Discount>
                <Discount_ID>1</Discount_ID>
                <Discount_Name>
                    <![CDATA[10% Online Regisztráció Kupon séma]]>
                </Discount_Name>
                <Discount_Rate>10.00</Discount_Rate>
                <External_ID>37</External_ID>
            </Discount>
        </Discounts>
        <Terminals_Types>
            <Terminal_Type>
                <Terminal_Type_ID>4</Terminal_Type_ID>
                <Terminal_Type_Name>WEB</Terminal_Type_Name>
                <Terminal_Type_Type>WEB</Terminal_Type_Type>
                <Terminal_Type_TimeBegin>07:00:00</Terminal_Type_TimeBegin>
                <Terminal_Type_TimeZone>+02:00</Terminal_Type_TimeZone>
            </Terminal_Type>
        </Terminals_Types>
    </Coupon>
</Coupons>
```

## Activate coupon

Request:

```
<? xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Coupon active" Terminal_Type="<code>" Global_Type="<code>">
<Coupon_ID>123456789012345678</Coupon_ID>
<Summ>123.45</Summ>
</Message>
```

## Get Coupon types

Request:

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="Get coupons types info" Terminal_Type="<code>" Global_Type="<code>"></Message>
```

Response:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<Coupons_Types Message_ID="0">
    <Coupon_Type>
        <Coupon_Type_ID>4</Coupon_Type_ID>
        <Coupon_Type_Name>
            <![CDATA[Regisztrációs 10% Kupon]]>
        </Coupon_Type_Name>
        <Coupon_Type_Notes></Coupon_Type_Notes>
        <Discount_External_ID>37</Discount_External_ID>
        <Discount_Name>
            <![CDATA[10% Online Regisztráció Kupon séma]]>
        </Discount_Name>
        <Discount_Rate>10.00</Discount_Rate>
        <Discount_Limit>0.00</Discount_Limit>
        <Terminals_Types>
            <Terminal_Type>
                <Terminal_Type_ID>4</Terminal_Type_ID>
                <Terminal_Type_Name>WEB</Terminal_Type_Name>
                <Terminal_Type_Type>WEB</Terminal_Type_Type>
                <Terminal_Type_TimeBegin>07:00:00</Terminal_Type_TimeBegin>
                <Terminal_Type_TimeZone>+02:00</Terminal_Type_TimeZone>
            </Terminal_Type>
        </Terminals_Types>
    </Coupon_Type>
    <Coupon_Type>
        <Coupon_Type_ID>6</Coupon_Type_ID>
        <Coupon_Type_Name>Süti kupon a 10. vásárlás után</Coupon_Type_Name>
        <Coupon_Type_Notes></Coupon_Type_Notes>
        <Coupon_Type_Details>
            <Coupon_Type_Detail>
                <Coupon_Type_Detail_Name>Ajándék sütemény</Coupon_Type_Detail_Name>
                <Coupon_Type_Detail_Notes></Coupon_Type_Detail_Notes>
                <Coupon_Type_Detail_Max>1</Coupon_Type_Detail_Max>
                <Coupon_Type_Detail_Priority>1</Coupon_Type_Detail_Priority>
                <Coupon_Type_Detail>
                    <Coupon_Type_Detail_External_Code>273</Coupon_Type_Detail_External_Code>
                    <Coupon_Type_Detail_Name>Túrógombóc</Coupon_Type_Detail_Name>
                    <Coupon_Type_Detail_Notes></Coupon_Type_Detail_Notes>
                    <Coupon_Type_Detail_Max></Coupon_Type_Detail_Max>
                    <Coupon_Type_Detail_Value>100.00</Coupon_Type_Detail_Value>
                    <Coupon_Type_Detail_Priority></Coupon_Type_Detail_Priority>
                    <Coupon_Type_Detail_Auto>True</Coupon_Type_Detail_Auto>
                    <Coupon_Type_Detail_Kind>percent</Coupon_Type_Detail_Kind>
                </Coupon_Type_Detail>
            </Coupon_Type_Detail>
        </Coupon_Type_Details>
        <Terminals_Types>
  </Terminals_Types>
    </Coupon_Type>
</Coupons_Types>
```