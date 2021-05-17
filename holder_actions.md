# Holder actions

- **[Add holders](holder_actions/add_holders.md)**
- **[Edit holders](holder_actions/edit_holders.md)**
- **[Search holders](holder_actions/search_holders_2.md)**
- **[Get holder info](holder_actions/get_holder_info.md)** 

## Holder data items

The CRM system provides options for the following 

| Name | info | type | Updatable |
| --- | --- | --- | --- |
| Holder_ID | the holder's unique ID (14 character) | integer | no (the system generates it) |
| Group_ID | holder's group ID | integer | yes, optional |
| External_Code | external id the vendor can define | string | yes, optional |
| L_Name | last name | string | yes, required |
| F_Name | first name | string | yes, required |
| M_Name | middle name | string | yes |
| Full_Name | full name | string | yes |
| Birth | day Born (yyyy-mm-dd) | string | yes, optional ["Unknown" - not specified] |
| Gender | sex | string | yes, optional ["Unknown" - is not defined, "Male" - men, "Female" - female] | 
| Marrital | marital status | string | yes, optional ["Unknown" - not determined, "No" - Single (Single), "Yes" - Single (Single)] |
| Smoke | smoke status | string | yes, optional ["No" - not smoking, "Yes" - smoking] |
| Verification | optinal verification status for the holder | string | yes, optional ["No" - not verified, "Yes" - verified] |
| Language_ID | language code (UCS provides it) | string | yes, optional ["Unknown" - undefined] |
| Language_Name | language name | string | yes, optional ["Unknown" - not determined] |
| Remarks | notes for the holder | string | yes, optional |
| Division_ID | department code | integer | no (the system adds it) |
| Division_Name | division title | string | no (the system adds it) |
| Unpay_Type_ID | (defaulter code) | integer | yes, not needed |
| Unpay_Type_Name | (defaulter name) | string | yes, not needed |
<!-- | Dispatch_EMail | permission to EMail newsletter | no, ["True" - allowed to "False" - prohibited] | -->
<!-- | Dispatch_SMS | for SMS permission | string | no, ["True" - allowed to, "False" - prohibited] | -->

## Other data items

Everything starts with a Holder. Address data, Contact data, Account data, Card data ... can only exist when it's attached to a holder. New address,contact ... can be created during add Holder and edit Holder actions.

### Possible additional data types

| Name | Info | link|
| --- | --- | --- |
| Account | | [link](other/account.md) |
| Holder_Contact | keeps contact informations | [link](other/contacts.md)|
| Holder_Address | keeps address informations | [link](other/address.md)|
<!-- | Holder_Card | keeps card informations | [link](other/cards.md)| -->
<!-- | Holder_Coupon | keeps coupon informations | [link](other/coupons.md)| -->