# Contacts

## The contact object

| Field | Description | Format |
| :--- | :--- | :--- |
| id | Unique identifier for the object. | string |
| type | Contact type: `individual` or `company` | enum |
| name | Full name of the business or individual | string |
| email | Optional email address of the contact. | email |
| telephone | Optional phone number of the contact. | International phone number, starting with `+` |
| address.line1 | Optional address of the contact.  | string |
| address.line2 | Optional address of the contact. | string |
| address.city | Optional city, district, town or village of the contact. | string |
| address.country | Optional two-letter country code of the contact. | 2-letter ISO code |
| bank\_name | Name of the contact's bank. | string |
| bank\_country | Two-letter ISO code representing the country the contact's bank account is located. | 2-letter ISO code |
| currency | Three-letter ISO code for the currency of the contact's bank account. | 3-letter ISO code |

#### Required fields for UK GBP accounts:

| Field | Description | Format |
| :--- | :--- | :--- |
| account\_no | Bank account number | string |
| sort\_code | Sort code | string |

#### Required fields for IBAN countries:

| Field | Description | Format |
| :--- | :--- | :--- |
| iban | IBAN | string |
| bic | BIC | string |

#### Required fields for US USD accounts:

| Field | Description | Format |
| :--- | :--- | :--- |
| account\_no | Bank account number | string |
| routing\_number | Routing transit number | string |

#### Required fields for SWIFT:

| Field | Description | Format |
| :--- | :--- | :--- |
| account\_no | Bank account number | string |
| bic | BIC | string |

{% api-method method="post" host="" path="" %}
{% api-method-summary %}
Create contact
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

{% api-method method="get" host="" path="" %}
{% api-method-summary %}
Retrieve contact by ID
{% endapi-method-summary %}

{% api-method-description %}
Get contact info by ID.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

{% api-method method="post" host="" path="" %}
{% api-method-summary %}
Update contact
{% endapi-method-summary %}

{% api-method-description %}
Update contact information.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

{% api-method method="delete" host="" path="" %}
{% api-method-summary %}
Delete contact
{% endapi-method-summary %}

{% api-method-description %}
Deletes a contact.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

{% api-method method="get" host="" path="" %}
{% api-method-summary %}
List contacts
{% endapi-method-summary %}

{% api-method-description %}
Fetch a list of all contacts.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

