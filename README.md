# Google Maps Formulas for Google Sheets

## Overview
This Google Apps Script adds powerful Google Maps functionality directly to your Google Sheets through custom functions. It enables you to calculate distances, get directions, lookup addresses, and more without leaving your spreadsheet.

## Features
- Calculate travel time between locations
- Measure distances between points
- Get latitude and longitude coordinates
- Look up full addresses from zip codes
- Reverse geocode coordinates to addresses
- Get country information for any address
- Generate turn-by-turn directions

## Installation

1. Open your Google Sheets document
2. Go to Extensions > Apps Script
3. Copy and paste the entire script code into the Apps Script editor
4. Save the project
5. Return to your spreadsheet and refresh the page

## Available Functions

### GOOGLEMAPS_DURATION
Calculates travel time between two locations.
```
=GOOGLEMAPS_DURATION("origin", "destination", "mode")
```
- **Parameters:**
  - origin: Starting address
  - destination: Ending address
  - mode: "driving" (default), "walking", "bicycling", or "transit"
- **Example:**
  ```
  =GOOGLEMAPS_DURATION("UT 84060", "Salt Lake City Utah", "walking")
  ```

### GOOGLEMAPS_DISTANCE
Calculates the distance between two locations.
```
=GOOGLEMAPS_DISTANCE("origin", "destination", "mode")
```
- **Parameters:**
  - origin: Starting address
  - destination: Ending address
  - mode: "driving" (default), "walking", "bicycling", or "transit"
- **Example:**
  ```
  =GOOGLEMAPS_DISTANCE("Park City Utah 84060", "Salt Lake City Utah", "walking")
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

### GOOGLEMAPS_ADDRESS
Returns the full address from a zip code or partial address.
```
=GOOGLEMAPS_ADDRESS("partial_address")
```
- **Example:**
  ```
  =GOOGLEMAPS_ADDRESS("10005")
  ```

### GOOGLEMAPS_REVERSEGEOCODE
Converts latitude and longitude coordinates to an address.
```
=GOOGLEMAPS_REVERSEGEOCODE(latitude, longitude)
```
- **Parameters:**
  - latitude: Decimal latitude coordinate
  - longitude: Decimal longitude coordinate

### GOOGLEMAPS_COUNTRY
Returns the country name and code for an address.
```
=GOOGLEMAPS_COUNTRY("address")
```
- **Example:**
  ```
  =GOOGLEMAPS_COUNTRY("10 Hanover Square, NY")
  ```

### GOOGLEMAPS_DIRECTIONS
Provides turn-by-turn directions between two locations.
```
=GOOGLEMAPS_DIRECTIONS("origin", "destination", "mode")
```
- **Parameters:**
  - origin: Starting address
  - destination: Ending address
  - mode: "driving" (default), "walking", "bicycling", or "transit"
- **Example:**
  ```
  =GOOGLEMAPS_DIRECTIONS("NY 10005", "Hoboken NJ", "walking")
  ```

## Technical Details

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
- Google Maps API access (automatically available through Google Apps Script)
- Active Google Workspace account

## Limitations
- Cache entries expire after 6 hours
- Subject to Google Maps API quotas and limits
- Functions must be used within Google Sheets

## Contributing
This script is maintained by [labnol.org](https://labnol.org/google-maps-formulas-for-sheets-200817). For updates and more information, visit the official website.
