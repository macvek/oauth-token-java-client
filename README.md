# OAuth JWT Assertion Client for Java #

## Description ##
Client helper for OAuth 2.0 "Client Credentials" flow with RS256 JWT "client_assertion".

## Features ##
- Client Credentials Grant (2-Legged OAuth)
- "private_key_jwt" authentication method as defined in [Assertion Framework for OAuth 2.0 Client Authentication and Authorization Grants](https://tools.ietf.org/html/rfc7521#section-6.2) and [OpenID Connect Core 1.0](http://openid.net/specs/openid-connect-core-1_0.html#ClientAuthentication)
- **Access token caching**. Uses in-memory cache by default. Caching key includes all parameters, so it is safe to use with more than one Authorization Server, credential set or OAuth scope list.

_If you need support for other grant types or authentication methods, please check [Google OAuth Client Library](https://github.com/google/google-oauth-java-client) or another implementation._

## Getting started ##
Install with Maven:
```xml
<dependency>
    <groupId>com.scalepoint</groupId>
    <artifactId>oauth-jwt-assertion-client</artifactId>
    <version>0.1.0</version>
</dependency>
```

Obtaining access token from Authorization Server token endpoint is as simple as this:

```java
TokenClient tokenClient = new JwtAssertionTokenClient(tokenEndpointUri, clientId, keyPair);
String accessToken = tokenClient.getToken("scope1", "scope2");
```

_Check [here](src/test/java/com/scalepoint/jwt_assertion_client/TestCertificateHelper.java) for how you can load "keyPair" from .jks or .pfx file containing only one certificate and key for test purposes._