Advertiser Campaigns
====================
<hr>

Advertiser Campaigns can be managed using the Network API. In addition to create, update, and show operations, this interface provides additional endpoints including go_live, archive, and quick_stats.

Note that the `<advertiser_id_from_network>` and `<advertiser_campaign_id_from_network>` are the network’s id for those objects, not Invoca’s.

`/api/2015-05-01/<network_id>/advertisers/<advertiser_id_from_network>/advertiser_campaigns/<advertiser_campaign_id_from_network>.json`

We support passing back current_terms and future_terms on campaigns. The current properties of the campaign are reflected in current_terms. All changes to the campaign are staged in future_terms. Once the campaign goes live, future_terms transition over to current_terms.

You can set budgets on your campaign. There are two budget types, budget_cap_alert which is based on commissions, and call_cap_alert, which is based on the number of calls. These budget activities are only applicable for AffiliateEnabled campaigns (Known in the platform as a “Publisher Promotion” Campaign Type.)

You are not allowed to delete campaigns.

<table>
<tr><th>Property</th><th>Type</th><th>Value</th></tr>
<tr><td>name</td><td>string</td><td>Campaign name.</td></tr>
<tr><td>campaign_type</td><td>string</td><td>2 Campaign Types Supported: “AffiliateEnabled” ‐ Advertiser Campaign that allows Affiliates to promote it. Includes Payin and Payouts for qualified Calls. “DirectOnly” ‐ Advertiser Campaign used for internal marketing. No ability to promote via Affiliates or setup Payin and Payouts for Calls.</td></tr>
<tr><td>description</td><td>string</td><td>Campaign Description.</td></tr>
<tr><td>url</td><td>string</td><td>Click URL Template.</td></tr>
<tr><td>timezone</td><td>string</td><td>Supported Time Zones: “Pacific Time (US & Canada)”, “Mountain Time (US & Canada)”, “Central Time (US & Canada)”, “Eastern Time (US & Canada)”, “London”, “UTC”.</td></tr>
<tr><td>operating_24_7</td><td>boolean</td><td></td></tr>
<tr><td>affiliate_payout</td><td></td></tr>
<tr><td>currency</td><td>string</td><td>USD, GBP, EUR.</td></tr>
<tr><td>policies</td><td></td></tr>
<tr><td>amount</td><td>decimal</td><td>Payout Amount.</td></tr>
<tr><td>condition</td><td>string</td><td>Condition options depend on the following Campaign Setup items being in place: Duration (seconds/minutes) and (greater than, greater than or equal to, less than, less than or equal to, equal to), Connect Duration (seconds/minutes) and (greater than, greater than or equal to, less than, less than or equal to, equal to), Repeat, In Region (specified across multiple Regions), During Hours, Key Press, Is Mobile, Is Landline, Send SMS All may be grouped with logic operators (AND/OR/NOT).</td></tr>
<tr><td>type</td><td>string</td><td>One of: Base, Bonus.</td></tr>
<tr><td>advertiser_payin</td><td></td></tr>
<tr><td>currency</td><td>string</td><td>Supported Currencies: ‐ USD, GBP, EUR.</td></tr>
<tr><td>policies</td><td></td></tr>
<tr><td>amount</td><td>integer</td><td>Advertiser Payin Amount.</td></tr>
<tr><td>condition</td><td>string</td><td>Condition options depend on the following Campaign Setup items being in place: Duration (seconds/minutes) and (greater than, greater than or equal to, less than, less than or equal to, equal to), Connect Duration (seconds/minutes) and (greater than, greater than or equal to, less than, less than or equal to, equal to), Repeat, In Region (specified across multiple Regions), During Hours, Key Press, Is Mobile, Is Landline, Send SMS. All may be grouped with logic operators (AND/OR/NOT).</td></tr>
<tr><td>type</td><td>string</td><td>One of: Base, Bonus.</td></tr>
<tr><td>hours</td><td></td></tr>
<tr><td>[day of week]_open (e.g. friday_open)</td><td>string</td><td>Open Hours. In seconds past midnight (e.g. 0 for midnight, 32400 for 9:00 AM).</td></tr>
<tr><td>[day of week]_close (e.g. friday_close)</td><td>string</td><td>Closed Hours. In seconds past midnight (e.g. 0 for midnight, 75600 for 9:00 PM).</td></tr>
<tr><td>[day of week]_closed (e.g. sunday_closed)</td><td>string</td><td>true, false, or null. Whether the business is closed that day of the week.</td></tr>
<tr><td>named_regions</td><td></td></tr>
<tr><td>name</td><td>string</td><td>Region Name.</td></tr>
<tr><td>regions</td></tr>
<tr><td>region_type</td><td>string</td><td>Region Type. Can be one of: Zone, City, State, Country.</td></tr>
<tr><td>value</td><td>string</td><td>Region Value, e.g. “Sacramento, CA”, or just “CA”.</td></tr>
<tr><td>ivr_tree</td><td>hash</td><td>See following Advertiser Campaign IVR Section.</td></tr>
<tr><td>budget_activities</td><td></td><td>Only applicable for AffiliateEnabled campaigns.</td></tr>
<tr><td>budget_cap_alert</td></tr>
<tr><td>reset_period</td><td>string(required)</td><td>Budget will reset based on this entry. One of: Daily, Weekly, Monthly, Quarterly, Ongoing.</td></tr>
<tr><td>starts_at</td><td>date (required)</td><td>Budget Start.</td></tr>
<tr><td>budget_currency</td><td>string(required)</td><td>Budget Currency.</td></tr>
<tr><td>time_zone</td><td>string (required)</td><td>Supported Time Zones: “Pacific Time (US & Canada)”, “Mountain Time (US & Canada)”, “Central Time (US & Canada)”, “Eastern Time (US & Canada)”, “London”, “UTC”.</td></tr>
<tr><td>budget_amount</td><td>decimal (required)</td><td>Budget Amount.</td></tr>
<tr><td>include_call_fees</td><td>boolean</td><td>True if you want call fees to be included in the budget.</td></tr>
<tr><td>call_cap_alert</td></tr>
<tr><td>reset_period</td><td>string (required)</td><td>Budget will reset based on this entry. One of: Daily, Weekly, Monthly, Quarterly, Ongoing.</td></tr>
<tr><td>starts_at</td><td>date (required)</td><td>Call Cap Start.</td></tr>
<tr><td>budget_currency</td><td>string (required)</td><td>Budget Currency.</td></tr>
<tr><td>time_zone</td><td>string (required)</td><td>Supported Time Zones: “Pacific Time (US & Canada)”, “Mountain Time (US & Canada)”, “Central Time (US & Canada)”, “Eastern Time (US & Canada)”, “UTC”.</td></tr>
<tr><td>budget_amount</td><td>decimal (required)</td><td>Budget Amount.</td></tr>
<tr><td>auto_approve</td><td>string</td><td>One of: All, None, Approved_Affiliates Default: None This controls if affiliates are automatically approved when applying to the campaign.</td></tr>
<tr><td>visibility</td><td>string</td><td>One of: All, None, Approved_Affiliates Default: All This controls the level of visibility publishers have when applying to campaigns.</td></tr>
<tr><td>expiration_date</td><td>string</td><td>date string (ex. ‘2015‐01‐01’). Read only.</td></tr>
<tr><td>default_creative_id_from_network</td><td>integer</td><td>Default Creative ID.</td></tr>
<tr><td>max_promo_numbers</td><td>integer</td><td>Maximum Promo Numbers.</td></tr>
</table>

