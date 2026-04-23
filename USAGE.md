<!-- Start SDK Example Usage [usage] -->
```python
# Synchronous Example
from cassie_marie_mcp_hub_api_python import McpHubAPIPython


with McpHubAPIPython() as mcp_hub_api_python:

    res = mcp_hub_api_python.system.get_system_health(timestamp=6433.07)

    # Handle response
    print(res)
```

</br>

The same SDK client can also be used to make asychronous requests by importing asyncio.
```python
# Asynchronous Example
import asyncio
from cassie_marie_mcp_hub_api_python import McpHubAPIPython

async def main():

    async with McpHubAPIPython() as mcp_hub_api_python:

        res = await mcp_hub_api_python.system.get_system_health_async(timestamp=6433.07)

        # Handle response
        print(res)

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->