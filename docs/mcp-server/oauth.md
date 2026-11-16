> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Integrate OAuth 2.0 with Razorpay MCP Server

> Enable granular permissions and user-based authorisation using OAuth 2.0 with Razorpay MCP Server.

Available in
🇮🇳 India

The Razorpay MCP Server uses OAuth 2.0 to authenticate MCP clients securely. OAuth provides enhanced security compared to using secret keys directly, as it enables granular permissions and user-based authorisation.

> [accordion] Benefits
>
> * **Enhanced Security**: No need to share API secret keys directly.
> * **Granular Permissions**: Control access at a more detailed level.
> * **User-Based Authorisation**: Individual user consent and access management.
> * **Token Expiration**: Temporary access tokens that can be refreshed or revoked.

## Client Registration Methods

Razorpay MCP Server supports two methods for registering OAuth clients:

> [accordion] Dynamic Client Registration (DCR)
>
> Your application registers itself programmatically by calling the `/register` endpoint. This is the recommended approach for MCP clients.
>
> **How it works**
>
> DCR allows MCP clients to register themselves programmatically with the Razorpay authorisation server, instead of requiring manual creation of client credentials.
>
> When a client sends a registration request to the `/register` endpoint, the authorisation server creates a new client with a unique `client_id` and `client_secret`.

> [accordion] Manual Registration
>
> Write to the [Razorpay Support Team](mailto:n8n-node-support@razorpay.com) to generate a Client id and secret manually.

## OAuth Flow

The Razorpay MCP Server implements the OAuth 2.0 Authorisation Code flow. Here is how the integration works:

1. **Discover Endpoints**: Retrieve OAuth endpoints from the well-known configuration.
2. **Register Client**: Register your application using Dynamic Client Registration.
3. **Request Authorisation**: Direct users to the authorisation endpoint.
4. **Receive Authorisation Code**: Handle the callback with the temporary code.
5. **Exchange for Access Token**: Trade the authorisation code for an access token.
6. **Access MCP Tools**: Use the access token to call Razorpay MCP Server tools.

## Integration Steps