### Advertiser Campaign IVRs

When creating an advertiser campaign, you need to provide some call flow logic through an IVR tree. Depending on the advertiser/campaign type (direct, bundled, etc) you may use the following node types:

Node Parameters and Usage

* => required parameter

<table>
<tr><th>Node Type</th><th>Parameters</th><th>Usage</th></tr>
<tr><td>Menu</td><td>\*prompt</td><td>Allows the caller to select from up to 9 choices (e.g. choosing a department, selecting a language, etc).</td></tr>
<tr><td>Connect</td><td>prompt   </td></tr>
<tr><td>&nbsp;</td><td>\*destination_phone_number</td><td>Forwards the call to a selected phone number after optionally reading a prompt.</td></tr>
<tr><td>&nbsp;</td><td>\*destination_country_code</td><td>&nbsp;</td></tr>
<tr><td>EndCall</td><td>prompt</td><td>Ends the call after optionally reading a prompt.</td></tr>
<tr><td>SmsPromo</td><td>\*prompt</td><td>Provide the option for a user to receive a text message with a special promotion.</td></tr>
<tr><td>&nbsp;</td><td>\*sms_promo_copy</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>sms_promo_delay</td><td>&nbsp;</td></tr>
<tr><td>&nbsp;</td><td>sms_promo_sender</td><td>&nbsp;</td></tr>
<tr><td>Condition</td><td>\*condition</td><td>If/else option for a call based on the qualities of the call/caller.</td></tr>
<tr><td>VerifyLocation</td><td>prompt</td><td>Prompt the caller to verify the guessed location or confirm through input. Useful if geographical data is important or useful in a condition node.</td></tr>
</table>

