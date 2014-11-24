---
layout: default
group: get-started
subgroup: Web API concepts
title: Web API concepts
menu_title: Web API concepts
menu_order: 2
menu_node: parent
github_link: get-started/gs-web-api-concepts.md
---

<p>A web API call is made up of a request and a response.</p>
<a name="requests"></a>
<h2>Web API requests</h2>
<a name="verbs"></a>
<h3>HTTP verbs</h3>
<p>Include one of these HTTP verbs in the web API request:</p>
<dl>
   <dt>GET</dt>
   <dd>Requests transfer of a current representation of the
      target resource.
   </dd>
   <dt>PUT</dt>
   <dd>Requests that the state of the target resource be
      created or replaced with the state defined by the representation
      enclosed in the request message payload.
   </dd>
   <dt>POST</dt>
   <dd>Requests that the origin server accept the
      representation enclosed in the request as data to be processed by the
      target resource.
   </dd>
   <dt>DELETE</dt>
   <dd>Requests that the origin server delete the target
      resource.
   </dd>
</dl>
<a name="endpoints"></a>
<h3>Endpoints</h3>
<p>An endpoint is a combination of a URL and URI.</p>
<p>The REST endpoint URL is <code>http://magento.ll/index.php/rest/</code>.</p>
<p>The URL points to the server that fulfills the request.</p>
<p>The URI is the resource against which the request is being made. Specifically, the service endpoint combines:</p>
<ul>
   <li>The web protocol: <code>http</code></li>
   <li>The server that fulfills the request: <code>magento.ll/index.php</code></li>
   <li>The web service: <code>rest</code></li>
   <li>The resource URI: <code>V1/customerGroups/</code></li>
   <li>Any template parameters: <code>/:id</code></li>
</ul>
<p>In this example, the service endpoint is:</p>
<pre>http://magento.ll/index.php/rest/V1/customerGroups/:id</pre>
<a name="payload"></a>
<h3>Call payload</h3>
<p>Payloads</p>
<a name="formats"></a>
<h3 id="formats">Request and response formats</h3>
<ul>
   <li>JSON</li>
   <li>XML</li>
</ul>
<p>The decision to use JSON- or XML-formatted data depends on your data integration requirements. For example, if you are writing a Magento 2 service consumer, the consumer drives the decision to use either JSON or XML.</p>
<p>The JSON response format is the default.</p>
<p>To request an XML response:</p>
<ul>
   <li>Set the HTTP </code>Accept</code> header to </code>text/xml</code>.</li>
   <li>Set the HTTP </code>Content-Type</code> header to </code>text/xml</code>.</li>
</ul>
<a name="http-headers"></a>
<h3>HTTP headers</h3>
<p>Magento has many services and some require that you specify a set of HTTP headers
   in your calls.
</p>
<table style="width:100%">
   <tr bgcolor="lightgray">
      <th>HTTP header</th>
      <th>Description</th>
   </tr>
   <tr>
      <td>
         <code>Authorization: Bearer</code>
      </td>
      <td>The authentication token.</td>
   </tr>
   <tr>
      <td>
         <code>Accept</code>
      </td>
      <td>The API password. This is one of the Authentication token assigned to your account.</td>
   </tr>
   <tr>
      <td>
         <p>
            <code>Content-Type</code>
         </p>
      </td>
      <td>
         <p>Required for operations with a request body.</p>
         <p>Specifies the format of the request body. The following example shows the syntax for the header, where format is either <code>json</code> or <code>xml</code>:</p>
         <pre>Content-Type: application/format</pre>
      </td>
   </tr>
