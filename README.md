# Documentation of the UCS's CRM system


## Baiscs

Requests are transmitted via TCP / IP in the card authorization server.

### XML based system
The CRM receives XML requests and sends XML responses.

Example:

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Message Action="<action name>" Terminal_Type="<code>" Global_Type="<code>"></Message>
```

**Notes to pay attention to:**
- make sure you remove every excessive whitespace characters from the XML code
- the CRM system is a Russian development, error messages most likely describe the issue in Russian language
- upper and lower case letters are used strictely when it comes to the param/argumnet keys
- `"` is not supported in the passed content. Please remove all `"` apostrophes from the posted string contents!

### Authentication
The authentication happens with the `Terminal_Type` and `Global_Type` values in the XML message. With some exceptions all the requests requires authentication!
Thease authentication codes are provided by the UCS company.

<details>
	<summary>Authentication error example</summary>

```
<?xml version="1.0" encoding="utf-8" standalone="yes" ?>
<Data Message_ID="0" ErrorCode="SAC-0004" ErrorText="Ошибочно введен классификатор &#91;&quot;asdfTsssEST&quot;&#93;" />
```

</details>

### URL
The requests' target is always the root address of the domain/IP provided the the UCS company. The domain/IP is pointed to the CRM hosting server and a PORT address almost always defined as well. 
The server can be located at the vendor's own location as well.

**Example:**
`https://ucs.hu/9999`

## Holder actions

[Holder actions](holder_actions.md)