Node Details

## Get all campaigns for an Advertiser
GET `/advertiser_campaigns`

### Examples

Read all campaigns for Advertiser 2 id from network

Endpoint:

`https://invoca.net/api/2015-05-01/<network_id>/advertisers/2/advertiser_campaigns.json`

Response Body:
An array of campaigns are returned.

<hr>

## Get a campaign for an Advertiser
GET `/advertiser_campaigns/<advertiser_campaign_id>`

### Examples

Read Campaign 100 for Advertiser 2

Endpoint:
`https://invoca.net/api/2015-05-01/<network_id>/advertisers/2/advertiser_campaigns/100.json`

Response Body:
<pre><code>{
  "current_terms": {
    "description": "August promotion to sell post-season tickets at half price.",
    "timezone": "Pacific Time (US & Canada)",
    "visibility": "All",
    "created_at": "2015-05-13 07:45:08 -0800",
    "id": "215",
    "operating_24_7": false,
    "go_live_date": null,
    "default_creative_id_from_network": "222",
    "advertiser_payin": {
      "min": 7,
      "currency": "EUR",
      "pricing": "€7.00 per call if duration > 2 min 30 sec",
      "max": 7,
      "policies": [
        {
          "type": "Base",
          "currency": "EUR",
          "condition": "duration > 2 min 30 sec",
          "amount": 7
        }
      ],
      "range": "€7.00 per call"
    },
    "pricing_type": "Fixed",
    "ivr_tree": {
      "root": {
        "condition": "during_hours",
        "children": [
          {
            "destination_phone_number": "8004377950",
            "destination_country_code": "1",
            "prompt": "",
            "node_type": "Connect"
          },
          {
            "destination_phone_number": "8004377950",
            "destination_country_code": "1",
            "prompt": "",
            "node_type": "Connect"
          }
        ],
        "node_type": "Condition"
      },
      "record_calls": true
    },
    "auto_approve": "None",
    "expiration_date": null,
    "campaign_type": "AffiliateEnabled",
    "affiliate_payout": {
      "min": 4.5,
      "currency": "USD",
      "pricing": "Base: $4.50 per call Bonus: $2.75 per call if duration > 60",
      "max": 7.25,
      "policies": [
        {
          "type": "Base",
          "currency": "USD",
          "condition": "",
          "amount": 4.5
        },
        {
          "type": "Bonus",
          "currency": "USD",
          "condition": "duration > 60",
          "amount": 2.75
        }
      ],
      "range": "$4.50 - $7.25 per call"
    },
    "updated_at": "2015-05-13 07:45:08 -0800",
    "url": "http://www.nfltix.com/postseasonnow",
    "hours": {
      "saturday_open": 32400,
      "sunday_open": 32400,
      "monday_closed": false,
      "tuesday_open": 32400,
      "thursday_open": 32400,
      "friday_close": 75600,
      "sunday_close": 50999,
      "wednesday_closed": false,
      "thursday_closed": false,
      "tuesday_close": 75600,
      "friday_open": 32400,
      "saturday_closed": true,
      "sunday_closed": true,
      "tuesday_closed": true,
      "wednesday_close": 75600,
      "friday_closed": true,
      "monday_open": 32400,
      "saturday_close": 75600,
      "monday_close": 75600,
      "thursday_close": 75600,
      "wednesday_open": 32400
    },
    "named_regions": [
      {
        "regions": [
          {
            "region_type": "State",
            "value": "CA",
            "text": "TBD"
          },
          {
            "region_type": "State",
            "value": "OR",
            "text": "TBD"
          },
          {
            "region_type": "State",
            "value": "WA",
            "text": "TBD"
          }
        ],
        "name": "West Coast"
      },
      {
        "regions": [
          {
            "region_type": "State",
            "value": "NY",
            "text": "TBD"
          },
          {
            "region_type": "State",
            "value": "NJ",
            "text": "TBD"
          }
        ],
        "name": "East Coast"
      }
    ]
  },
  "future_terms": {
    "description": "August promotion to sell post-season tickets at half price.",
    "timezone": "Pacific Time (US & Canada)",
    "visibility": "All",
    "created_at": "2015-05-13 08:46:43 -0800",
    "id": "",
    "operating_24_7": false,
    "go_live_date": null,
    "default_creative_id_from_network": "123",
    "advertiser_payin": {
      "min": 7,
      "currency": "EUR",
      "pricing": "€7.00 per call if duration > 2 min 30 sec",
      "max": 7,
      "policies": [
        {
          "type": "Base",
          "currency": "EUR",
          "condition": "duration > 2 min 30 sec",
          "amount": 7
        }
      ],
      "range": "€7.00 per call"
    },
    "budget_activities": {
      "call_cap_alert": {
        "budget_amount": 200.0,
        "budget_currency": "USD",
        "reset_period": "Ongoing",
        "start_at": "2014-04-17T00:00:00-07:00",
        "total_amount": 0.0,
        "time_zone": "Pacific Time (US & Canada)"
      },
      "budget_cap_alert": {
        "budget_amount": 100.0,
        "budget_currency": "USD",
        "reset_period": "Monthly",
        "start_at": "2014-04-01T00:00:00-07:00",
        "total_amount": 0.0,
        "time_zone": "Pacific Time (US & Canada)"
      },
      "pricing_type": "Fixed",
      "ivr_tree": {
        "root": {
          "condition": "during_hours",
          "children": [
            {
              "destination_phone_number": "8004377950",
              "destination_country_code": "1",
              "prompt": "",
              "node_type": "Connect"
            },
            {
              "destination_phone_number": "8004377950",
              "destination_country_code": "1",
              "prompt": "",
              "node_type": "Connect"
            }
          ],
          "node_type": "Condition"
        },
        "record_calls": true
      },
      "auto_approve": "None",
      "expiration_date": "2015-05-18T23:59:59-08:00",
      "campaign_type": "AffiliateEnabled",
      "affiliate_payout": {
        "min": 4.5,
        "currency": "USD",
        "pricing": "Base: $4.50 per call Bonus: $2.75 per call if duration > 60",
        "max": 7.25,
        "policies": [
          {
            "type": "Base",
            "currency": "USD",
            "condition": "",
            "amount": 4.5
          },
          {
            "type": "Bonus",
            "currency": "USD",
            "condition": "duration > 60",
            "amount": 2.75
          }
        ],
        "range": "$4.50 - $7.25 per call"
      },
      "updated_at": "2015-05-13 08:46:43 -0800",
      "url": "http://www.nfltix.com/postseasonnow",
      "hours": {
        "saturday_open": 32400,
        "sunday_open": 32400,
        "monday_closed": false,
        "tuesday_open": 32400,
        "thursday_open": 32400,
        "friday_close": 75600,
        "sunday_close": 50999,
        "wednesday_closed": false,
        "thursday_closed": false,
        "tuesday_close": 75600,
        "friday_open": 32400,
        "saturday_closed": true,
        "sunday_closed": true,
        "tuesday_closed": true,
        "wednesday_close": 75600,
        "friday_closed": true,
        "monday_open": 32400,
        "saturday_close": 75600,
        "monday_close": 75600,
        "thursday_close": 75600,
        "wednesday_open": 32400
      },
      "named_regions": [
        {
          "regions": [
            {
              "region_type": "State",
              "value": "CA",
              "text": "TBD"
            },
            {
              "region_type": "State",
              "value": "OR",
              "text": "TBD"
            },
            {
              "region_type": "State",
              "value": "WA",
              "text": "TBD"
            }
          ],
          "name": "West Coast"
        },
        {
          "regions": [
            {
              "region_type": "State",
              "value": "NY",
              "text": "TBD"
            },
            {
              "region_type": "State",
              "value": "NJ",
              "text": "TBD"
            }
          ],
          "name": "East Coast"
        }
      ]
    },
    "status": "Entry",
    "name": "PostSeason Promotion 11 fJauFbSEGHKw8ADEGv",
    "max_promo_numbers": 10
  }
}</pre></code>

