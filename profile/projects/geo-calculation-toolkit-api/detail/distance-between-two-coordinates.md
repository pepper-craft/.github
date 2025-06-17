## 📄 Distance between two coordinates API

두 지점(A, B)의 위도/경도를 입력받아 두 지점 사이의 거리(직선 거리)를 계산하는 HTTP API입니다.

## 👤 독자 유형별 읽기 추천 가이드

| 사용 목적                     | 먼저 읽을 항목                                                           | 설명                                                         |
|---------------------------|--------------------------------------------------------------------|------------------------------------------------------------|
| ✅ 처음 접하는 사용자              | [개요 + 이미지 설명](#-개요--이미지-설명)                                        | API가 어떤 역할을 하는지 시각적으로 이해할 수 있습니다. 지리 좌표와 거리 계산 개념부터 접근하세요. |
| ✅ 연동 개발을 시작하려는 사용자        | [요청/응답 스펙](#-요청-스펙), [요청 예시](#-요청-예시-http-파일-형식), [응답 예시](#-응답-예시) | 실제 요청 형식과 응답 구조를 통해 API 통신 형식을 익히고, 개발에 바로 활용할 수 있습니다.     |
| ✅ API 테스트 또는 바로 사용하려는 사용자 | [참고 링크](#-참고-링크)                                                   | RapidAPI 콘솔에서 테스트하고, API 키를 발급받아 실시간 호출을 진행하세요.            |

## 📚 목차

1. [Overview](#1.-Overview)
2. [Request Details](#-요청-스펙)
    1. Request Example
    2. Request Specifications
3. [Response Details](#-응답-스펙)
    1. Response Example
    2. Response Specifications
4. [Error Response Examples](#-실패-응답-예시)
5. [Reference Links](#-참고-링크)


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

#### **Base Endpoint Info**

**Base Endpoint Info**

| **API Provider Platform** | **Method** | **Base URL(HTTP Protocol + Host)** | **Path**                      |
|:-------------------------:|:----------:|------------------------------------|:------------------------------|
|         Rapid API         |    POST    | https://yourapi.p.rapidapi.com     | /distance/between-coordinates |

#### Request Headers

#### Query Parameters

#### Request Body

## 📥 3. Response Details

## 💥 4. Error Response Examples

## 🔗 4. Reference Links

---

[Go to API List](../index.md)