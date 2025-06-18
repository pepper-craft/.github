## 📄 Distance between two coordinates API

> This is an HTTP API that calculates the shortest distance over the Earth's surface (Great-circle distance) between two
> points specified by latitude and longitude.

---

## 📚 Table of Contents

1. [🧭 Overview](#-1-overview) — *For first-time users*
2. [📤 Request Details](#-2-request-details) — *For developers integrating the API*
    1. [Request Example](#21-request-example)
    2. [Request Specifications](#22-request-specifications)
3. [📥 Response Details](#-3-response-details)
    1. [Response Example](#31-response-example)
    2. [Response Specifications](#32-response-specifications)
4. [💥 Error Response Examples](#-4-error-response-examples)
5. [🔗 Reference Links](#-5-reference-links) — *For testing the API and retrieving your API key*

---

## 🧭 1. Overview

![distance-between-two-coordinates](./img/distance-between-two-coordinates.png)

This image is a **visual representation of the distance between two geographic coordinates**.
Points **A** and **B** are defined by their **latitude** and **longitude**, forming geographic coordinates.
While the image illustrates the distance as a **straight line on a flat surface** for simplicity,
it actually represents the **shortest path over the Earth’s surface**, known as the **Great-circle distance**.
The API below takes two such coordinates as input and returns the **calculated shortest distance on Earth**.


---

## 📤 2. Request Details

### 2.1 Request Example

```http request
POST {{base-url}}/distance/between-coordinates?unit=mm
Content-Type: application/json

{
  "fromCoordinate": {
    "lat": 37.618515,
    "lng": 126.920021
  },
  "toCoordinate": {
    "lat": 37.618385,
    "lng": 126.920339
  }
}
```

### 2.2 Request Specifications

**2.2.1. Base Endpoint Info**

| **API Provider Platform** | **Method** | **Base URL(HTTP Protocol + Host)** | **Path**                        |
|:-------------------------:|:----------:|------------------------------------|:--------------------------------|
|         Rapid API         |    POST    | `https://yourapi.p.rapidapi.com`   | `/distance/between-coordinates` |

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

| Field            | Type   | Required | Description                        |
|------------------|--------|----------|------------------------------------|
| `fromCoordinate` | object | ✅ Yes    | Starting point coordinates         |
| └`lat`           | number | ✅ Yes    | Latitude of the starting point     |
| └`lng`           | number | ✅ Yes    | Longitude of the starting point    |
| `toCoordinate`   | object | ✅ Yes    | Destination point coordinates      |
| └`lat`           | number | ✅ Yes    | Latitude of the destination point  |
| └`lng`           | number | ✅ Yes    | Longitude of the destination point |

---

## 📥 3. Response Details

### 3.1 Response Example

```json
{
  "success": true,
  "data": {
    "distance": 31.4989,
    "unit": "m"
  }
}
```

### 3.2 Response Specifications

| Field       | Type    | Nullable | Description                                        |
|-------------|---------|----------|----------------------------------------------------|
| `success`   | boolean | ❌ No     | Indicates whether the operation succeeded          |
| `data`      | object  | ❌ No     | Included only when `success` is `true`             |
| └`distance` | number  | ❌ No     | Distance between coordinates (4 decimal precision) |
| └`unit`     | string  | ❌ No     | Unit of measurement (e.g. `m`, `km`, `mi`)         |

---

## 💥 4. Error Response Examples

```json
{
  "success": false,
  "code": "REQUIRED_PARAMETER_MISSING",
  "message": "Required parameter is missing.",
  "detailMessage": "Required parameter is missing. (fromCoordinate)"
}
```

| Field           | Type    | Nullable | Description                                                          |
|-----------------|---------|----------|----------------------------------------------------------------------|
| `success`       | boolean | ❌ No     | Indicates whether the operation was successful. Always `false` here. |
| `code`          | string  | ❌ No     | Application-defined error code representing the type of failure.     |
| `message`       | string  | ❌ No     | General explanation of the error.                                    |
| `detailMessage` | string  | ❌ No     | Detailed context or location of the error, useful for debugging.     |

---

## 🔗 5. Reference Links

---

[Go to API List](../index.md)