<hr>

## Create an Advertiser Campaign
POST `/advertiser_campaigns/<advertiser_campaign_id>`

### Examples

Example POST to non‐existing Advertiser Campaign fJauFbSEGHKw8ADEGv under Advertiser cFUyYnFHyiYA42TrpM in the Demo Network.

POST
`https://demo.invoca.net/api/2015-05-01/advertisers/cFUyYnFHyiYA42TrpM/advertiser_campaigns/fJauFbSEGHKw8ADEGv.json`

With an existing advertiser, the IVR tree may be updated independently of other attributes. Below is a curl command that only needs network API credentials, a network id and an advertiser id. This will create an advertiser campaign with id 445566. The campaign id may be changed freely.

Endpoint:
`https://demo.invoca.net/api/2015-05-01/advertisers/cFUyYnFHyiYA42TrpM/advertiser_campaigns/fJauFbSEGHKw8ADEGv.json`

<pre><code>curl­ -XPOST­ -H "Content­Type: application/json"­ -u 'login:pass'
'https://vanity.invoca.net/api/2015-05-01/advertisers/advertiser_id/advertiser_campaigns/445566.json' \
-d '
{
  "hours": {
    "tuesday_close": 61200,
    "wednesday_close": 61200,
    "saturday_open": 28800,
    "wednesday_closed": false,
    "friday_open": 28800,
    "thursday_close": 61200,
    "thursday_closed": false,
    "friday_close": 61200,
    "monday_close": 61200,
    "wednesday_open": 28800,
    "sunday_open": 28800,
    "thursday_open": 28800,
    "friday_closed": false,
    "monday_open": 28800,
    "tuesday_closed": false,
    "monday_closed": false,
    "saturday_close": 61200,
    "saturday_closed": false,
    "sunday_close": 61200,
    "sunday_closed": false,
    "tuesday_open": 28800
  },
  "name": "NFLCampaign",
  "timezone": "PacificTime(US&Canada)",
  "description": "Augustpromotion tosellpost­seasonticketsathalf price.",
  "ivr_tree": {
    "root": {
      "children": [
      ],
      "condition": "",
      "node_type": "Connect",
      "destination_phone_number": "8052844300",
      "destination_country_code": "1"
    },
    "record_calls": true
  },
  "named_regions": [
    {
      "name": "WestCoast",
      "regions": [
        {
          "value": "CA",
          "region_type": "State"
        },
        {
          "value": "OR",
          "region_type": "State"
        },
        {
          "value": "WA",
          "region_type": "State"
        }
      ]
    },
    {
      "name": "EastCoast",
      "regions": [
        {
          "value": "NY",
          "region_type": "State"
        },
        {
          "value": "NJ",
          "region_type": "State"
        }
      ]
    }
  ],
  "operating_24_7": false,
  "url": "http://www.nfltix.com/postseasonnow"
}
' -v</pre></code>

