# Snap21 Reviews API

This repository provides API documentation for accessing customer reviews via Snap21.

## Overview
The Snap21 API allows you to retrieve customer reviews for a specific organization. The data includes:
- Average star rating
- Total review count
- Individual reviews with ratings, comments, and timestamps

## API Endpoint
```
GET https://snap21.com/api/v1/reviews?orgId={orgId}
```

### Example Request
```http
GET https://snap21.com/api/v1/reviews?orgId=38007
```

### Example Response
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

## Getting Started
1. Make a GET request to the API endpoint with the required `orgId` parameter.
2. Parse the JSON response to extract review details.
3. Handle errors appropriately (e.g., missing parameters, invalid `orgId`).

## License
This API documentation is provided for reference purposes. Ensure compliance with Snap21's API terms of use.
