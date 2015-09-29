# Basics

##Design Principles

###REST
<hr>

All interfaces use [REST](http://en.wikipedia.org/wiki/REST). This makes them easy to predict as they use HTTP and its existing
verbs to Create, Read, Update, and Delete objects. Any language that supports HTTP can
access these interfaces. Create and Update are idempotent operations.

|---
|Action | HTTP Verb | Notes
|---
|Create | POST | Object is created. If it already exists, it is updated.
|Read | GET | Object is read.
|Update | PUT | Object is created. If it already exists, it is updated.
|Delete | DELETE | Object is deleted. If the object has already been deleted, does nothing.
{:.table-striped}

<br>

###Status Codes
<hr>

HTTP Status codes are used to indicate success or failure. The set of status codes returned
by the Network Integration API are:

|---
|Status Code | Meaning
|---
|200, 201 | Success
|401 | Failure. Access is not authorized.
|403 | Failure. Request arguments are invalid.
|404 | Failure. The resource was not found.
|500 | Failure. Internal Service Error.
{:.table-striped}

\* See the section on Error Handling for greater detail on response bodies for failure codes.


###Security
<hr>

HTTPS is required for all API requests.

Authentication is performed using one of several approaches.

The preferred approach is to use Invoca API tokens, which are created and managed on the Manage API Credentials page of the platform.

Some API endpoints will accept HTTP(S) Basic Authentication, which authenticates using a username and password in the request header.  

Additionally, session login authentication is sufficient as an alternative. This is so that you can
test an API URL simply by logging in to the platform first as a Network Role of ‘Super’ (full access user) and then pasting the URL into the browser.

###Using OAuth token to Access Invoca APIs
<hr>

Requests are authenticated using HTTPS basic authentication with an Invoca API Token, which can be created and managed on the Manage API Credentials page in the platform.
<br><br>

####Step by step guide using API token to access APIs
<hr>

1. Obtain OAuth 2.0 credentials from the Manage API Credentials.

   Visit your API Credentials page to obtain OAuth 2.0 credentials for your Network Integration API.

2. Send the access token to an API.

<br>

After you obtain a token, include it in the HTTP header of your request, as a URL string parameter, or as a key/value pair in the JSON body.

Example using API token as URL parameter:

`https://<vanity>.invoca.net/api/2015-05-01/advertisers.json?oauth_token=YbcFHZ38FNfptfZMB0RZ6dk9dOJCaCfU`

Example using Curl to make an API call with token-based authentication:

<pre><code>curl -X POST -H "Accept: application/json" -H "Content-Type: application/json" 'https://\<vanity\>.invoca.net/api/2015-05-01/advertisers/1111.json' -d '{"oauth_token":"YbcFHZ38FNfptfZMB0RZ6dk9dOJCaCfU"}'
</code></pre>
{: .prettyprint .theme-github}

<b>Guidelines</b>
* Users should generate their own API tokens. Tokens should be treated like passwords and not be emailed or transmitted over other insecure mediums, nor should they be stored in a source code repository.
* As a network user, you should not generate a token on behalf of Advertisers or Publishers because tokens inherit the privileges of the user generating it.
* Invoca does not use OAuth refresh tokens.



###Idempotency
<hr>

Most interfaces are designed to be idempotent, meaning that it is harmless to call them
more than once with the same parameters. Subsequent calls to an interface have no side effects,
and return the same result.

###Self‐Correction
<hr>

Most updates expect a complete copy of the object, making Update and Create
interchangeable. This means that errors tend to be corrected over time. Campaign Terms
are an exception to this due to their complexity (see Advertiser Campaigns for more).

###Versioning
<hr>

The API version is given as a date in the path.

###Dedicated Subdomain
<hr>
All APIs are accessed through the dedicated subdomain of invoca.net that is used for the
network. For example, a network named "LeadTrust" might be assigned
leadtrust.invoca.net. We recommend that, when making your API calls, you place your
\<network_id> after the API version in the url.

###Request Parameter Format & Response Body Format
<hr>

Previous versions of the API accepted form‐encoded style parameters in the request and used
XML as the output format. As of 2015‐05‐01, all new feature development has switched to
JSON format for both request and response. Previous XML functionality will continue to be
supported via the 2013‐03‐22 version of the API (please contact
[questions@invoca.com](mailto:questions@invoca.com) for more information on previous versions).

##Error Handling

###AdvertiserCampaign RingPools
<hr>

Not found – 404:

`https://invoca.net/api/2014­-01-­01/<network_id>/advertisers/1/advertiser_campai
gns/100/ring_pools/123.json`

<pre><code>{
  "errors": {
    "invalid_data": "Could not find RingPool 123 for advertiser campaign 100 and advertiser 1",
    "class": "RecordNotFound"
  }
}
</code></pre>
{: .prettyprint .theme-github}


###Affiliate Campaign RingPools
<hr>

Not found – 404:

`https://invoca.net/api/2014­-01-­01/<network_id>/advertisers/1/advertiser_campai
gns/100/affiliates/300/affiliate_campaigns/ring_pools/123.json`

<pre><code>{
  "errors": {
    "invalid_data": "Could not find RingPool 123 for affiliate 300 and advertiser campaign 100",
    "class": "RecordNotFound"
  }
}
</code></pre>
{: .prettyprint .theme-github}


###Common RingPool errors:
<hr>

Validation failed – 403 – Body contains a json with validation errors for each field:

<pre><code>{
  "errors": {
    "pool_type": [
      "can't be blank"
    ],
    "destination_type": [
      "can't be blank"
    ],
    "name": [
      "can't be blank"
    ]
  }
}
</code></pre>
{: .prettyprint .theme-github}


Service error – 500 – Body contains a json Error with a unique handle (to use as a
cross‐reference with Invoca):

<pre><code>{
  "errors": {
    "invalid_data": "refer to error handle 1228118400",
    "class": "InternalServiceError"
  }
}
</code></pre>
{: .prettyprint .theme-github}

## PPC Platform Authentication Access Tokens

The PPC Platform provides an interface to get a one‐time use access token authenticating a
Network, Advertiser, or Affiliate user. The access token must then be appended to a PPC
Platform destination URL.

The network authenticates an organization by doing the following:

1. Authenticates the user on the network Platform.
2. Makes a server‐to‐server request for a one‐time use access token.
3. Appends the returned access token to the PPC Platform destination URL `access_token=<ProvidedAccessToken>`
4. Redirects to the PPC Platform destination URL.

The format of the API URL is in (2):

`https://invoca.net/api/2014-­01-­01/<network_id>/network/<email>/create_access_token.json`

`https://invoca.net/api/2014­-01-­01/<network_id>/advertisers/<advertiser_id_from
_network>/<email>/create_access_token.json`

`https://invoca.net/api/2014­-01-­01/<network_id>/affiliates/<affiliate_id_from_n
etwork>/<email>/create_access_token.json`

The success response is an JSON document with a root element of Response that contains a
single AccessToken element whose content is the access token:

|---
|Response JSON Element | Value
|---
|AccessToken | The access token
|---
{:.table-striped}

<br>

Example URLs

Create access token for “sy@young.com” network user:

POST

`https://invoca.net/api/2014­-01-­01/<network_id>/network/sy%40young.com/create_access_token.json HTTP/1.1`


Response:
<pre><code>{
  "token": "bpD8HmLcCxzSiOX01v­4XbZr4_s",
  "id": 1
}
</code></pre>
{: .prettyprint .theme-github}

Create access token for “sy@young.com” user in advertiser id 354:

POST

`https://invoca.net/api/2014­-01-­01/<network_id>/advertisers/354/sy%40young.com/create_access_token.json HTTP/1.1`

Response:
<pre><code>{
  "token": "bpD8HmLcCxzSiOX01v­4XbZr4_s",
  "id": 1
}
</code></pre>
{: .prettyprint .theme-github}

Create access token for “sy@young.com” user in affiliate id 976:

POST

`https://invoca.net/api/2014­-01-­01/<network_id>/affiliates/976/sy%40young.com/create_access_token.json HTTP/1.1`

Response:
<pre><code>{
  "token": "bpD8HmLcCxzSiOX01v­4XbZr4_s",
  "id": 1
}
</code></pre>
{: .prettyprint .theme-github}

<br>
<h3>
On-The-Fly Authentication
</h3>
<hr>


The PPC Platform supports "On-The-Fly Authentication": if a user types in a URL, or clicks
on a link in an email, or chooses a bookmarked link and they are not currently logged in
("authenticated"), they must first log in and then are redirected to their original destination
URL.

When using the API, all authentication is by the network on behalf of the replicated users.
So in this case the PPC Platform redirects to a network authentication URL such as
[http://www.network.com/loginwith](http://www.network.com/loginwith) with the following query parameters:

|---
|Query Parameter | Description
|---
|destination | The ultimate PPC Platform destination URL to redirect to once authentication has been established.
|---
|type | Either advertiseror affiliate, or empty if unknown.
{:.table-striped}

For example:

`http://www.network.com/login?destination=
http%3A%2F%2Finvoca.net%2Faffiliates%2F1&type=advertiser`

The network authenticates the user either by using existing session credentials or by
prompting for login credentials. It generates an access token using a server‐to‐server
POST:

POST

`https://invoca.net/api/2014­-01-­01/<network_id>/advertisers/354/sy%40young.com/create_acce
ss_token.json`

The returned value is an access token, for example 9AC23B903F4. The network then
appends this token to the destination URL and redirects there:

`http://invoca.net/affiliates/1?access_token=9AC23B903F4`

<br>
<h3>
Network Link to PPC
</h3>
<hr>


The network platform offers a Marketing Automation hyperlink in the authenticated area
for Advertisers and Affiliates. The link uses the same landing page as On-The-Fly
authentication does to seamlessly log the user into the Invoca Marketing Automation
Platform:

`http://www.network.com/login?destination=http%3A%2F%2F<network>.invoca.net%2Fhome`

<br>
<h3>
PPC Link to Network
</h3>
<hr>

The PPC platform offers a “Return from marketing automation” link that returns to an
appropriate URL at the network. This URL must be provided by the network. For
example:

[http://www.network.com/home](http://www.network.com/home)

<br>
<h3>
CURL examples:
</h3>
<hr>


Here are some basic examples on how to use the API using CURL.

Create

`curl -v ­XPOST -H "Content­Type: application/json" -u '<username>:<password>’ 'https://www.invoca.net/api/2014­-01-­01/<network_id>/<url>' -d '<valid JSON>’`

Read

`curl -v -u '<username>:<password> 'https://www.invoca.net/api/2014­-01­-01/<network_id>/<url>'`

Update

`curl­ -v -XPUT -H "Content­Type: application/json" -u '<username>:<password> 'https://www.invoca.net/api/2014­-01-­01/<network_id>/<url>' -d '<valid JSON>’`

Delete

`curl -v -XDELETE -H "Content­Type: application/json" -u '<username>:<password> 'https://www.invoca.net/api/2014­-01­-01/<network_id>/<url>' -d '<valid JSON>’`