Create Campaign fJauFbSEGHKw8ADEGv for Advertiser cFUyYnFHyiYA42TrpM on network 1 (POST)

Endpoint:

`https://invoca.net/api/2015-05-01/<network_id>/advertisers/cFUyYnFHyiYA42TrpM/advertiser_campaigns/fJauFbSEGHKw8ADEGv.json`

Request Body

<pre><code>{
  "name": "PostSeason Promotion 11 fJauFbSEGHKw8ADEGv",
  "description": "August promotion to sell post-season tickets at half price.",
  "url": "http://www.nfltix.com/postseasonnow",
  "timezone": "Pacific Time (US & Canada)",
  "operating_24_7": false,
  "campaign_type": "AffiliateEnabled",
  "max_promo_numbers": 6,
  "default_creative_id_from_network": "111",
  "hours": {
    "friday_open": 32400,
    "wednesday_open": 32400,
    "sunday_close": 50999,
    "monday_open": 32400,
    "friday_close": 75600,
    "wednesday_close": 75600,
    "friday_closed": true,
    "thursday_open": 32400,
    "sunday_closed": true,
    "sunday_open": 32400,
    "saturday_open": 32400,
    "monday_closed": false,
    "thursday_close": 75600,
    "tuesday_closed": true,
    "tuesday_close": 75600,
    "tuesday_open": 32400,
    "saturday_closed": true,
    "saturday_close": 75600,
    "monday_close": 75600,
    "thursday_closed": false,
    "wednesday_closed": false
  },
  "named_regions": [
    {
      "name": "West Coast",
      "regions": [
        {
          "region_type": "State",
          "value": "CA"
        },
        {
          "region_type": "State",
          "value": "OR"
        },
        {
          "region_type": "State",
          "value": "WA"
        }
      ]
    },
    {
      "name": "East Coast",
      "regions": [
        {
          "region_type": "State",
          "value": "NY"
        },
        {
          "region_type": "State",
          "value": "NJ"
        }
      ]
    }
  ],
  "advertiser_payin": {
    "policies": [
      {
        "condition": "duration > 2 min 30 sec",
        "type": "Base",
        "currency": "USD",
        "amount": 7.0
      }
    ]
  },
  "affiliate_payout": {
    "policies": [
      {
        "condition": "",
        "amount": 4.5,
        "currency": "USD",
        "type": "Base"
      },
      {
        "condition": "duration > 60",
        "amount": 2.75,
        "currency": "USD",
        "type": "Bonus"
      }
    ]
  },
  "ivr_tree": {
    "record_calls": true,
    "root": {
      "node_type": "Condition",
      "condition": "during_hours",
      "children": [
        {
          "node_type": "Connect",
          "destination_phone_number": "8004377950",
          "destination_country_code": "1",
          "prompt": ""
        },
        {
          "node_type": "Connect",
          "destination_phone_number": "8004377950",
          "destination_country_code": "1",
          "prompt": ""
        }
      ]
    }
  }
}</pre></code>