</table>
<p>Be aware that different Magento APIs use different sets of HTTP headers (and some
   don't use any at all). Refer to the Developer documentation for the definitive list
   of HTTP headers for the Magento operation(s) you plan to use.
</p>
<a name="responses"></a>
<h2>Web API responses</h2>
<h3>Error handling</h3>
<h4>Service errors</h4>
<p>Service operations always throw exceptions with a service-specific error code and an optional error message. Exceptions enable in-process PHP calls to handle the exception and behave accordingly.</p>
<p>Exceptions contain fields for error codes, error messages, service name, and parameters to generate a different localized error message. You can add base exceptions as needed.</p>
<p>The base exceptions are:</p>
<ul>
   <li><code>Magento_Service_Exception</code>. The client is notified of all business logic violations when this exception or one of its derivative is thrown.</li>
   <li><code>Magento_Service_AuthorizationException</code>. All authorization check failures should be notified to the caller by throwing this exception or one of its derivative.</li>
   <li><code>Magento_Service_ResourceNotFoundException</code>. If the requested resource does not exist, service should throw this exception or one of its derivative.</li>
</ul>
<p>Services do not wrap system exceptions such as network exceptions or database connection exceptions into a service exception. Those exceptions are thrown to the client as-is so the root cause is identified.</p>
<p>Error codes are service-specific. The service name field in the exception helps the caller identify the service. The combination of service name and error code provides a unique error. The service name is a namespace for all errors, including the ones introduced by extensions.</p>
<h4>Web API error-related behavior</h4>
<ul>
   <li>Web API catches all the exceptions thrown by a service and returns an appropriate error response.</li>
   <li>Web API maintains a mapping of base service exceptions to HTTP return codes. This mapping helps determine the HTTP return code.</li>
   <li>Apart from HTTP codes, service error codes and error messages are returned to the caller.</li>
   <li>Every Response object contains an error structure that sends an error response. The error structure contains ErrorCode and ErrorMessage.</li>
   <li>The importance of the service-specific error codes and backward compatibility may vary for each service. The service-specific error codes are helpful for debugging.</li>
   <li>In case of errors, response contains an <code>Error</code> element with error code returned by the service and with the error message in the payload.</li>
   <li>In case of authentication or authorization errors, response contains an <code>Error</code> element with an error code denoting authentication or authorization error codes and error messages in the payload.</li>
</ul>
<h3>HTTP status codes</h3>
<p>The web API returns relevant HTTP return codes, such as 200, 400, and 500, that reflect the result of a request.</p>
<table style="width:100%">
   <colgroup>
      <col width="10%">
      <col width="20%">
      <col width="70%">
   </colgroup>
   <thead>
      <tr style="background-color:lightgray">
         <th>HTTP code</th>
         <th>Description</th>
         <th>Notes</th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td>200</td>
         <td>Success</td>
         <td>Framework returns HTTP 200 to the caller upon success.</td>
      </tr>
      <tr>
         <td>400</td>
         <td>Bad Request</td>
         <td>If service implementation throws either <code>Magento_Service_Exception</code> or its derivative, framework returns a HTTP 400 with a error response including the service-specific error code and message.</td>
      </tr>
      <tr>
         <td>401</td>
         <td>Unauthorized</td>
         <td>If an error occurs during credential validation or if service throws <code>Magento_Service_AuthorizationException</code>, framework returns HTTP 401.</td>
      </tr>
      <tr>
         <td>404</td>
         <td>Incorrect URI/Resource not found</td>
         <td>If the request endpoint is not correct, framework returns HTTP 404. If service throws <code>Magento_Service_ResourceNotFoundException</code>, framework returns HTTP 404.</td>
      </tr>
      <tr>
         <td>500</td>
         <td>System Errors</td>
         <td>If service implementation throws any other exception like network errors, database communication, framework returns HTTP 500.</td>
      </tr>
   </tbody>
</table>
<h4>Error format</h4>
<p>Errors returned by the Web API contain an error code, an error message, and parameters that enable you to generate an error message inside the client.</p>
<table style="width:100%">
   <colgroup>
      <col width="30%">
      <col width="70%">
   </colgroup>
   <thead>
      <tr style="background-color:lightgray">
         <th>Part</th>
         <th>Description</th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td>errorCode</td>
         <td>The error code representing the error.</td>
      </tr>
      <tr>
         <td>errorMessage</td>
         <td>The message explaining the error.</td>
      </tr>
      <tr>
         <td>parameters</td>
         <td>Optional. An array of attributes used to generate a different and/or localized error message for the client.</td>
      </tr>
   </tbody>
</table>