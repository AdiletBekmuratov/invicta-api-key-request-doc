## Endpoints

### Send prompt

#### Description

Provide a brief description of what this endpoint does.

#### HTTP Request

```http
POST https://api.invictai.io/api/triggers/webhooks/api-key/{AI_AGENT_ID}
```

#### Headers

| Parameter | Type   | Required | Description          |
|-----------|--------|----------|----------------------|
| X-INVICTA-API    | string | Yes      | An API key is a unique identifier used to authenticate a request to an API. This ensures that only authorized requests can activate the webhook, enhancing security and preventing unauthorized access. |

#### Parameters

| Parameter | Type   | Required | Description          |
|-----------|--------|----------|----------------------|
| userInput | string | Yes      | It is the prompt that initiates the AI agent's response. |
| variables | \{ key: string, value: string \| number \}\[\] | Yes      | This parameter allows users to dynamically control certain parts of the system prompt by specifying key-value pairs. By including this parameter, users can customize and modify specific elements of the system prompt at the time of the request, providing greater flexibility and control over the AI agent's behaviour. If the AI agent doesn't have any variables, the array should be empty. |
| threadId | string    | No       | It represents the thread identifier that stores the AI agent's memory, allowing the system to consider previous messages in its response. Including this parameter enables contextual continuity in the conversation with the AI agent. If the request doesn't include this parameter, a new thread will be created automatically and can be used for subsequent requests. |
| modelName | string | No      | It specifies the name of the model that the AI agent will utilize to process the request. Including this parameter allows you to select a particular model for generating responses, offering flexibility in the AI agent's behaviour and capabilities. |

#### Example Request

```curl
curl -X POST https://api.invictai.io/api/triggers/webhooks/api-key/{AI_AGENT_ID} \
-H "Content-Type: application/json" \
-H "X-INVICTA-API: cb8fb709-3ffb-4b0b-994d-5523f2f4438f" \
-d '{
  "userInput": "What kind of assistance can the AI provide on the website?",
  "threadId": "bdd3a319-af01-494f-bc86-892bd41c3e21",
  "modelName": "gpt-4o",
  "variables": []
}'
```

#### Response Type

```typescript
{
  "id": number
  "prompt": string
  "response": string
  "communityId": string | null
  "userId": number | null
  "liked": boolean | null
  "totalTokens": number | null
  "cp_cost": number
  "savedToMemory": boolean
  "csv_request_id": string | null
  "ai_agent_request_id": number | null
  "modelName": string | null
  "threadId": string | null
  "createdAt": Date
  "updatedAt": Date
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
