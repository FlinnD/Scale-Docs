# Contacts

Contact is a person or business that is the ultimate beneficiary of a payment.

Contact data includes three data blocks.

#### 1\) General Data <a id="recipient-accounts-create-1-general-data"></a>

* Contact full name
* Legal type \(private/business\)
* Currency

#### 2\) Bank account data <a id="recipient-accounts-create-2-bank-account-data"></a>

Bank account details vary widely and depend on the target currency of the payment. For example:

* GBP — sort code and account number
* BGN, CHF, DKK, EUR, GEL, GBP, NOK, PKR, PLN, RON, SEK — IBAN
* USD — routing number, account number, account type
* INR — IFSC code, account number
* etc.

When creating contact, please note that the following general rules should be applied to the _recipients_ field:

* Private contacts must have full names. You must include both a first and last name, and both should be more than one character. Acceptable characters include:`[A-Za-zÀ-ÖØ-öø-ÿ].`
* Business names must be in full, but can be just a single name. The full name cannot be just a single character but can be made up of a set of single characters. Business names can include numbers and special characters.
* In general the following regex describes permitted characters for a name: `[0-9A-Za-zÀ-ÖØ-öø-ÿ-_()'*,.\s]`.

Contact objects will vary depending on type \(currency, business/personal etc\). A GBP example is provided here.

## Contact \(UK\)

### Attributes

| Field | Description | Format |
| :--- | :--- | :--- |
| contactId | Unique identifier for the object. | string |
| type | Contact type: `private` or `business` | string |
| accountHolderName | Full name of the contact: `private` | string |
| businessName | Full name of the contact: `business` | string |
| details.accountNumber | Bank account number \(UK\) | string |
| details.sortCode | Sort code \(UK\) | string |
| address.line1 | Optional address of the contact.  | string |
| address.line2 | Optional address of the contact. | string |
| address.city | Optional city, district, town or village of the contact. | string |
| address.country | Optional two-letter country code of the contact. | 2-letter ISO code |
| details.bankName | Name of the contact's bank. | string |
| details.bankCountry | Two-letter ISO code representing the country the contact's bank account is located. | 2-letter ISO code |
| details.currency | Three-letter ISO code for the currency of the contact's bank account. | 3-letter ISO code |

#### Example fields for UK \(GBP\) contact request:

| Field | Description | Format |
| :--- | :--- | :--- |
| accountHolderName | Full name of the individual | string |
| businessName | Full name of the business | string |
| type | Contact type: `private` or `business` | string |
| details.accountNumber | Bank account number | string |
| details.sortCode | Sort code | string |
| details.currency | Three-letter ISO code for the currency of the contact's bank account. | string |

{% api-method method="post" host="https://app.helloscale.co" path="/v1/contacts/add" %}
{% api-method-summary %}
Create contact
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="details" type="object" required=true %}
The account details of the contact
{% endapi-method-parameter %}

{% api-method-parameter name="currency" type="string" required=true %}
The target currency of contact's account
{% endapi-method-parameter %}

{% api-method-parameter name="accountHolderName" type="string" required=true %}
Full name of contact, 'Personal'.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://app.helloscale.co" path="/v1/contacts/list/:id" %}
{% api-method-summary %}
Retrieve contact by ID
{% endapi-method-summary %}

{% api-method-description %}
Get contact info by ID.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="contactId" type="string" required=false %}
The id of the contact you are requesting
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://app.helloscale.co" path="/v1/contacts/update" %}
{% api-method-summary %}
Update contact
{% endapi-method-summary %}

{% api-method-description %}
Update contact information.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="contactId" type="string" required=true %}
The Id of the contact to update
{% endapi-method-parameter %}

{% api-method-parameter name="details" type="object" required=false %}
The account details of the contact
{% endapi-method-parameter %}

{% api-method-parameter name="currency" type="string" required=false %}
The target currency of the contact's account
{% endapi-method-parameter %}

{% api-method-parameter name="recipient" type="object" required=false %}
Full name of contact \('Personal'  \| 'Business'\)
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://app.helloscale.co" path="/v1/contacts/delete" %}
{% api-method-summary %}
Delete contact
{% endapi-method-summary %}

{% api-method-description %}
Deletes a contact.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="contactId" type="string" required=false %}
The id of the contact to delete.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://app.helloscale.co" path="/v1/contacts/list/all" %}
{% api-method-summary %}
List contacts
{% endapi-method-summary %}

{% api-method-description %}
Fetch a list of all contacts.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

