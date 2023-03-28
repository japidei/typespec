---
title: "Data types"
toc_min_heading_level: 2
toc_max_heading_level: 3
---

# Data types

## TypeSpec.Http

### `Response` {#TypeSpec.Http.Response}

```typespec
model Response<Status>
```

#### Template Parameters

| Name   | Description |
| ------ | ----------- |
| Status |             |

### `Body` {#TypeSpec.Http.Body}

Defines a model with a single property of the given type, marked with `@body`.

This can be useful in situations where you cannot use a bare T as the body
and it is awkward to add a property.

```typespec
model Body<T>
```

#### Template Parameters

| Name | Description |
| ---- | ----------- |
| T    |             |

### `LocationHeader` {#TypeSpec.Http.LocationHeader}

```typespec
model TypeSpec.Http.LocationHeader
```

### `HeaderOptions` {#TypeSpec.Http.HeaderOptions}

Header options.

```typespec
model TypeSpec.Http.HeaderOptions
```

### `OkResponse` {#TypeSpec.Http.OkResponse}

```typespec
model TypeSpec.Http.OkResponse
```

### `CreatedResponse` {#TypeSpec.Http.CreatedResponse}

```typespec
model TypeSpec.Http.CreatedResponse
```

### `AcceptedResponse` {#TypeSpec.Http.AcceptedResponse}

```typespec
model TypeSpec.Http.AcceptedResponse
```

### `NoContentResponse` {#TypeSpec.Http.NoContentResponse}

```typespec
model TypeSpec.Http.NoContentResponse
```

### `MovedResponse` {#TypeSpec.Http.MovedResponse}

```typespec
model TypeSpec.Http.MovedResponse
```

### `NotModifiedResponse` {#TypeSpec.Http.NotModifiedResponse}

```typespec
model TypeSpec.Http.NotModifiedResponse
```

### `BadRequestResponse` {#TypeSpec.Http.BadRequestResponse}

```typespec
model TypeSpec.Http.BadRequestResponse
```

### `UnauthorizedResponse` {#TypeSpec.Http.UnauthorizedResponse}

```typespec
model TypeSpec.Http.UnauthorizedResponse
```

### `ForbiddenResponse` {#TypeSpec.Http.ForbiddenResponse}

```typespec
model TypeSpec.Http.ForbiddenResponse
```

### `NotFoundResponse` {#TypeSpec.Http.NotFoundResponse}

```typespec
model TypeSpec.Http.NotFoundResponse
```

### `ConflictResponse` {#TypeSpec.Http.ConflictResponse}

```typespec
model TypeSpec.Http.ConflictResponse
```

### `PlainData` {#TypeSpec.Http.PlainData}

Produces a new model with the same properties as T, but with `@query`,
`@header`, `@body`, and `@path` decorators removed from all properties.

```typespec
model PlainData<T>
```

#### Template Parameters

| Name | Description |
| ---- | ----------- |
| T    |             |

### `QueryOptions` {#TypeSpec.Http.QueryOptions}

Query parameter options.

```typespec
model TypeSpec.Http.QueryOptions
```

### `BasicAuth` {#TypeSpec.Http.BasicAuth}

Basic authentication is a simple authentication scheme built into the HTTP protocol.
The client sends HTTP requests with the Authorization header that contains the word Basic word followed by a space and a base64-encoded string username:password.
For example, to authorize as demo / `p@55w0rd` the client would send

```
Authorization: Basic ZGVtbzpwQDU1dzByZA==
```

```typespec
model TypeSpec.Http.BasicAuth
```

### `BearerAuth` {#TypeSpec.Http.BearerAuth}

Bearer authentication (also called token authentication) is an HTTP authentication scheme that involves security tokens called bearer tokens.
The name “Bearer authentication” can be understood as “give access to the bearer of this token.” The bearer token is a cryptic string, usually generated by the server in response to a login request.
The client must send this token in the Authorization header when making requests to protected resources:

```
Authorization: Bearer <token>
```

```typespec
model TypeSpec.Http.BearerAuth
```

### `ApiKeyAuth` {#TypeSpec.Http.ApiKeyAuth}

An API key is a token that a client provides when making API calls. The key can be sent in the query string:

```
GET /something?api_key=abcdef12345
```

or as a request header

```
GET /something HTTP/1.1
X-API-Key: abcdef12345
```

or as a cookie

```
GET /something HTTP/1.1
Cookie: X-API-KEY=abcdef12345
```

```typespec
model ApiKeyAuth<TLocation, TName>
```

#### Template Parameters

| Name      | Description |
| --------- | ----------- |
| TLocation |             |
| TName     |             |

### `OAuth2Auth` {#TypeSpec.Http.OAuth2Auth}

OAuth 2.0 is an authorization protocol that gives an API client limited access to user data on a web server.
OAuth relies on authentication scenarios called flows, which allow the resource owner (user) to share the protected content from the resource server without sharing their credentials.
For that purpose, an OAuth 2.0 server issues access tokens that the client applications can use to access protected resources on behalf of the resource owner.
For more information about OAuth 2.0, see oauth.net and RFC 6749.

```typespec
model OAuth2Auth<TFlows>
```

#### Template Parameters

| Name   | Description |
| ------ | ----------- |
| TFlows |             |

### `AuthorizationCodeFlow` {#TypeSpec.Http.AuthorizationCodeFlow}

Authorization Code flow

```typespec
model TypeSpec.Http.AuthorizationCodeFlow
```

### `ImplicitFlow` {#TypeSpec.Http.ImplicitFlow}

Implicit flow

```typespec
model TypeSpec.Http.ImplicitFlow
```

### `PasswordFlow` {#TypeSpec.Http.PasswordFlow}

Resource Owner Password flow

```typespec
model TypeSpec.Http.PasswordFlow
```

### `ClientCredentialsFlow` {#TypeSpec.Http.ClientCredentialsFlow}

Client credentials flow

```typespec
model TypeSpec.Http.ClientCredentialsFlow
```

### `AuthType` {#TypeSpec.Http.AuthType}

Authentication type

```typespec
enum TypeSpec.Http.AuthType
```

### `ApiKeyLocation` {#TypeSpec.Http.ApiKeyLocation}

Describes the location of the API key

```typespec
enum TypeSpec.Http.ApiKeyLocation
```

### `OAuth2FlowType` {#TypeSpec.Http.OAuth2FlowType}

Describes the OAuth2 flow type

```typespec
enum TypeSpec.Http.OAuth2FlowType
```