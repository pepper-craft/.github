## 📄 Distance between two coordinates API

This is an HTTP API that calculates the straight-line distance between two points based on their latitude and longitude
coordinates.

---

## 👤 Recommended Reading Guide

| Purpose of Use                                   | Start with                                | Description                                                                                       |
|--------------------------------------------------|-------------------------------------------|---------------------------------------------------------------------------------------------------|
| ✅ First-time user                                | [🧭 Overview](#-1-overview)               | Understand what the API does through a visual explanation. Start with the basic concepts.         |
| ✅ Users starting integration development         | [📤 Request Details](#-2-request-details) | Learn the request and response formats to quickly integrate and test the API in your application. |
| ✅ Users who want to test or use the API directly | [🔗 Reference Links](#-5-reference-links) | Test the API in the RapidAPI console and get your API key to start making live calls.             |

---

## 📚 Table of Contents

1. [🧭 Overview](#-1-overview)
2. [📤 Request Details](#-2-request-details)
    1. [Request Example](#21-request-example)
    2. [Request Specifications](#22-request-specifications)
3. [📥 Response Details](#-3-response-details)
    1. [Response Example](#31-response-example)
    2. [Response Specifications](#32-response-specifications)
4. [💥 Error Response Examples](#-4-error-response-examples)
5. [🔗 Reference Links](#-5-reference-links)

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

| Field                | Type   | Required | Description                        |
|----------------------|--------|----------|------------------------------------|
| `fromCoordinate.lat` | number | ✅ Yes    | Latitude of the starting point     |
| `fromCoordinate.lng` | number | ✅ Yes    | Longitude of the starting point    |
| `toCoordinate.lat`   | number | ✅ Yes    | Latitude of the destination point  |
| `toCoordinate.lng`   | number | ✅ Yes    | Longitude of the destination point |

---

## 📥 3. Response Details

### 3.1 Response Example

```json
{
  "distance": 47.1732,
  "unit": "m"
}
```

### 3.2 Response Specifications

| Field           | Type    | Nullable | Description                                        |
|-----------------|---------|----------|----------------------------------------------------|
| `success`       | boolean | ❌ No     | Indicates whether the operation succeeded          |
| `data`          | object  | ❌ No     | Included only when `success` is `true`             |
| `data.distance` | number  | ❌ No     | Distance between coordinates (4 decimal precision) |
| `data.unit`     | string  | ❌ No     | Unit of measurement (e.g. `m`, `km`, `mi`)         |

---

## 💥 4. Error Response Examples

```json
{
  "success": false,
  "error": {
    "code": 400,
    "message": "Invalid input: 'lat' and 'lng' are required."
  }
}
```

| Field           | Type    | Description                         |
|-----------------|---------|-------------------------------------|
| `success`       | boolean | Always `false` when an error occurs |
| `error.code`    | number  | HTTP status code                    |
| `error.message` | string  | Description of the error            |

---

## 🔗 5. Reference Links

---

[Go to API List](../index.md)