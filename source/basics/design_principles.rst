Design Principles
=================

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
