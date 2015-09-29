# API Documentation

## API Overview

The platform provides the following APIs:

[Transactions](/docs/rest/transactions) - provides read-only access to call transaction data.

[Network Integration](/docs/rest/network-integration) -
supports the replication and synchronization of advertiser, publisher and campaign data between partner platforms.

[Conversion Reporting](/docs/rest/conversion-reporting) -
provides the ability to report completed order information (or other conversion events) from a server back into the platform.

[RingPool](/docs/rest/ringpool) -
allocates a dynamic, trackable promo phone number from a RingPool.

[Bulk RingPool API](/docs/api-documentation/bulk-ringpool-api) -
allocates a dynamic, trackable promo phone number from a RingPool (designed to handle a high volume of requests per second).


The following table identifies the APIs available by account type and role:

<img src="https://invoca.uservoice.com/assets/74048204/API%20Graphic.png" style="font-family: sans-serif; font-size: 14.44444465637207px; font-style: normal; font-variant: normal;">


The Transactions API and Network Integration API are accessible using the API credentials generated on the platform. See [Manage API Credentials](/docs/api-documentation/manage-api-credentials) for more information.

The Conversion Reporting API is accessible using credentials provided by Invoca. Contact [questions@invoca.com](mailto:questions@invoca.com) to request Conversion Reporting API credentials.

The RingPool and Bulk RingPool APIs are accessible using the API keys provided in the RingPool wizard. (Note: the Bulk RingPool API is only available after being enabled by Customer Success. Contact [questions@invoca.com](mailto:questions@invoca.com) to request the Bulk RingPool API.)

The RingPool wizard includes a section showing the correct API URL for your organization:
<img src="https://lh6.googleusercontent.com/bPAQy29TdQ_Pljxyv5gh520cLnWHWNWUXyU8_GrN52yLNOdkKlWZPzFLCOKgdE-IejM3XDdJGZyJtQ8EMprqwUSImYfuffWuXMGQAYAFzEbMOxt7Ggtp59Q96AOf6a3BeQ" width="544px;" height="191px;" style="border-style: none;" alt="RP_API.png">

## Manage API Credentials

Invoca provides the ability for users to self-generate API access tokens for the Transactions API and the Network Integration
API (the Network Integration API is available to Network super users only).


### Create An API Token
<hr>

To create an API token:

