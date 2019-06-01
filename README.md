# jurisdictions

Each JSON file will be automatically imported as districts and associated legislators.

## Schema

Each file must have the following schema:

```json
{
  "label": "Legislature name",
  "short_label": "Legislature abbreviation",
  "session": 20192020,
  "districts": [
    {
      "type": "Feature",
      "geometry": {...},
      "properties": {
        "label": "District name",
        "short_label": "District abbreviation",
        "district": 19,
        "office_holder": {
          "first_name": "First",
          "last_name": "Last",
          "email": "legislator@email.gov",
          "phone": "(608) 825-1465",
          "username": "RepFirstLast",
          "twitter_username": null,
          "image_url": null
        }
      }
    }
  ]
```

### Schema notes

- `districts` field must be valid GeoJSON.
- All `office_holder` fields are required except `twitter_username` and `image_url`.
- Vacant districts have `"office_holder": null`.
- Sessions can be any number, but best if they are concatenation of session years. For example `2020` or `20192020`.
- `short_label`'s should be 10 characters or less.
