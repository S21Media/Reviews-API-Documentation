# Snap21 Reviews API Documentation

## Endpoint
### GET `/api/v1/reviews`
This endpoint retrieves customer reviews for a specific organization.

### Base URL
```
https://snap21.com
```

## Request Parameters
| Parameter | Type   | Required | Description |
|-----------|--------|----------|-------------|
| `orgId`   | `integer` | Yes      | The unique organization ID for which reviews are requested. |

### Example Request
```http
GET https://snap21.com/api/v1/reviews?orgId=38007
```

---

## Response
### Success Response
- **HTTP Status Code:** `200 OK`
- **Content-Type:** `application/json`
- **Response Body Structure:**
```json
{
  "aggregates": {
    "avgStarRating": 4.9,
    "reviewCount": 3847
  },
  "reviews": [
    {
      "id": 663107,
      "comments": "Everything went smooth and excellently.",
      "timestamp": "2025-03-04 20:44:18",
      "rating": 5,
      "photoUrl": "https://snap21.com/photo/view/thumbnail.php?noCount=true&snapId=174098079128020",
      "reviewUrl": "https://snap21.com/reviews/adelaide-vehicle-centre-enfield-sa?review=663107"
    }
  ]
}
```

---

## Response Fields
### Aggregates Object
| Field          | Type     | Description |
|---------------|----------|-------------|
| `avgStarRating` | `float`  | The average star rating of all reviews. |
| `reviewCount`   | `integer` | The total number of reviews available for the organization. |

### Reviews Array
Each review object contains the following fields:

| Field      | Type      | Description |
|------------|----------|-------------|
| `id`       | `integer` | Unique identifier for the review. |
| `comments` | `string`  | The customer’s review text. |
| `timestamp` | `string` (ISO 8601) | Date and time when the review was posted (`YYYY-MM-DD HH:mm:ss`). |
| `rating`   | `integer` | The star rating given by the reviewer (1-5). |
| `photoUrl` | `string` (URL) | URL of the review's associated image (if available). |
| `reviewUrl` | `string` (URL) | URL to view the full review on the Snap21 website. |

---

## Example Usage
### Fetch Reviews for Organization ID 38007
#### Request
```http
GET https://snap21.com/api/v1/reviews?orgId=38007
```

#### Response
```json
{
  "aggregates": {
    "avgStarRating": 4.9,
    "reviewCount": 3847
  },
  "reviews": [
    {
      "id": 663107,
      "comments": "Everything went smooth and excellently.",
      "timestamp": "2025-03-04 20:44:18",
      "rating": 5,
      "photoUrl": "https://snap21.com/photo/view/thumbnail.php?noCount=true&snapId=174098079128020",
      "reviewUrl": "https://snap21.com/reviews/adelaide-vehicle-centre-enfield-sa?review=663107"
    }
  ]
}
```

---

## Error Handling
| HTTP Status Code | Meaning | Description |
|------------------|---------|-------------|
| `400 Bad Request` | Invalid Request | Missing or invalid `orgId` parameter. |
| `401 Unauthorized` | Unauthorized | Authentication is required. |
| `403 Forbidden` | Forbidden | Access to this resource is denied. |
| `404 Not Found` | Not Found | The requested `orgId` does not exist. |
| `500 Internal Server Error` | Server Error | An unexpected error occurred on the server. |

---

## Notes
- The API returns a list of reviews for a given organization.
- The `photoUrl` field is optional and may not be present in every review.
- The `timestamp` follows the `YYYY-MM-DD HH:mm:ss` format.
