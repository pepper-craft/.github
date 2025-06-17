## 📄 Distance between two coordinates API

두 지점(A, B)의 위도/경도를 입력받아 두 지점 사이의 거리(직선 거리)를 계산하는 HTTP API입니다.

## 👤 Recommended Reading Guide

| Purpose of Use            | Start with...                             | Description                                                                                       |
|---------------------------|-------------------------------------------|---------------------------------------------------------------------------------------------------|
| ✅ 처음 접하는 사용자              | [🧭 Overview](#-1-overview)               | Understand what the API does through a visual explanation. Start with the basic concepts.         |
| ✅ 연동 개발을 시작하려는 사용자        | [📤 Request Details](#-2-request-details) | Learn the request and response formats to quickly integrate and test the API in your application. |
| ✅ API 테스트 또는 바로 사용하려는 사용자 | [🔗 Reference Links](#-5-reference-links) | Test the API in the RapidAPI console and get your API key to start making live calls.             |

## 📚 Table of Contents

1. [🧭 Overview](#-1-overview)
2. [📤 Request Details](#-2-request-details)
    1. [Request Example](#-21-request-example)
    2. [Request Specifications](#-22-request-spec)
3. [📥 Response Details](#-3-response-details)
    1. [Response Example](#-31-response-example)
    2. [Response Specifications](#-32-response-specifications)
4. [💥 Error Response Examples](#-4-error-response-examples)
5. [🔗 Reference Links](#-5-reference-links)

## 🧭 1. Overview

![distance-between-two-coordinates](./img/distance-between-two-coordinates.png)

This API calculates and returns the shortest distance between two geographic coordinates (latitude and longitude) on the
Earth's surface.
The default unit for the returned distance is meters, with options to calculate in feet and miles as needed.

[//]: # (
지표상 위도/경도로 구성된 두 좌표 사이의 최단 거리를 계산하고 반환하는 API 입니다.
반환하는 거리의 기본 단위는 미터이며 필요에 따라 피트와 마일 단위로도 계산할 수 있습니다.
)

## 📤 2. Request Details

### 2.1 Request Example

```http request
# Distance Between Two Coordinates API reqeust example
POST {{host}}/distance/between-coordinates?unit=mm
Content-Type: application/json

{
  "fromCoordinate": {
    "lat": 37.61851599854798,
    "lng": 126.92002132129107
  },
  "toCoordinate": {
    "lat": 37.618385433468916,
    "lng": 126.9203394433419
  }
}
```

### 2.2 Request Spec

#### Base Endpoint Info

| **API Provider Platform** | **Method** | **Base URL(HTTP Protocol + Host)** | **Path**                        |
|:-------------------------:|:----------:|------------------------------------|:--------------------------------|
|         Rapid API         |    POST    | `https://yourapi.p.rapidapi.com`   | `/distance/between-coordinates` |

#### Request Headers

| Header Name       | Type   | Required | Description                         |
|-------------------|--------|----------|-------------------------------------|
| `Content-Type`    | string | ✅        | Must be `application/json`          |
| `X-RapidAPI-Key`  | string | ✅        | Your API key issued by RapidAPI     |
| `X-RapidAPI-Host` | string | ✅        | The API host identifier on RapidAPI |

#### Query Parameters

| Parameter | Type   | Required   | Description                                                   |
|-----------|--------|------------|---------------------------------------------------------------|
| `unit`    | string | ❌ Optional | Distance unit (`mm`, `m`, `km`, `ft`, `mi`) — defaults to `m` |

#### Request Body

```json
{
  "fromCoordinate": {
    "lat": 37.61851599854798,
    "lng": 126.92002132129107
  },
  "toCoordinate": {
    "lat": 37.618385433468916,
    "lng": 126.9203394433419
  }
}
```

## 📥 3. Response Details

### 3.1 Response Example

```json
{
  "distance": 47.0,
  "unit": "m"
}
```

### 3.2 Response Specifications

| Field           | Type    | Nullable | Description                                        |
|-----------------|---------|----------|----------------------------------------------------|
| `success`       | boolean | ❌        | Indicates whether the operation succeeded          |
| `data`          | object  | ❌        | Included only when `success` is `true`             |
| `data.distance` | number  | ❌        | Distance between coordinates (4 decimal precision) |
| `data.unit`     | string  | ❌        | Unit of measurement (e.g. `m`, `km`, `mi`)         |

| Field           | Type    | Description                                                |
|-----------------|---------|------------------------------------------------------------|
| `success`       | boolean | Indicates whether the operation succeeded                  |
| `data`          | object  | Contains the result of the calculation                     |
| `data.distance` | number  | Distance between coordinates (precision: 4 decimal places) |
| `data.unit`     | string  | Unit of measurement used in the response                   |

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

## 🔗 4. Reference Links

---

[Go to API List](../index.md)