Advertiser Users
================

* * *

For convenience, the API provides an interface for performing operations on specific advertiser users. This is useful
for situations where it is inconvenient to send an array of all existing advertiser users.

Endpoint:

    https://invoca.net/api/2015-05-01/&lt;network_id&gt;/advertisers/&lt;advertiser_id_from_network&gt;/users/&lt;user_id_from_network&gt;.json

<div class="panel-group" id="accordion">
<div class="panel panel-default">
<div class="panel-heading toggle2 GET collapsed" data-toggle="collapse" data-target="#GET3658528685703960626" aria-expanded="false" aria-controls="GET3658528685703960626">
<h4 class="panel-title">
<div class="row">
<div class="col-md-2"><p class="GET-text">GET</p></div>
<div class="col-md-5"><p class="text-left">/advertisers/&lt;advertiser_id&gt;/users</p></div>
<div class="col-md-4"><span class="pull-right">Get all Advertiser Users for Advertiser</span></div>
</div>
</h4>
</div>
<div id="GET3658528685703960626" class="panel collapse" aria-expanded="false" style="height: 0px;">
<div class="panel-body">
<div>
<p>Get all Advertiser Users for Advertiser</p>
<br>
<h4> Examples </h4>
<hr>
<div class="example">
<div class="example-title">
<p>Read all advertiser users for advertiser e0Fv6YEk</p>
</div>
<span>Endpoint:
<p><code>https://invoca.net/api/2015-05-01/&lt;network_id&gt;/advertisers/e0Fv6YEk/users.json</code></p>
</span>
<p>Format:
application/json
</p>
<p>Response Code:
200
</p>
<p>Response Body:</p>
<pre class="prettyprint theme-github prettyprinted"><code><span class="pun">[</span><span class="pln"></span><span class="pun">{</span><span class="pln">
</span><span class="str">"email_address"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"chris@nfltix.com"</span><span class="pun">,</span><span class="pln">
</span><span class="str">"id_from_network"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"549494858585Dxlj2uCX0ijqXP4nAW"</span><span class="pun">,</span><span class="pln">
</span><span class="str">"first_name"</span><span class="pun">:</span><span class="pln"> </span><span class="str">"Chris"</span><span
class="pun">,</span><span class="pln">
</span><span class="str">"contact_country_code"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"1"</span><span class="pun">,</span><span class="pln">
</span><span class="str">"last_name"</span><span class="pun">:</span><span class="pln"> </span><span class="str">"Dean"</span><span
class="pun">,</span><span class="pln">
</span><span class="str">"role"</span><span class="pun">:</span><span class="pln"> </span><span class="str">"Manager"</span><span
class="pun">,</span><span class="pln">
</span><span class="str">"oauth_refresh_token"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"556588585858585858585858858"</span><span class="pun">,</span><span class="pln">
</span><span class="str">"contact_phone_number"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"8886033760"</span><span class="pln">
</span><span class="pun">}</span><span class="pln">
</span><span class="pun">]</span></code></pre>


</div>

</div>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading toggle2 collapsed GET" data-toggle="collapse" data-target="#GET-3400821928438983762"
aria-expanded="false" aria-controls="GET-3400821928438983762">
<h4 class="panel-title">

<div class="row">
<div class="col-md-2">
<p class="GET-text">GET</p>
</div>
<div class="col-md-5">
<p class="text-left">/advertisers/&lt;advertiser_id&gt;/users/&lt;user_id&gt;</p>
</div>

<div class="col-md-4">
<span class="pull-right">
Get an Advertiser User
</span>
</div>
</div>
</h4>
</div>
<div id="GET-3400821928438983762" class="panel collapse" aria-expanded="false">
<div class="panel-body">
<div>
<p>Get an Advertiser User</p>

<br>
<h4> Examples </h4>

<hr>
<div class="example">

<div class="example-title">
<p>Read a specific advertiser user</p>

</div>

<span>Endpoint:
<p><code>https://invoca.net/api/2015-05-01/&lt;network_id&gt;/advertisers/e0Fv6YEk/users/549494858585Dxlj2uCX0ijqXP4nAW.json</code>
</p>

</span>

<p>Format:
application/json
</p>


<p>Response Code:
200
</p>

<p>Response Body:</p>
<pre class="prettyprint theme-github prettyprinted"><code><span class="pun">{</span><span class="pln">
</span><span class="str">"email_address"</span><span class="pun">:</span><span class="pln"> </span><span class="str">"chris@nfltix.com"</span><span
class="pun">,</span><span class="pln">
</span><span class="str">"id_from_network"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"549494858585Dxlj2uCX0ijqXP4nAW"</span><span class="pun">,</span><span class="pln">
</span><span class="str">"first_name"</span><span class="pun">:</span><span class="pln"> </span><span class="str">"Chris"</span><span
class="pun">,</span><span class="pln">
</span><span class="str">"contact_country_code"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"1"</span><span class="pun">,</span><span class="pln">
</span><span class="str">"last_name"</span><span class="pun">:</span><span class="pln"> </span><span class="str">"Dean"</span><span
class="pun">,</span><span class="pln">
</span><span class="str">"role"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"Manager"</span><span class="pun">,</span><span class="pln">
</span><span class="str">"oauth_refresh_token"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"556588585858585858585858858"</span><span class="pun">,</span><span class="pln">
</span><span class="str">"contact_phone_number"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"8886033760"</span><span class="pln">
</span><span class="pun">}</span></code></pre>


