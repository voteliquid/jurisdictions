# jurisdictions

Each JSON file will be automatically imported as districts and associated legislators.

To get the JSON file, you have to get shapefiles covering the districts and convert to JSON.

## identify shapefiles
Search the jurisdiction name + legislature name + districts + shapefiles, gis, ERSI, or datasets

Eg: San Francisco city & county board of supervisors districts shapefiles

That will usually lead you to a site that has the shapefiles already posted or an email address for the data team you need to contact. If not, browse the government website for a tech team and contact them.

The county will often have these files for smaller cities and towns.

### Converting shape files to JSON
Upload the zip file to https://mygeodata.cloud/converter/shp-to-json

Find "Coordinate system" under Output Data/Output parameters. Click "(the same as input)" and select WGS 84

Finish the conversion

#### Schema

Each file must have the following schema:

```json
{
  "label": "San Francisco City Council",
  "short_label": "San Francisco",
  "locality": "San Francisco",
  "administrative_area_level_2": "San Francisco County",
  "administrative_area_level_1": "California",
  "session": 20192020,
  "districts": [
    {
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

##### Schema notes

- `districts` field must be valid GeoJSON.
- All `office_holder` fields are required except `twitter_username` and `image_url`.
- Vacant districts have `"office_holder": null`.
- Sessions can be any number, but best if they are concatenation of session years. For example `2020` or `20192020`.
- `short_label`'s should be 10 characters or less.
