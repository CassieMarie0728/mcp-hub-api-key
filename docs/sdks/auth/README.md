# Auth
(*auth()*)

## Overview

Authentication and user session management

### Available Operations

* [postLogin](#postlogin) - User login with username and password
* [getCurrentUser](#getcurrentuser) - Get current authenticated user
* [postLogout](#postlogout) - Logout user and clear session cookie

## postLogin

Authenticates a user and starts a browser session. Programmatic clients may exchange the returned token for bearer-style access where supported.

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.components.AuthLoginBody;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.PostLoginResponse;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        AuthLoginBody req = AuthLoginBody.builder()
                .username("john.doe")
                .password("secret123")
                .build();

        PostLoginResponse res = sdk.auth().postLogin()
                .request(req)
                .call();

        if (res.inlineResponse2002().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                             | Type                                                  | Required                                              | Description                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `request`                                             | [AuthLoginBody](../../models/shared/AuthLoginBody.md) | :heavy_check_mark:                                    | The request object to use for the request.            |

### Response

**[PostLoginResponse](../../models/operations/PostLoginResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 400, 401                   | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getCurrentUser

Get current authenticated user

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetCurrentUserResponse;
import org.openapis.openapi.models.operations.GetCurrentUserSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        GetCurrentUserResponse res = sdk.auth().getCurrentUser()
                .security(GetCurrentUserSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.inlineResponse2003().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                          | Type                                                                                                               | Required                                                                                                           | Description                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| `security`                                                                                                         | [org.openapis.openapi.models.operations.GetCurrentUserSecurity](../../models/operations/GetCurrentUserSecurity.md) | :heavy_check_mark:                                                                                                 | The security requirements to use for the request.                                                                  |

### Response

**[GetCurrentUserResponse](../../models/operations/GetCurrentUserResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401                        | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## postLogout

Logout user and clear session cookie

### Example Usage

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.PostLogoutResponse;
import org.openapis.openapi.models.operations.PostLogoutSecurity;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        PostLogoutResponse res = sdk.auth().postLogout()
                .security(PostLogoutSecurity.builder()
                    .appSessionCookie("<YOUR_API_KEY_HERE>")
                    .build())
                .call();

        if (res.inlineResponse2001().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                                                                  | Type                                                                                                       | Required                                                                                                   | Description                                                                                                |
| ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `security`                                                                                                 | [org.openapis.openapi.models.operations.PostLogoutSecurity](../../models/operations/PostLogoutSecurity.md) | :heavy_check_mark:                                                                                         | The security requirements to use for the request.                                                          |

### Response

**[PostLogoutResponse](../../models/operations/PostLogoutResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/Error        | 401                        | application/json           |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |