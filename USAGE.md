<!-- Start SDK Example Usage [usage] -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.McpHubApiJava;
import org.openapis.openapi.models.errors.Error;
import org.openapis.openapi.models.operations.GetSystemHealthResponse;

public class Application {

    public static void main(String[] args) throws Error, Exception {

        McpHubApiJava sdk = McpHubApiJava.builder()
            .build();

        GetSystemHealthResponse res = sdk.system().getSystemHealth()
                .timestamp(6433.07)
                .call();

        if (res.inlineResponse200().isPresent()) {
            // handle response
        }
    }
}
```
<!-- End SDK Example Usage [usage] -->