1. From any page, choose the Tools gear, ﻿API Credentials.

   * ![](https://invoca.uservoice.com/assets/74025540/gear-icon.png)

2. On the Manage Credentials page, click ﻿﻿"Create New API Token".
3. Enter a description and click Save.

Note: It is recommended to provide a description that identifies the intended API type and usage for this token.


### Delete an API Token
<hr>

To delete or remove an API token from your organization:

1.   From any page, choose the Tools gear, ﻿API Credentials.
     * ![](https://invoca.uservoice.com/assets/74025540/gear-icon.png)
2.   On the Manage Credentials page, click the delete icon associated with the API token to delete it.


### API Guidelines
<hr>

* Users should generate their own API tokens. Tokens should be treated like passwords and not be emailed or transmitted over other insecure mediums, nor should they be stored in a source code repository.

* As a network user, you should not generate a token on behalf of Advertisers or Publishers, as tokens inherit the privileges of the user generating it.

* These access tokens are Oauth compliant.

* Invoca does not use OAuth refresh tokens.
{:.bullets}

## Network Integration

### Coming soon to a documentation page near you

## Conversion Reporting

### Eh I'm sure the subsections cover it well enough

## Conversion Reporting Pixel

A conversion pixel is placed on an advertiser's web page to report a conversion event that triggers payouts on the platform.  Typically, the pixel is placed on a shopping cart confirmation page or lead form thank you page.

<h3>
To report conversions using a pixel
</h3>
---
Verify that you have received the Conversion Reporting credentials email from support, including your Upload Email Address and Conversion Reporting ID.

For "Publisher Promotion" or Fixed Price "Bundled" Campaigns, view your Conversion Reporting credentials in the Campaign Summary tab, Integration section.

![](https://i.embed.ly/1/image?url=http%3A%2F%2Fi40.photobucket.com%2Falbums%2Fe238%2Fnasteele%2FInvoca%2520screenshots%2Fcr6_zpsbc607ab1.png&key=afea23f29e5a4f63bd166897e3dc72df)

<b>
Advantages:
</b>

  * Easy to integrate - simply add a 1x1 image tag with a specific URL.
  {:.bullets}

<b>
Disadvantages:
</b>

  * Requires that the visitor came to the site via an Invoca tracking link.
  * Pixel must be hit in a browser (it can not be done in a redirect, or from a background process).
  {:.bullets}

<h3>
Pixel URL
</h3>
---
`http://api.invoca.net/pixels/conversion/ADVERTISER_ID.gif?SALES_PARAMS`

For "Publisher Promotion" or Fixed Price "Bundled" Campaigns, the Advertiser_ID is listed on the Campaign Summary, Integration panel.

For all other campaign types, the Advertiser_ID is accessible from the ﻿Advertiser Home Page. ﻿Note the address b in the ar  the browswer in t he rD follows /as/ in the URL.

![](https://i.embed.ly/1/image?url=http%3A%2F%2Fi40.photobucket.com%2Falbums%2Fe238%2Fnasteele%2FInvoca%2520screenshots%2Fusc2_zps2a8a907a.png&key=afea23f29e5a4f63bd166897e3dc72df)

The ﻿Sales_Params ﻿available are documented in Conversion Reporting API under the "Shared Parameters for Sales and Web Conversions" section.

The advertiser campaign and publisher are determined based on what link drove the traffic to the advertiser's site, and are calculated automatically.

We support tying a web pixel to a subsequent server-side conversion. In order to tie the conversions together, you must have passed a reference_id to the original web pixel, and also pass that same reference_id to the Conversion Reporting API.

<h3>
Example URLs
</h3>
---
(assuming that Advertiser_ID = 1)
Most basic URL, just reports that a conversion occurred, but without a sale or any additional data:

  `http://api.invoca.net/pixels/conversion/1.gif`

Report a conversion where a $10 sale occurred:

  `http://api.invoca.net/pixels/conversion/1.gif?sale_amount=10`

Report a conversion with specific sales data:

  `http://api.invoca.net/pixels/conversion/1.gif?sale_amount=10&reason_code=renewal&sku_list[]=34657`

Report a conversion with multiple sku items:

  `http://api.invoca.net/pixels/conversion/1.gif?sale_amount=10&sku_list[]=dog&sku_list[]=cat`

Report a conversion with unique identifier to track later (in the Transactions API or future pixel-based conversions):

  `http://api.invoca.net/pixels/conversion/1.gif?sale_amount=0&reason_code=new_signup&reference_id=2012994455`

Update a conversion that was reported earlier:

  `http://api.invoca.net/pixels/conversion/1.gif?sale_amount=95.0&reason_code=confirmed_order&parent_reference_id=2012994455`

<br>

*Web pixel example*

~~~
<!DOCTYPE html>

<html>
  <head>
    <title>Order Confirmation</title>
  </head>

  <body>
    <img src="PIXEL_URL" width="1" height="1">

    Your order has been placed.
  </body>
</html>
~~~
{:.prettyprint .theme-github}

<h3>
Old version (before December 2012)
</h3>
---

This version is only supported for existing installations.  Conversions generated by this version can not be tied to future server-based conversions.

`http://api.invoca.net/tracked_actions/web_sale/ADVERTISER_ID?SALES_PARAMS`

The following sales params are supported:

* `amount` (sale amount)

* `currency` (sale currency, defaults to USD)

* `external_data` (string, shown in reports)
{:.bullets}

## Conversion Reporting Email

Conversion events can be reported using an email message with an attached CSV file.

<h3>
To report conversions using email
</h3>
---

Verify that you have received the Conversion Reporting credentials email from support, including your Upload Email Address and Conversion Reporting ID.

For "Publisher Promotion" or Fixed Price "Bundled" Campaigns, view Conversion Reporting credentials in the Campaign Summary tab, Integration section.

![](https://i.embed.ly/1/image?url=http%3A%2F%2Fi40.photobucket.com%2Falbums%2Fe238%2Fnasteele%2FInvoca%2520screenshots%2Fcr6_zpsbc607ab1.png&key=afea23f29e5a4f63bd166897e3dc72df)

Note or copy the Upload Email Address.

<h3>
Conversion Report Message Format:
</h3>
---

Conversion Reporting sent via email must be in a CSV (comma-separated values) file format with the sale reporting parameters as the column headers and each sale transaction on a single row. Attach the CSV file to an empty message and send it to the Upload Email Address.

Two example files are shown at the bottom of this article. Feel free to contact your Program Manager or [questions@invoca.com](mailto:questions@invoca.com) for a skeleton file that suits your needs. Removing un-used columns reduces mistakes, so trim the skeleton file to include only the parameters you need.

<h3>
For Call Based Conversions
</h3>
---

Only one parameter is absolutely required: the start time of the call. Any entry missing the start time of the call causes an error and is not processed. Including the calling phone number is also recommended.

* <b>Start time</b>

* Start time is used to associate the sales transaction to a call. There are two types of time parameters: start_time and start_time_t.  Start_time_t is in the universal "Unix time_t" format while start_time is in human-readable format: YYYY/MM/DD HH:MM:SS. Note that skeleton files have an example of this format but be sure to look at them in a plain text editor like Notepad.  If you open the file with Excel, Excel reformats that column to match its preference!

* Start_time_t has precedence over start_time so if you are planning to just use start_time, remove the start_time_t column from the skeleton file.

* Best practices encourage using the 10-digit start_time_t.

* If you are using the start_time parameter, contact us to set the time zone of your sale reporting at [questions@invoca.com](mailto:questions@invoca.com).

For more information on possible parameters and how the matching call is found, see [Conversion Reporting API](/docs/rest/conversion-reporting).

<h3>
For Web Based Conversions
</h3>
---

The affiliate or publisher ID and advertiser campaign ID are required.

For more information on possible parameters and how the matching call is found, see ﻿[Conversion Reporting API](/docs/rest/conversion-reporting).

<h3>
Reply Message
</h3>
---

Conversion Reporting emails are processed on a nightly basis and a reply message is sent once the task is completed. The reply message includes the number of conversions processed, the number of conversions that did not match up with a transaction and the number of errors. For each error encountered, the row number, the content of that row and the error it caused is returned. Please note that only up to 10 errors per batch are allowed before processing is stopped.

![](https://i.embed.ly/1/image?url=http%3A%2F%2Fi40.photobucket.com%2Falbums%2Fe238%2Fnasteele%2FInvoca%2520screenshots%2F06c39c20-348a-4fc8-ac8c-36affc228fbe_zps626d230e.jpg&key=afea23f29e5a4f63bd166897e3dc72df)

<h3>
Examples:
</h3>
---

1. Conversions reported include the call Start Time in Human Readable Time Format, the Calling Phone Number and the Reason Code.

   ![](https://i.embed.ly/1/image?url=http%3A%2F%2Fi40.photobucket.com%2Falbums%2Fe238%2Fnasteele%2FInvoca%2520screenshots%2Fcr_email3_zps689c6b82.jpg&key=afea23f29e5a4f63bd166897e3dc72df)


2. Conversions reported include the call Start Time in Unix Time Format, the calling phone number and the Sku List.

   ![](https://i.embed.ly/1/image?url=http%3A%2F%2Fi40.photobucket.com%2Falbums%2Fe238%2Fnasteele%2FInvoca%2520screenshots%2Fcr_email2_zpsf3b62472.jpg&key=afea23f29e5a4f63bd166897e3dc72df)


<h3>
Idempotency:
</h3>
---

Sales are considered unique using a combination of start_time_t + SKU_list + reason code. Reported conversions duplicate keys (same call, sku list, reason code) behave as follows:

* If the values passed are unchanged, the reported conversion remains unchanged and is not duplicated.
* If different values are passed, the original conversion is  updated with the new values.
{:.bullets}

Reported conversions with unique keys always create new conversion transactions.

## Transactions

## Ringpool

## Bulk Ringpool API
Before using the Bulk RingPool API, contact [questions@invoca.com](mailto:questions@invoca.com) to enable the Bulk RingPool API feature. It is recommended that before you enable the feature on your production platform, testing occurs on a demo or test platform.

### Overview
<hr>

The Bulk RingPool API is designed to efficiently handle a high volume of requests per second. A persistent connection is strongly recommended.

The Bulk RingPool API can be enabled on the Network, Advertiser, or Publisher level. Note that once enabled, all new or edited RingPools are served by the Bulk RingPool API and not the RingPool API.  Therefore, if the Bulk RingPool API is enabled for your organization,
 attempting to access a RingPool with the RingPool API results in an error.

Finally, also note that only the custom RingPool type is supported by the Bulk RingPool API.

<b>
Example API URL:
</b>

`POST ﻿https://pnapi.invoca.net/api/2013-07-01/bulk.json`


### Request Body
<hr>

The JSON POST body of the request has a top level key "request" which maps to an array of hashes, where each hash contains a RingPool API URL. The array must contain at least one entry. The requests follow a similar format to the RingPool API, which can be found here.

Each hash in the array must contain a key/value pair with a key of "api_suffix". The value must be the suffix of the RingPool API URL after /api/\<date>.

At least one RingPool parameter must be present in each allocation request, even if the value is an empty string.

Each element may also include a key/value pair with a key of "request_id". If provided, it is echoed in the response for context. This parameter is optional and does not have to be unique across the hashes.

Individual responses and request IDs are returned in the same order as the requests.

Below is an example of the JSON request body:


~~~ json
{
 "requests":[
  {"api_suffix":"<RING_POOL_ID>/allocate_number.json?ring_pool_key=<RING_POOL_KEY>&m1=autos&m2=ford","request_id":"193C5F"},
  {"api_suffix":"<RING_POOL_ID>/allocate_number.json?ring_pool_key=<RING_POOL_KEY>&m1=antiques","request_id":"58CD4F"},
  {"api_suffix":"<RING_POOL_ID>/allocate_number.json?ring_pool_key=<RING_POOL_KEY>&m1=electronics","request_id":"E3901B"}
 ]
}
~~~
{: .prettyprint .theme-github}

### Response Body
<hr>

The response format is in <b>JSON</b>.

Below is an example response (whitespace added for clarity):

~~~ json
 {
 "responses":[
  {"request_id":"193C5F","promo_number_formatted":"888-390-6665","promo_number":"8883906665","tracking_url":"http://ringrevenue.com/c/1/14-11-109?us=http%3A%2F%2Fwww2.ringrevenue.com.com%2Fdemo%2F8x8_staging.html%3Fsid%3D8883906665%26PPCPN%3D8883906665"},
  {"request_id":"58CD4F","promo_number_formatted":"877-455-1120","promo_number":"8774551120","tracking_url":"http://ringringrevenue.com/c/1/19-99-210?us=http%3A%2F%2Fwww2.ringrevenue.com%2Fdemo%2F8x8_staging.html%3Fsid%3D8774551120%26PPCPN%3D8774551120"},
  {"request_id":"E3901B","promo_number_formatted":"866-971-5703","promo_number":"8669715703","tracking_url":"http://ringringrevenue.com/c/1/38-240-19?us=http%3A%2F%2Fwww2.ringrevenue.com%2Fdemo%2F8x8_staging.html%3Fsid%3D8669715703%26PPCPN%3D8669715703","overflow":true}
 ]
}
~~~
{: .prettyprint .theme-github}

Note the last response above has `"overflow":true`.  This indicates that the number returned is the overflow number for that RingPool.  To simplify the normal case when the number is not overflow, the key-value pair is omitted when the value would be `false`.

Additionally, Bulk API responses return the total server processing (this does not include transit) time for the request in the header under the key “processing-time”, and is reported in milliseconds.

### Errors
<hr>

The Bulk RingPool API clearly identifies errors when a request can not be processed. For example, when the parameters are incorrect, an error response will be returned for that row in the response as shown below:

~~~ json
{
 "responses":[
{"request_id":"193C5F","promo_number_formatted":"888-390-6665","promo_number":"8883906665","tracking_url":"http://ringrevenue.com/c/1/14-11-109?us=http%3A%2F%2Fwww2.ringrevenue.com.com%2Fdemo%2F8x8_staging.html%3Fsid%3D8883906665%26PPCPN%3D8883906665"},

{"request_id":"58CD4F","error_class":"InvalidKey","message":"API Key 'A329F4DC002168' is not valid for resource '1'"},

{"request_id":"E3901B","promo_number_formatted":"866-971-5703","promo_number":"8669715703","tracking_url":"http://ringringrevenue.com/c/1/38-240-19?us=http%3A%2F%2Fwww2.ringrevenue.com%2Fdemo%2F8x8_staging.html%3Fsid%3D8669715703%26PPCPN%3D8669715703"}
]
}
~~~
{: .prettyprint .theme-github}

As another example, the following exception occurs when attempting to allocate a number with the RingPool API against a RingPool that has been set up to use the Bulk RingPool API:

~~~ json
{
    “errors”:
    {
        “invalid_data”:”Numbers are automatically allocated by the
        PNAPI server”,”class”:”OnlyBulkNumberAllocationAllowed”
    }
}
~~~
{: .prettyprint .theme-github}


If a system error occurs, an InternalServiceError will be returned with an integer error handle.

Contact [questions@invoca.com](mailto:questions@invoca.com) to determine the root cause of such an error.

## Call Outcomes API


