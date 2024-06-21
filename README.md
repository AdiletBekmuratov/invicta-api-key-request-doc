## Endpoints

### Send prompt

#### Description

Provide a brief description of what this endpoint does.

#### HTTP Request

```http
POST /v1/endpoint-1
```

#### Parameters

| Parameter | Type   | Required | Description          |
|-----------|--------|----------|----------------------|
| param1    | string | Yes      | Description of param1|
| param2    | int    | No       | Description of param2|

#### Example Request

```http
POST /v1/endpoint-1 HTTP/1.1
Host: api.example.com
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json

{
  "param1": "value",
  "param2": 123
}
```

#### Example Response

```json
{
  "id": "resource_id",
  "attribute": "value"
}
```

---

## Errors

### Error Handling

The API uses standard HTTP status codes to indicate success or failure of an API request.

| Status Code | Meaning                |
|-------------|------------------------|
| 200         | OK                     |
| 400         | Bad Request            |
| 401         | Unauthorized           |
| 404         | Not Found              |
| 500         | Internal Server Error  |

### Example Error Response

```json
{
  "error": {
    "code": "invalid_request_error",
    "message": "Invalid parameter provided"
  }
}
```
