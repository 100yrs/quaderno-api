# Changelog

## API versions and changes

### 20210701 (Current version)

- **Breaking change**: `DELETE /invoices/INVOICE_ID` will cease to exist and return a `410 Gone`.
- **Breaking change**: `PUT /invoices/INVOICE_ID` will only allow modification of the parameters `notes`, `tag_list`, `custom_metadata` and all those related to the customer's address: `street_line_1`,`street_line_2`,`city`,`region`,`postal_code` and `country`.

### 20210316
* **Breaking change**: record pagination is no longer performed with a `page` parameter, but with a `created_before` parameter. See the [pagination documentation](#pagination) for more details.
* **Breaking change**: the existing [/taxes/calculate](#calculate-taxes) endpoint is deprecated in favour of the [/tax_rates/calculate](#calculate-a-tax-rate) endpoint.
* Adds a `Deprecation: true` header (as per <a href='https://tools.ietf.org/html/draft-ietf-httpapi-deprecation-header-01#section-2.1'>draft-ietf-httpapi-deprecation-header-01</a>) to responses using deprecated pagination, with a `Link` header linking to the updated documentation. After the deprecation dates, those endpoints will return a `410 Gone`.

### 20170914
* Added the accounts API
* Added the `related_document` to the credit object.
* Added `tax_1_transaction_type` and `tax_2_transaction_type` fields to the taxes attributes in the credit object.
* Added `transaction_type` fields to the document items attributes in the credit object.
* Added `kind`, `stripe_plan_id`, `paypal_interval_unit`, `paypal_interval_frequency` and `paypal_interval_duration` fields in the item object.
* Changed `number` field limit to 20 characters for `invoices`, `credits` and `estimates`.

### 20170628
* Return 429 (`too many requests`) instead of 503 (`service unavailable`) on rate limits.

### 20170418
* Added `custom_metadata` as an editable field.

### 20161108
* `country` is now returned as an attribute for `invoices`, `expenses`, `credits` and `estimates`.

### 20160614
* Amounts are now returned as cents instead being formatted as amount with currency symbol.
* Versions are no longer passed as part of the URL, instead they can be passed as an accept header.

### 20160602
* First version.
* Amounts are returned formatted as amount with currency symbol.
