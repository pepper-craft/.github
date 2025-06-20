## Shortest distance from a coordinate to a line

This is an HTTP API that calculates the shortest surface distance from a given coordinate to a straight line defined by
two geographic points.


---

## 📚 Table of Contents

1. [🧭 Overview](#-1-overview) — *For first-time users*
2. [📤 Request Details](#-2-request-details) — *For developers integrating the API*
    1. [Request Example](#21-request-example)
    2. [Request Specifications](#22-request-specifications)
3. [📥 Response Details](#-3-response-details)
    1. [Response Example](#31-response-example)
    2. [Response Specifications](#32-response-specifications)
4. [💥 Error Response Details](#-4-error-response-details)
    1. [Error Response Example](#41-error-response-example)
    2. [Error Response Specifications](#42-error-response-specifications)
    3. [Error Codes](#43-error-codes)
5. [🔗 Reference Links](#-5-reference-links) — *For testing the API and retrieving your API key*

---

## 🧭 1. Overview

![shortest-distance-from-a-coordinate-to-a-line](./img/shortest-distance-from-a-coordinate-to-a-line.png)

This image provides a visual explanation of how the API calculates the shortest distance from a coordinate to a single polyline.
Points A and B represent specific locations defined by latitude and longitude, while polyline C is a straight line segment formed by exactly two geographic coordinates.

- For point A, the shortest distance to polyline C is represented by the segment from A to point D, which lies on polyline C.
- For point B, the shortest distance is the segment from B to point E, also located on polyline C.

This API takes a single coordinate and a polyline consisting of two coordinates as input, and returns the shortest surface distance, taking the curvature of the Earth into account.

---

## 📤 2. Request Details

### 2.1. Request Example

```http request
POST {{base-url}}/distance/from-point-to-line/shortest?unit=mm
Content-Type: application/json

{
  "coordinate": {
    "lat": 37.618492,
    "lng": 126.920078
  },
  "line": {
    "fromCoordinate": {
      "lat": 37.618515,
      "lng": 126.920021
    },
    "toCoordinate": {
      "lat": 37.618385,
      "lng": 126.920339
    }
  }
}
```

### 2.2. Request Specifications

**2.2.1. Base Endpoint Info**

| API Provider Platform | Method | Base URL(HTTP Protocol + Host)   | Path                                    |
|:---------------------:|:------:|----------------------------------|:----------------------------------------|
|       Rapid API       |  POST  | `https://yourapi.p.rapidapi.com` | `/distance/from-point-to-line/shortest` |

**2.2.2. Request Headers**

| Header Name       | Type   | Required | Description                         |
|-------------------|--------|----------|-------------------------------------|
| `Content-Type`    | string | ✅ Yes    | Must be `application/json`          |
| `X-RapidAPI-Key`  | string | ✅ Yes    | Your API key issued by RapidAPI     |
| `X-RapidAPI-Host` | string | ✅ Yes    | The API host identifier on RapidAPI |

**2.2.3. Query Parameters**

| Parameter | Type   | Required   | Description                                                |
|-----------|--------|------------|------------------------------------------------------------|
| `unit`    | string | ❌ Optional | Distance unit (`mm`, `m`, `km`, `ft`, `mi`) - defaults `m` |

**2.2.4. Request Body**

| Field              | Type   | Required | Description                                                   |
|--------------------|--------|----------|---------------------------------------------------------------|
| `coordinate`       | object | ✅ Yes    | The point from which the shortest distance will be calculated |
| └ `lat`            | number | ✅ Yes    | Latitude of the input point                                   |
| └ `lng`            | number | ✅ Yes    | Longitude of the input point                                  |
| `line`             | object | ✅ Yes    | The line segment defined by two coordinates                   |
| └ `fromCoordinate` | object | ✅ Yes    | Starting point of the line                                    |
| └─ `lat`           | number | ✅ Yes    | Latitude of the starting point                                |
| └─ `lng`           | number | ✅ Yes    | Longitude of the starting point                               |
| └ `toCoordinate`   | object | ✅ Yes    | Ending point of the line                                      |
| └─ `lat`           | number | ✅ Yes    | Latitude of the ending point                                  |
| └─ `lng`           | number | ✅ Yes    | Longitude of the ending point                                 |

---

## 📥 3. Response Details

### 3.1. Response Example

```json
{
  "success": true,
  "data": {
    "distance": 31.4989,
    "unit": "m"
  }
}
```

### 3.2. Response Specifications

| Field       | Type    | Nullable | Description                                                                           |
|-------------|---------|----------|---------------------------------------------------------------------------------------|
| `success`   | boolean | ❌ No     | Indicates whether the operation succeeded                                             |
| `data`      | object  | ❌ No     | Included only when `success` is `true`                                                |
| └`distance` | number  | ❌ No     | Shortest surface distance from the input coordinate to the line (4 decimal precision) |
| └`unit`     | string  | ❌ No     | Unit of measurement (e.g. `m`, `km`, `mi`)                                            |

---

## 💥 4. Error Response Details

### 4.1. Error Response Example

```http request
400 Bad Request
Content-Type: application/json

{
  "success": false,
  "code": "REQUIRED_PARAMETER_MISSING",
  "message": "Required parameter is missing.",
  "detailMessage": "Required parameter is missing. (fromCoordinate)"
}
```

### 4.2. Error Response Specifications

**4.2.1. Error Response Headers**

| Header Name    | Example Value      | Description                    |
|----------------|--------------------|--------------------------------|
| `Content-Type` | `application/json` | MIME type of the response body |

**4.2.2. Error Response Body**

| Field           | Type    | Nullable | Description                                                                      |
|-----------------|---------|----------|----------------------------------------------------------------------------------|
| `success`       | boolean | ❌ No     | Indicates whether the operation was successful. Always `false` here.             |
| `code`          | string  | ❌ No     | Application-defined error code representing the type of failure.                 |
| `message`       | string  | ❌ No     | General explanation of the error.                                                |
| `detailMessage` | string  | ❌ No     | Additional information providing context about the error for debugging purposes. |

### 4.3. Error Codes

To view the full list of error codes, please visit the link below.

- [Error Codes](./common/error-codes.md)

---

## 🔗 5. Reference Links

- [🚀 Try the API on RapidAPI Console](https://rapidapi.com/your-api/test)  
  Run live requests, view sample code, pricing, and manage your API key—all in one place.


- [💬 Contact Support](mailto:support@yourapi.com)  
  If you have any questions or need help with the API, feel free to email us. We’ll get back to you as soon as possible.

---

[Go to API List](../index.md)