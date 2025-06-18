## 💥 Error Codes

| HTTP Status | Error Code                   | Description                                      |
|-------------|------------------------------|--------------------------------------------------|
| 400         | `REQUIRED_PARAMETER_MISSING` | One or more required parameters are missing.     |
| 400         | `INVALID_COORDINATE_FORMAT`  | Latitude or longitude format is invalid.         |
| 401         | `UNAUTHORIZED`               | API key is missing or invalid.                   |
| 403         | `FORBIDDEN`                  | The API key does not have access to this action. |
| 429         | `RATE_LIMIT_EXCEEDED`        | Too many requests in a short period.             |
| 500         | `INTERNAL_SERVER_ERROR`      | An unexpected server error occurred.             |
