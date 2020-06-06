# Bulk Payments

A Bulk Payment represents a group of payments to contacts that are registered in Scale. Grouping payments in this way condenses many complex payment processes into a single approval and execution step.

Bulk Payments consist of multiple payment items, where each payment item represents a transfer to a contact with the amount and currency of your choice.

Bulk Payments can require approval by designated individuals before being able to be executed. Once approved, users with execution permissions can authorise the payment to be sent, providing Open Banking based payment authorisation with your connected account as necessary.

Funds are sent via Open Banking to a Scale wallet associated with your account, which in turn disburses funds according to the configuration provided in the Bulk Payment.

### Usage

1. Prepare a Bulk Payment object
2. \(Optional\) Add and modify line items
3. Submit a Bulk Payment for approval
4. Approve a Bulk Payment
5. Execute the Bulk Payment by initiating an Open Banking payment
6. Confirm the results of the Bulk Payment

## BulkPayment

### Attributes

| Field | Description | Format |
| :--- | :--- | :--- |
| bulkPaymentId | ID of this bulk payment | string |
| items | Array of line items which belong to this bulk payment. | [BulkPaymentItem\[\]](bulk-payments.md#bulkpaymentitem) |
| createdAt | UTC timestamp of when the bulk payment was created. | ISO 8601 date |
| status | Current status of the bulk payment. | [PaymentStatus](bulk-payments.md#payment-status) |
| approvers | List of user IDs responsible for approving this payment. | string\[\] |
| name | Name of the bulk payment | string |

#### Payment Status

| Value | Description |
| :--- | :--- |
| draft | The bulk payment is editable and has had no action taken on it. |
| submitted | The bulk payment has been submitted for approval and is no longer editable. |
| approved | The bulk payment has been approved and is ready to be executed. |
| paid | The bulk payment has been executed. |

## API Reference

{% api-method method="post" host="https://api.helloscale.co" path="/v1/bulk-payments/" %}
{% api-method-summary %}
Create Bulk Payment
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="items" type="array" required=false %}
Array of BulkPaymentItems to seed the Bulk Payment.
{% endapi-method-parameter %}

{% api-method-parameter name="approvers" type="array" required=true %}
Array of user IDs who can approve this payment.
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
The name of the Bulk Payment
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Invalid approvers
{% endapi-method-response-example-description %}

```javascript
{
    "error": "approver not found",
    "details": "e7fe5eaa-22a4-4752-8177-7321585e952c"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.helloscale.co" path="/v1/bulk-payments/:bulkPaymentId" %}
{% api-method-summary %}
Retrieve Bulk Payment
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="bulkPaymentId" type="string" required=true %}
ID of the Bulk Payment.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "approvers": [
        "5853cda5-1013-495c-92d7-9b978a903fae"
    ],
    "bulkPaymentId": "60e47218-6e0c-40b8-b3d3-66421a82af59",
    "createdAt": "2020-04-15T15:25:24+0000"
    "items": [
        {
            "bulkPaymentItemId": "1fbd178d-fe9e-4622-8634-fbd39370dad1",
            "recipientContactId": "05d88b15-2075-4cbe-8473-57111d745769",
            "currency": "GBP",
            "amount": 45124
        }
    ],
    "name": "April-W3",
    "status": "draft"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Bulk Payment ID not found.
{% endapi-method-response-example-description %}

```javascript
{
    "error": "not found"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.helloscale.co" path="/v1/bulk-payments/" %}
{% api-method-summary %}
List bulk payments
{% endapi-method-summary %}

{% api-method-description %}
Returns a summary list of bulk payments already sent to third parties. Bulk payments are returned in sorted order, with the most recently created bulk payments appearing first.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="to" type="string" required=false %}
Filter results to be before a specified date.
{% endapi-method-parameter %}

{% api-method-parameter name="status" type="string" required=false %}
Filter results by status.
{% endapi-method-parameter %}

{% api-method-parameter name="from" type="string" required=false %}
Filter results to be after a specified date.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "count": 2,
    "items": [
        {
            "approvers": [
                "5853cda5-1013-495c-92d7-9b978a903fae"
            ],
            "bulkPaymentId": "60e47218-6e0c-40b8-b3d3-66421a82af59",
            "createdAt": "2020-04-15T15:25:24+0000"
            "itemCount": 1,
            "name": "April-W3",
            "status": "draft"
        },
        {
            "approvers": [
                "5853cda5-1013-495c-92d7-9b978a903fae"
            ],
            "bulkPaymentId": "87537bb1-814c-437a-a473-f80ceeaa3bac",
            "createdAt": "2020-04-8T12:16:52+0000"
            "itemCount": 3,
            "name": "April-W2",
            "status": "paid"
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://api.helloscale.co" path="/v1/bulk-payments/:bulkPaymentId" %}
{% api-method-summary %}
Delete Bulk Payment
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="bulkPaymentId" type="string" required=true %}
ID of the Bulk Payment.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.helloscale.co" path="/v1/bulk-payments/:bulkPaymentId/submit" %}
{% api-method-summary %}
Submit for Approval
{% endapi-method-summary %}

{% api-method-description %}
Submits the Bulk Payment for approve and locks edits.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="bulkPaymentId" type="string" required=false %}
ID of the Bulk Payment.
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

## BulkPaymentItem

### Attributes

| Field | Description | Format |
| :--- | :--- | :--- |
| bulkPaymentItemId | ID for this line item. | string |
| recipientContactId | Contact ID of the recipient. | string |
| currency | Currency of the payment | string - ISO 4217 currency |
| amount | Amount to send this recipient. | number |

{% api-method method="post" host="https://api.helloscale.co" path="/v1/bulk-payments/:bulkPaymentId" %}
{% api-method-summary %}
Add item to bulk payment
{% endapi-method-summary %}

{% api-method-description %}
Add a BulkPaymentItem to a specified BulkPayment
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="bulkPaymentId" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="amount" type="number" required=true %}
Amount to send recipient.
{% endapi-method-parameter %}

{% api-method-parameter name="currency" type="string" required=true %}
ISO 4217 currency
{% endapi-method-parameter %}

{% api-method-parameter name="recipientContactId" type="string" required=true %}
ID of the contact recipient.
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

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

{% tabs %}
{% tab title="Contact not found" %}
```javascript
{
    "error": "contact not found",
    "details": "0d6211b8-a81d-4354-8caf-9c3c5a758e5f"
}
```
{% endtab %}

{% tab title="Bad currency" %}
```javascript
{
    "error": "bad currency",
    "details": "OMG"
}
```
{% endtab %}
{% endtabs %}
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://api.helloscale.co" path="/v1/bulk-payments/:bulkPaymentId/:bulkPaymentItemId" %}
{% api-method-summary %}
Delete item from bulk payment
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="bulkPaymentItemId" type="string" required=true %}
ID of the Bulk Payment Item.
{% endapi-method-parameter %}

{% api-method-parameter name="bulkPaymentId" type="string" required=true %}
ID of the Bulk Payment.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

