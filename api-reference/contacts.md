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

## Contact

### Attributes

| Field | Description | Format |
| :--- | :--- | :--- |
| id | Unique identifier for the object. | string |
| type | Contact type: `individual` or `business` | string |
| accountHolderName | Full name of the contact: `individual` | string |
| businessName | Full name of the contact: `business` | string |
| details.accountNumber | Bank account number \(UK\) | string |
| details.sortCode | Sort code \(UK\) | string |
| address.line1 | Optional address of the contact.  | string |
| address.line2 | Optional address of the contact. | string |
| address.city | Optional city, district, town or village of the contact. | string |
| address.country | Optional two-letter country code of the contact. | string - ISO 3166 country |
| details.bankName | Name of the contact's bank. | string |
| details.bankCountry | Two-letter ISO code representing the country the contact's bank account is located. | string - ISO 3166 country |
| details.currency | Three-letter ISO code for the currency of the contact's bank account. | string - ISO 4217 currency |

## API Reference

{% api-method method="post" host="https://app.helloscale.co" path="/v1/contacts" %}
{% api-method-summary %}
Create contact
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="address" type="string" required=false %}
Optional contact address.
{% endapi-method-parameter %}

{% api-method-parameter name="businessName" type="string" required=false %}
Required if type is 'business'.
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
Either 'individual' or 'business'.
{% endapi-method-parameter %}

{% api-method-parameter name="details" type="object" required=true %}
The account details of the contact.
{% endapi-method-parameter %}

{% api-method-parameter name="accountHolderName" type="string" required=false %}
Required if type is 'individual'.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://app.helloscale.co" path="/v1/contacts/:contactId" %}
{% api-method-summary %}
Retrieve contact by ID
{% endapi-method-summary %}

{% api-method-description %}
Get contact info by ID.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="contactId" type="string" required=false %}
Contact ID to retrieve.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "id": "4b88c59c-1f3f-4e99-af82-4eef483ba981",
    "type": "individual",
    "accountHolderName": "Bob Smith",
    "details": {
        "accountNumber": "12345678",
        "sortCode": "112233",
        "currency": "GBP"
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://app.helloscale.co" path="/v1/contacts/:contactId" %}
{% api-method-summary %}
Update contact
{% endapi-method-summary %}

{% api-method-description %}
Update contact information.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="contactId" type="string" required=true %}
Contact ID to update.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="details" type="object" required=false %}
The account details of the contact.
{% endapi-method-parameter %}

{% api-method-parameter name="currency" type="string" required=false %}
The target currency of the contact's account.
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

{% api-method method="delete" host="https://app.helloscale.co" path="/v1/contacts/:contactId" %}
{% api-method-summary %}
Delete contact
{% endapi-method-summary %}

{% api-method-description %}
Deletes a contact.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="contactId" type="string" required=true %}
Contact ID to delete.
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

{% api-method method="get" host="https://app.helloscale.co" path="/v1/contacts" %}
{% api-method-summary %}
List contacts
{% endapi-method-summary %}

{% api-method-description %}
Fetch a list of all contacts.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "count": 2,
    "items": [
        {
            "id": "4b88c59c-1f3f-4e99-af82-4eef483ba981",
            "type": "individual",
            "accountHolderName": "Bob Smith",
            "details": {
                "accountNumber": "12345678",
                "sortCode": "112233",
                "currency": "GBP"
            }
        },
        {
            "id": "e12a82a9-441d-4050-8edd-3d102b5d0dc2",
            "type": "business",
            "businessName": "Shoply Ltd",
            "details": {
                "accountNumber": "12345678",
                "sortCode": "112233",
                "currency": "GBP"
            }
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

