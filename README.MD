# Request Limit

A Python package for FastAPI that provides a decorator to limit the rate of requests based on specified parameters.

## Installation

```bash
pip install fastapi-request-limit
```

### Usage

Here's how you can use the `request-limit` decorator in a FastAPI application:~

```python
from fastapi import FastAPI, Request
from fastapi.responses import JSONResponse
from fastapi_request_limit import request_limit

app = FastAPI()

@app.post("/", response_class=JSONResponse)
@request_limit(seconds=5, data=["foo", "bar"])
async def root(foo: str, bar: int, request: Request):
    return JSONResponse(content={"message": f"Request accepted for {foo} and {bar}"})
```

### Parameters
- *seconds (int)*: The number of seconds required between requests with the same parameter values.
- *data (List[str])*: A list of parameter names to use for rate limiting.