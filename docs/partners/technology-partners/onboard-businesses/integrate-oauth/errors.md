> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Errors

> List of errors that could arise during Razorpay OAuth integration.

Available in
🇮🇳 India

Given below is a list of errors you might face while integrating with Razorpay OAuth.

## Initiate Authorisation Using URL

| Error | Cause | Solution |
| - | - | - |
| The authorization grant type is not supported by the authorization server. | <ul><li>The `response_type` is not provided or is not `code`.</li><li>The `client_id` is not provided.</li></ul> | <ul><li>Ensure that you pass the `response_type` as `code`.</li><li>Provide your application `client_id`.</li></ul> |
| A server error occurred while serving this error. | One or more of the following is not provided: <ul><li>State</li><li>Scope</li><li>Redirect URI</li></ul> | Ensure that you enter the state, scope and `redirect_uri`. |
| The requested scope is invalid, unknown or malformed | The scope entered is invalid. | Use a valid scope. Possible values are `read_only` and `read_write`. |
| Client authentication failed | The `client_id` or `redirect_uri` provided is wrong. | Use a valid `client_id` and `redirect_uri`. |
| Access is forbidden | The scope entered is invalid. | Use a valid scope. Possible values are `read_only` and `read_write`. |

## Token APIs

| Error | Cause | Solution |
| - | - | - |
| Check the `client_id` parameter | The `client_id` is not provided. | Provide your application `client_id`. |
| Check the `client_secret` parameter | The `client_secret` provided is not a string. | Ensure that the `client_secret` is a string. |
| Invalid Client or Grant type | The `client_id` does not exist. | Use a valid `client_id`. |
| Access denied | The `client_secret` provided is wrong. | Use a valid `client_secret`. |
| Check that all required parameters have been provided | <ul><li>The `grant_type` provided is invalid.</li><li>The `authorization_code` is not provided.</li></ul> | <ul><li>Use a valid `grant_type`.</li><li>Ensure that you enter the authorisation code.</li></ul> |
| Check the `redirect_uri` parameter | The `redirect_uri` is not provided or is not a string. | Ensure that the `redirect_uri` is a valid string. |
| Client authentication failed | The `redirect_uri` provided does not match the one configured with the client. | Use the `redirect_uri` that is configured with the client. |
| Only allowed modes are test or live | The mode used is not valid. | Only use either live or test mode. |
| Mode can be only set to live for production clients | A production client is using test mode API keys. | Ensure that you only use live API keys if you are a production client. |
| Cannot decrypt the authorization code | The `authorization_code` provided is invalid. | Use a valid authorisation code. |
| Authorization code has expired | The `authorization_code` provided has expired. | Use a valid authorisation code. |
| Authorization code has been revoked | The `authorization_code` provided has been revoked. | Use a valid authorisation code. |
| Authorization code was not issued to this client | The `authorization_code` provided does not belong to the client id used. | Ensure that the `authorization_code` belongs to the client id used. |
| Invalid redirect URI | The `redirect_uri` entered is incorrect. | Ensure that the `redirect_uri` entered matches the one added in the application settings. |

### Refresh Token API

In addition to the [Token API errors](#token-apis), you may also face the below errors when refreshing a token.

| Error | Cause | Solution |
| - | - | - |
| Check the `refresh_token` parameter | The refresh token is not provided. | Ensure that you enter the refresh token in the request. |
| Cannot decrypt the refresh token | An invalid refresh token is provided. | Use a valid refresh token. |
| Token is not linked to client | The refresh token provided: <ul><li>Does not belong to the client id.</li><li>Has expired.</li></ul> | Use a valid refresh token that belongs to the client id provided. |
| Token has been revoked | The refresh token provided has been revoked. | Use a valid refresh token. |

### Revoke Token API

| Error | Cause | Solution |
| - | - | - |
| Could not validate the token provided | <ul><li>The access token used is invalid, has expired or has already been revoked.</li><li>The access token used does not belong to the OAuth client id provided.</li></ul> | <ul><li>Use a valid access token that has not been revoked yet.</li><li>Ensure that the access token belongs to the OAuth client id provided.</li></ul> |
| The server encountered an error. The incident has been reported to admins | The server was not able to process the request. | Retry after some time. |
