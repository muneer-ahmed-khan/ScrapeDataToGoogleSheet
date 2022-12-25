# ScrapeDataToGoogleSheet
Scrape data from a web site, then output data to a Google Sheet

## Test Client Project Requirements are listed below.

## **- Goal**
_- Scrape data from a web site, then output data to a Google Sheet_

## **- Tools**
- Use NodeJS and googleapis JS-based libraries. For web scraping, use Puppeteer
- Please use the below libraries:
        _- Node_
        _- Express_
        _- Googleapis_
        _- Puppeteer_


## - Task Details:
- Create Node script and log into the Google API using OAuth2 so you can access
Google Sheets using Node
- Create a node cronjob that runs once daily
- The cronjob should call function fetchSnapStaysResults
- Create a function fetchSnapStaysResults
- Function should take an array as input that is a string of cities, for example ['atlanta','dallas','las vegas']
- The function should iterate through each city, one at a time (asynchronously in series)
#### - For each city, the function should:
    - Go to https://search.snapstays.com/userDash
    - Enter the relevant city in the Location field
    - For the Check-in date, enter a date 7 days from the current date
    - For Check-out date, enter a date 3-months from the Check-in date
    - So if current date is Nov 3, Check-in date should be Nov 10, and Check-out date should be Feb 10
    - If current date is Nov 20, Check-in date should be Nov 27, and Check-out date should be Feb 27
    - Leave “Bedrooms” as 1
    - Run the Search

#### - Using the data that is returned, for each property returned add the following to a Results array:
- City
- Property name
- rcId
- Price
- LastUpdated

- Go to the next city in the fetchSnapStaysResults input array

- When complete iterating through all cities, create a new tab in the Google
sheet with the current date in this format: 2022-11-26.
- Add the data from the Results array to the google sheet, with each property’s data in a row
- Add the Check-in & Check-out dates used for the search at the top of the sheet
- Any dates should be in the proper US date format in the Google sheet eg 11/15/22 for November 15, 2022

#### - Detail for the Results data:
##### - City
        - should be the city that was searched, eg “Austin, TX”
##### - Property name 
        - name of the property in the search results
##### - rcId 
        - rcId for the property - this can be found in the results array for each property, eg in the findMatches call, the results of the call will show listings with propertyData and the propertyData will have a field rcId; this is the rcId that should be used
##### - Price 
        - the price shown with the listing
##### - LastUpdated 
        - this can be found in the results array for each property, eg in the findMatches call, the results of the call will show a “lastUpdated” field for each listing. Note that the date will likely have to be reformatted to be a proper date field in the Google Sheets.
