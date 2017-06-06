---
seo:
  title: List Upload Troubleshooting
  description: Having trouble uploading a list in Marketing Campaigns? Learn common solutions here...
  keywords: marketing, campaigns, csv, upload, contacts, format, list, header, error, UTF-8
title: List Upload Troubleshooting
weight: 0
layout: page
navigation:
  show: true
---

{% info %}
In the case of an error, we will often send an email to you in the case of a list upload failure. Please check the email from SendGrid that outlines the results of your CSV upload, including a downloadable error report.

![]({{root_url}}/images/listupload_error.png)

{% endinfo %}

{% anchor h2 %} General Formatting Rules {% endanchor h2 %}


{% anchor h3 %} Character Encoding {% endanchor h3 %}

If your contacts list has non-English characters, please make sure that you're using a CSV file that is UTF-8 encoded.


{% anchor h3 %} Not all addresses populate in UI {% endanchor h3 %}

SendGrid will remove duplicate and invalid email addresses (including email addresses with special characters) from your list during upload, so the number of contacts can potentially change between your CSV and your Marketing Campaigns list.

{% anchor h3 %} Text that looks like a number {% endanchor h3 %}

Make sure that you don’t have text fields that look like numbers. Text that look like numbers are those that contain punctuation characters like a dash, underscore, parenthesis, or multiple dots.

```
- US Zip Code: 80202-1713
- Phone numbers: “(555) 555-5555” or “555.555.5555”
- Monetary Values with the currency indicator such as $3.50 or €5.73
```
{% anchor h3 %} CSV Headers can be blank {% anchor h3 %}

- Header fields can be blank in your CSV, but must be named and have their type defined later during the upload process.

![]({{root_url}}/images/listupload_5.png)

{% anchor h3 %} Date formatting {% endanchor h3 %}

Make sure that your dates are properly formatted in your CSV. If you created your CSV with Excel, you may need to force the date format before exporting to CSV. The date format needs to be one of the following: `MM/DD/YYYY, MM/D/YYYY, M/D/YYYY, or M/DD/YYYY`

{% anchor h3 %} Custom fields in your CSV but not your account {% endanchor h3 %}

If you include a column in your CSV that is for a custom field not defined in your account, then the CSV will be rejected. We are currently working to add a feature that will let you set up custom fields as a step during the upload process.

{% anchor h3 %} I have more than one of the same email in my database {% anchor h3 %}

With SendGrid’s Marketing Campaigns feature, the unique identifier is the email address. So, if you upload the same email address multiple times, the custom field data associated with that email will be updated with each upload to the most recently uploaded/updated information. This feature helps prevent you from accidentally emailing the user after they have unsubscribed.

What you may want to do is add logic to set a custom field, based on the reason why you have duplicate emails in your system (for example multiple product lines) and then segment your user to be in lists based on those [Custom Fields](https://sendgrid.com/docs/User_Guide/Marketing_Campaigns/custom_fields.html).


{% anchor h2 %} Specific Upload Errors {% endanchor h2 %}

{% anchor h3 %} We were unable to detect an email column in the CSV file headers. The email column must always have a header of "email" {% endanchor h3 %}

- If there is a header labeled “email”, try moving it to the column A, so it is the first header in your list.
- Your CSV _must_ include an email header.

![]({{root_url}}/images/listupload_1.png)

{% anchor h3 %} Some of your custom fields have not been selected {% endanchor h3 %}

- If you have worked with your CSV multiple times, or have made some adjustments to the data, there can be some hidden characters in the CSV file.
- A common fix for this error would be to select all and copy your data to a new CSV spreadsheet. This should remove any hidden characters.

![]({{root_url}}/images/listupload_2.png)

{% anchor h3 %} Each custom field can only be applied to a column once. Please check your columns and try again {% endanchor h3 %}

- Check your CSV for duplicate fields, especially fields that have matching information as your “email”, “first_name” and “last_name” fields. These are reserved field names, and cannot be edited.
- For example, if you have a “Name” field, it may conflict with your “first_name” reserved field.

![]({{root_url}}/images/listupload_3.png)

{% anchor h3 %} We were unable to detect any headers in your CSV file {% endanchor h3 %}

- Please be sure to include headers at the top of each column. The “email” header is required for all CSV uploads. Header fields can be blank in your CSV, but must be defined later during the upload process.

![]({{root_url}}/images/listupload_4.png)

{% anchor h3 %} Float type conversion error {% endanchor h3 %}

- Dashes or decimal places past the hundredth place need to be categorized as text_fields (-100, 123.123 are text fields, 100, 12.12 can be number fields).
Number fields can include monetary values without the currency symbols. For example, 19.95 would be a number field, and $19.95 including the ($) would be a text field.
- As you are uploading your CSV, make sure you select the correct fields for your Field type.

![]({{root_url}}/images/listupload_table.png)