> [accordion] Step 1: Discover OAuth Endpoints
>
> Before starting the OAuth flow, retrieve the available endpoints and supported configurations using the well-known endpoint.
>
> `GET https://mcp.razorpay.com/.well-known/oauth-authorization-server`
>
> ```bash Request theme={null}
> curl -X GET https://mcp.razorpay.com/.well-known/oauth-authorization-server
> ```
>
> ```json Response theme={null}
> {
>   "issuer": "https://mcp.razorpay.com",
>   "authorization_endpoint": "https://mcp.razorpay.com/authorize",
>   "token_endpoint": "https://mcp.razorpay.com/token",
>   "registration_endpoint": "https://mcp.razorpay.com/register",
>   "scopes_supported": [
>     "read_only"
>   ],
>   "response_types_supported": [
>     "code"
>   ],
>   "grant_types_supported": [
>     "authorization_code",
>     "client_credentials",
>     "refresh_token"
>   ],
>   "token_endpoint_auth_methods_supported": [
>     "client_secret_post"
>   ],
>   "code_challenge_methods_supported": [
>     "S256"
>   ]
> }
> ```
>
> > [accordion] Response Parameters
> >
> > `issuer`
> > : `string` The OAuth 2.0 issuer identifier.
> >
> > `authorization_endpoint`
> > : `string` The URL for requesting user authorisation.
> >
> > `token_endpoint`
> > : `string` The URL for exchanging authorisation codes for tokens.
> >
> > `registration_endpoint`
> > : `string` The URL for [Dynamic Client Registration](#step-2-register-your-client). MCP clients use this endpoint to register programmatically and obtain client credentials.
> >
> > `scopes_supported`
> > : `array` List of available OAuth scopes.
> >
> > `response_types_supported`
> > : `array` Supported OAuth response types.
> >
> > `grant_types_supported`
> > : `array` Supported OAuth grant types.
> >
> > `token_endpoint_auth_methods_supported`
> > : `array` Supported methods for authenticating at the token endpoint. For example, `client_secret_post` indicates that the client secret is sent in the request body.
> >
> > `code_challenge_methods_supported`
> > : `array` PKCE (Proof Key for Code Exchange) challenge methods. `S256` indicates SHA-256.

> [accordion] Step 2: Register Your Client
>
> Register your application to obtain a Client id and secret. You can use either of the following methods:
>
> * **Dynamic Client Registration (Recommended)**: Your application registers itself programmatically by sending a `POST` request to the `/register` endpoint.
> * **Manual Registration**: Write to the [Razorpay Support Team](mailto:n8n-node-support@razorpay.com) to generate client credentials.
>
> ### Dynamic Client Registration
>
> Send a `POST` request to the registration endpoint with your client details.
>
> `POST https://mcp.razorpay.com/register`
>
> ```bash Request theme={null}
> curl -H 'Content-Type: application/json' \
> -X POST https://mcp.razorpay.com/register \
> -d '{
>   "client_name": "MCP Inspector",
>   "redirect_uris": [
>     "http://localhost:6274/oauth/callback/debug"
>   ],
>   "grant_types": [
>     "authorization_code",
>     "refresh_token"
>   ],
>   "response_types": [
>     "code"
>   ],
>   "scope": "read_only",
>   "token_endpoint_auth_method": "none",
>   "client_uri": "https://github.com/modelcontextprotocol/inspector"
> }'
> ```
>
> ```json Response theme={null}
> {
>   "client_id": "xxxxxxxxxxxx",
>   "client_secret": "xxxxxxxxxxxx",
>   "client_id_issued_at": 1770803945,
>   "client_name": "MCP Inspector",
>   "redirect_uris": [
>     "http://localhost:6274/oauth/callback/debug"
>   ],
>   "grant_types": [
>     "authorization_code",
>     "refresh_token"
>   ],
>   "response_types": [
>     "code"
>   ],
>   "token_endpoint_auth_method": "client_secret_post",
>   "application_type": "public",
>   "scope": "read_only",
>   "application_id": "xxxxxxxxxxxxx"
> }
> ```
>
> > [accordion] Request Parameters
> >
> > `client_name` *mandatory*
> > : `string` A human-readable name for your client application.
> >
> > `redirect_uris` *mandatory*
> > : `array` List of redirect URIs to which the authorisation server redirects the user after an authorisation grant. These must exactly match the `redirect_uri` parameter used in authorisation requests.
> >
> > `grant_types` *mandatory*
> > : `array` OAuth 2.0 grant types the client will use. Supported values: `authorization_code`, `refresh_token`.
> >
> > `response_types` *mandatory*
> > : `array` OAuth 2.0 response types the client will use. Use `code` for the authorisation code flow.
> >
> > `scope` *optional*
> > : `string` Requested OAuth scopes. For example, `read_only`.
> >
> > `token_endpoint_auth_method` *optional*
> > : `string` Authentication method for the token endpoint. Use `none` for public clients.
> >
> > `client_uri` *optional*
> > : `string` URL of the client application's home page.
>
> > [accordion] Response Parameters
> >
> > `client_id`
> > : `string` Unique identifier assigned to your client. Use this in authorisation and token requests.
> >
> > `client_secret`
> > : `string` Secret key for your client. Store this securely and use it when exchanging authorisation codes for tokens.
> >
> > `client_id_issued_at`
> > : `integer` Unix timestamp indicating when the client credentials were issued.
> >
> > `client_name`
> > : `string` The registered name of your client application.
> >
> > `redirect_uris`
> > : `array` The registered redirect URIs for your client.
> >
> > `grant_types`
> > : `array` The grant types your client is authorised to use.
> >
> > `response_types`
> > : `array` The response types your client is authorised to use.
> >
> > `token_endpoint_auth_method`
> > : `string` The authentication method assigned for the token endpoint. For example, `client_secret_post`.
> >
> > `application_type`
> > : `string` The type of client created. For example, `public`.
> >
> > `scope`
> > : `string` The scopes granted to your client.
> >
> > `application_id`
> > : `string` Unique identifier for the application associated with the client.

> [accordion] Step 3: Request User Authorisation
>
> Redirect users to the authorisation endpoint to grant access to your application.
>
> `GET https://mcp.razorpay.com/authorize`
>
> ```bash Request theme={null}
> https://mcp.razorpay.com/authorize?response_type=code&client_id={YOUR_CLIENT_ID}&redirect_uri={YOUR_REDIRECT_URI}&scope=read_only&state={RANDOM_STATE_VALUE}&code_challenge={CODE_CHALLENGE}&code_challenge_method=S256
> ```
>
> ```bash Example Request theme={null}
> https://mcp.razorpay.com/authorize?response_type=code&client_id=xyz123&redirect_uri=https://cli.tool/callback&scope=read_only&state=random_state_string&code_challenge=hashed_code_verifier&code_challenge_method=S256
> ```
>
> > [accordion] Query Parameters
> >
> > `response_type` *mandatory*
> > : `string` Must be `code` for authorisation code flow.
> >
> > `client_id` *mandatory*
> > : `string` Your registered client identifier, obtained from [Step 2](#step-2-register-your-client).
> >
> > `redirect_uri` *mandatory*
> > : `string` URL where the user will be redirected after authorisation. Must match a URI registered during client registration.
> >
> > `scope` *mandatory*
> > : `string` Requested permissions. For example, `read_only`.
> >
> > `code_challenge` *recommended*
> > : `string` PKCE code challenge. Generate a random string (code verifier), then compute its SHA-256 hash and Base64 URL-encode the result.
> >
> > `code_challenge_method` *recommended*
> > : `string` Must be `S256` when using PKCE.
> >
> > `state` *recommended*
> > : `string` Random string to prevent CSRF attacks.
>
> > [accordion] User Experience
> >
> > When users visit this URL, they:
> >
> > 1. Log in to their Razorpay account.
> > 2. Review the permissions your application is requesting.
> > 3. Approve or deny access.

> [accordion] Step 4: Handle Authorisation Callback
>
> After the user approves access, Razorpay redirects them to your `redirect_uri` with an authorisation code.
>
> **Callback URL Format** \\
>
> `https://cli.tool/callback?code={AUTHORIZATION_CODE}&state={STATE_VALUE}`
>
> > [accordion] Callback Parameters
> >
> > `code`
> > : `string` Temporary authorisation code (single-use).
> >
> > `state`
> > : `string` The same state value you sent in the authorisation request.
>
> > [!WARNING]
> >
> > **Security Check**
> >
> > Always verify that the `state` parameter matches the value you sent in the initial request to prevent CSRF attacks.

> [accordion] Step 5: Exchange Authorisation Code for Access Token
>
> Use the authorisation code to obtain an access token from the token endpoint.
>
> `POST https://mcp.razorpay.com/token`
>
> ```bash Request theme={null}
> curl -X POST https://mcp.razorpay.com/token \
>   -H "Content-Type: application/x-www-form-urlencoded" \
>   -d "grant_type=authorization_code" \
>   -d "client_id=xyz123" \
>   -d "client_secret=secret456" \
>   -d "code=authCodeXYZ" \
>   -d "redirect_uri=https://cli.tool/callback" \
>   -d "code_verifier=rawRandomStringUsedEarlier"
> ```
>
> ```json Response theme={null}
>   {
>     "access_token": "mcp_access_token_abc123",
>     "token_type": "Bearer",
>     "expires_in": 3600,
>     "scope": "read_only"
>   }
> ```
>
> > [accordion] Request Parameters
> >
> > `grant_type` *mandatory*
> > : `string` Must be `authorization_code`.
> >
> > `client_id` *mandatory*
> > : `string` Your registered client identifier.
> >
> > `client_secret` *conditional*
> > : `string` Required for confidential clients. Send this in the request body (`client_secret_post` method).
> >
> > `code` *mandatory*
> > : `string` The authorisation code from [Step 4](#step-4-handle-authorisation-callback).
> >
> > `redirect_uri` *mandatory*
> > : `string` Must match the URI used in the authorisation request.
> >
> > `code_verifier` *conditional*
> > : `string` Required if a `code_challenge` was sent in the authorisation request. This is the original random string used to generate the code challenge.
>
> > [accordion] Response Parameters
> >
> > `access_token`
> > : `string` OAuth bearer token for accessing MCP tools. Use this token in the Authorization header for all API requests.
> >
> > `token_type`
> > : `string` Always `Bearer`. This indicates the type of token returned.
> >
> > `expires_in`
> > : `integer` Token lifetime in seconds. For example, 3600 = 1 hour. Track this value to refresh tokens before expiration.
> >
> > `scope`
> > : `string` Granted permissions. Indicates which scopes were approved by the user.

> [accordion] Step 6: Use Access Token to Call MCP Tools
>
> Include the access token in the Authorisation header when making requests to Razorpay MCP Server tools.
>
> `GET https://mcp.razorpay.com/api/tool-endpoint`
>
> ```bash Request theme={null}
> curl -X GET https://mcp.razorpay.com/api/tool-endpoint \
>   -H "Authorization: Bearer mcp_access_token_abc123"
> ```
>
> ```bash Example Request theme={null}
> curl -X GET https://mcp.razorpay.com/api/payments/pay_123456 \
>   -H "Authorization: Bearer mcp_access_token_abc123"
> ```

## Token Management

> [accordion] Token Expiration
>
> Access tokens expire after a set period. Monitor the `expires_in` value and implement token refresh logic in your application.

> [accordion] Token Storage
>
> Store access tokens securely:
>
> * Never commit tokens to version control.
> * Use environment variables or secure vaults.
> * Encrypt tokens at rest.
> * Clear tokens from memory after use.

> [accordion] Token Revocation
>
> If you need to revoke a token before expiration, contact [Razorpay Support team](mailto:n8n-node-support@razorpay.com) or implement token management in your application settings.
