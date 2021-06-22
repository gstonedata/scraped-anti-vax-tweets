# scraped-anti-vax-tweets

This project sets out to highlight areas in Australia with potential vaccination hesitancy issues;
this is achieved by scraping geolocated anti vax tweets from across the country.

Less than 5% of tweets are geotagged, these tweets can be scraped with the Twitter API, which is however known for server disconnection problems.

All tweets containing given keywords and their corresponding geocoded data are scraped by TWINT.
TWINT is used, an alternative to the Twitter API, that utilises geocoded searches. 
Whilst not precise, these searches allow twitter users to view tweets from within a specified distance of a particular location,
and are considered estimates.

Firstly, Uber's H3 library was used to create an overlay of hexagons covering a map of Australia, and following the curvature of the earth.

H3 is open source and is used by Twitter within their apps extensively. 
This post explains further and documents the benefits of hexagons (or mostly hexagons!):
https://eng.uber.com/h3/

Circles roughly fitting the hexagons are created and used by TWINT to scrape tweets within these geofenced areas.

TWINT attempts to get around the problem of server disconnection while scraping tweets by automating retries,
this is visible through ongoing updates during the scraping process.
https://github.com/twintproject/twint

Tweets containing the terms 'antivax' and 'anti vax' were scraped from 1/1/21 to 20/6/21.

Each hexagon/circle that contains anti vax tweets within that time frame has a CSV file created containing each tweet and it's relavent information.

Analysis will be done on these hexagon csv files and an interactive choropleth map with time slider will be created.

This project builds upon work done by Logan Williams for Bellingcat, the open-source intelligence group.