</div>

</div>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading toggle2 collapsed POST" data-toggle="collapse" data-target="#POST-3780377522845086374"
aria-expanded="false" aria-controls="POST-3780377522845086374">
<h4 class="panel-title">

<div class="row">
<div class="col-md-2">
<p class="POST-text">POST</p>
</div>
<div class="col-md-5">
<p class="text-left">/advertisers/&lt;advertiser_id&gt;/users</p>
</div>

<div class="col-md-4">
<span class="pull-right">
Create an Adertiser User
</span>
</div>
</div>
</h4>
</div>
<div id="POST-3780377522845086374" class="panel collapse" aria-expanded="false">
<div class="panel-body">
<div>
<p>Create an Adertiser User</p>

<br>
<h4> Examples </h4>

<hr>
<div class="example">

<div class="example-title">
<p>Create an advertiser user</p>

</div>

<span>Endpoint:
<p><code>https://invoca.net/api/2015-05-01/&lt;network_id&gt;/advertisers/e0Fv6YEk/users.json</code></p>

</span>


<p>Request Body</p>
<pre class="prettyprint theme-github prettyprinted"><code><span class="pun">{</span><span class="pln">
</span><span class="str">"user"</span><span class="pun">:</span><span class="pln"> </span><span
class="pun">{</span><span class="pln">
</span><span class="str">"id_from_network"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"549494858585Dxlj2uCX0ijqXP4nAW"</span><span class="pun">,</span><span class="pln">
</span><span class="str">"email_address"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"chris@nfltix.com"</span><span class="pun">,</span><span class="pln">
</span><span class="str">"first_name"</span><span class="pun">:</span><span class="pln"> </span><span class="str">"Chris"</span><span
class="pun">,</span><span class="pln">
</span><span class="str">"last_name"</span><span class="pun">:</span><span class="pln"> </span><span class="str">"Dean"</span><span
class="pun">,</span><span class="pln">
</span><span class="str">"contact_phone_number"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"8055555555"</span><span class="pun">,</span><span class="pln">
</span><span class="str">"oauth_refresh_token"</span><span class="pun">:</span><span class="pln"> </span><span
class="str">"556588585858585858585858858"</span><span class="pun">,</span><span class="pln">
</span><span class="str">"role"</span><span class="pun">:</span><span class="pln"> </span><span class="str">"Manager"</span><span
class="pln">
</span><span class="pun">}</span><span class="pln">
</span><span class="pun">}</span></code></pre>


</div>

</div>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading toggle2 collapsed PUT" data-toggle="collapse" data-target="#PUT-3825890680866726622"
aria-expanded="false" aria-controls="PUT-3825890680866726622">
<h4 class="panel-title">

<div class="row">
<div class="col-md-2">
<p class="PUT-text">PUT</p>
</div>
<div class="col-md-5">
<p class="text-left">/advertisers/&lt;advertiser_id&gt;/users/&lt;user_id&gt;</p>
</div>

<div class="col-md-4">
<span class="pull-right">
Update an Advertiser User
</span>
</div>
</div>
</h4>
</div>
<div id="PUT-3825890680866726622" class="panel collapse" aria-expanded="false">
<div class="panel-body">
<div>
<p>Update an Advertiser User</p>

<br>

</div>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading toggle2 collapsed DELETE" data-toggle="collapse"
data-target="#DELETE316151902958468490" aria-expanded="false" aria-controls="DELETE316151902958468490">
<h4 class="panel-title">

<div class="row">
<div class="col-md-2">
<p class="DELETE-text">DELETE</p>
</div>
<div class="col-md-5">
<p class="text-left">/advertisers/&lt;advertiser_id&gt;/users/&lt;user_id&gt;</p>
</div>

<div class="col-md-4">
<span class="pull-right">
Delete an Advertiser User
</span>
</div>
</div>
</h4>
</div>
<div id="DELETE316151902958468490" class="panel collapse" aria-expanded="false">
<div class="panel-body">
<div>
<p>Delete an Advertiser User</p>

<br>
<h4> Examples </h4>

<hr>
<div class="example">

<div class="example-title">
<p>Delete an advertiser user</p>

</div>

<span>Endpoint:
<p><code>https://invoca.net/api/2015-05-01/&lt;network_id&gt;/advertisers/e0Fv6YEk/users/549494858585Dxlj2uCX0ijqXP4nAW.json</code>
</p>

</span>

<p>Format:
application/json
</p>


<p>Response Code:
200
</p>

<p>Response Body:</p>
<pre class="prettyprint theme-github prettyprinted"><code><span class="pun">{</span><span class="pln">
</span><span class="pun">}</span></code></pre>


</div>

</div>
</div>
</div>
</div>

<br>
</div>
