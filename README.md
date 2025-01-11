# Google Maps Formulas for Google Sheets

## Overview
This Google Apps Script adds powerful Google Maps functionality directly to your Google Sheets through custom functions. It enables you to calculate distances, get directions, lookup addresses, and more without leaving your spreadsheet.

## Key Benefits
- **No API Key Required**: Uses Google Apps Script's built-in `Maps` service
- **Automatic Authentication**: Leverages your Google Workspace credentials
- **Zero Configuration**: No billing or API setup needed
- **Seamless Integration**: Works directly within Google Sheets

## How It Works
This script uses the built-in `Maps` service in Google Apps Script, which is pre-authenticated and different from the public Google Maps API. It automatically uses your Google Workspace credentials, making it much simpler than traditional Google Maps integrations that require API keys and billing setup.

## Installation

1. Open your Google Sheets document
2. Go to Extensions > Apps Script
3. Copy and paste the entire script code into the Apps Script editor
4. Save the project
5. Return to your spreadsheet and refresh the page

No additional setup or API configuration is required!

## Available Functions
### `GOOGLEMAPS_DURATION(origin, destination, [apiKey], [departureTime])`
Returns the travel duration between two locations.
- `origin`: Starting location (address or coordinates)
- `destination`: Ending location (address or coordinates)
- `apiKey`: (Optional) Google Maps API key. If not provided, will use script property
- `departureTime`: (Optional) Desired departure time as Date object
- Returns: String with formatted duration (e.g., "1 hour 23 mins")

Example:
```
=GOOGLEMAPS_DURATION("New York, NY", "Boston, MA")
```
Returns: `3 hours 57 mins`

### `GOOGLEMAPS_DURATION_MINS(origin, destination, [apiKey], [departureTime])`
Returns the travel duration between two locations in minutes.
- `origin`: Starting location (address or coordinates)
- `destination`: Ending location (address or coordinates)
- `apiKey`: (Optional) Google Maps API key. If not provided, will use script property
- `departureTime`: (Optional) Desired departure time as Date object
- Returns: Number with total minutes (e.g., 83)

Example:
```
=GOOGLEMAPS_DURATION_MINS("New York, NY", "Boston, MA")
```
Returns: `237`

### `GOOGLEMAPS_DISTANCE(origin, destination, [apiKey], [departureTime])`
Returns the travel distance between two locations.
- `origin`: Starting location (address or coordinates)
- `destination`: Ending location (address or coordinates)
- `apiKey`: (Optional) Google Maps API key. If not provided, will use script property
- `departureTime`: (Optional) Desired departure time as Date object
- Returns: String with formatted distance (e.g., "12.4 mi")

Example:
```
=GOOGLEMAPS_DISTANCE("New York, NY", "Boston, MA")
```

### GOOGLEMAPS_LATLONG
Returns the latitude and longitude of an address.
```
=GOOGLEMAPS_LATLONG("address")
```
- **Example:**
  ```
  =GOOGLEMAPS_LATLONG("10 Hanover Square, NY")
  ```

### `GOOGLEMAPS_ADDRESS(latitude, longitude, [apiKey])`
Returns the formatted address for given coordinates.
- `latitude`: Latitude coordinate
- `longitude`: Longitude coordinate
- `apiKey`: (Optional) Google Maps API key. If not provided, will use script property
- Returns: String with formatted address

Example:
```
=GOOGLEMAPS_ADDRESS(40.7127753, -74.0059728)
```
Returns: `10 Hanover Square, New York, NY 10005, USA`

### `GOOGLEMAPS_REVERSEGEOCODE(latitude, longitude, [apiKey])`
Returns the address components for given coordinates.
- `latitude`: Latitude coordinate
- `longitude`: Longitude coordinate
- `apiKey`: (Optional) Google Maps API key. If not provided, will use script property
- Returns: Array with address components [street number, route, city, state, country, postal code]

Example:
```
=GOOGLEMAPS_REVERSEGEOCODE(40.7127753, -74.0059728)
```
Returns: `["10", "Hanover Square", "New York", "NY", "United States", "10005"]`

### GOOGLEMAPS_COUNTRY
Returns the country name and code for an address.
```
=GOOGLEMAPS_COUNTRY("address")
```
- **Example:**
  ```
  =GOOGLEMAPS_COUNTRY("10 Hanover Square, NY")
  ```

### `GOOGLEMAPS_DIRECTIONS(origin, destination, [apiKey])`
Returns turn-by-turn directions between two locations.
- `origin`: Starting location (address or coordinates)
- `destination`: Ending location (address or coordinates)
- `apiKey`: (Optional) Google Maps API key. If not provided, will use script property
- Returns: Array with step-by-step directions

Example:
```
=GOOGLEMAPS_DIRECTIONS("New York, NY", "Boston, MA")
```
Returns: `["Head northeast on Broadway", "Turn right onto Park Row", ...]`



## Technical Details

### Authentication and API Access
- Uses Google Apps Script's built-in `Maps` service
- No API key or billing setup required
- Automatically authenticates using your Google Workspace credentials
- Subject to Google Workspace quotas (not Google Maps API quotas)

### Caching
- The script implements caching to improve performance and reduce API calls
- Cache duration: 6 hours
- Uses MD5 hashing for cache keys

### Error Handling
The script includes robust error handling for common scenarios:
- Missing addresses
- Invalid routes
- Unfound locations
- Missing coordinates

## Requirements
- Google Sheets
- Google Workspace account
- That's it! No additional API setup needed

## Important Notes
- This code only works within Google Apps Script
- Cannot be used in regular JavaScript environments
- Uses different syntax from the regular Google Maps JavaScript API
- Instead of `google.maps.DirectionsService`, it uses Apps Script's `Maps` service

## Limitations
- Cache entries expire after 6 hours
- Subject to Google Workspace quotas
- Functions must be used within Google Sheets
- Code is specific to Google Apps Script and cannot be used in other JavaScript environments

## Contributing
This script was inspired by [labnol.org](https://labnol.org/google-maps-formulas-for-sheets-200817). I have made some modifications to meet my specific use cases. For updates and more information, visit the their website.
