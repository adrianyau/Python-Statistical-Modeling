# Final-Project-Statistical-Modeling-with-Python

## Project/Goals
The project was to showcase our fundamentals and knowledge of Python functions, including NumPys and Pandas, as well as applications of Exploratory Data Analysis and Statistical Modeling. The goal was to use APIs to scrape data from CitiBikes, Foursquare, and, Yelp and establish relationships, if any, between the number of bikes and various locations (points of interests) with the city of our choosing.  The data was collected to wrangle, clean, and combine for presentation.

## Process
1. For my choice of city, I selected Vancouver, British Columbia, being born and raised in the city.  Plus, the familiarity of the Greater Metro Vancouver Area could be useful to identify places based on names, addresses, and landmarks.
   
2. Accounts were created to obtain API keys for CitiBikes, Foursquare, and Yelp to submit HTTP requests for return of their respective information.  It was important to stress that these API Keys need to be used security via environment variables to keep them out of the hands of malicious users.

3. For CitiBikes, I used the 'for loop' function to collect the bike network IDs under Vancouver and store them in an empty list.  Thus, the Vancouver bike IDs were passed to the url (.../networks/network_id) to get the information on bike stations in Vancouver.  As a result, the 'latitudes', 'longitudes', and 'number of bikes' were collected and saved in a .csv file.

4. For Foursquare, the coordinates from the CitiBikes.csv were imported as a dataframe in order to pass along the 'latitudes' and 'longitudes' using the Python's 'for loop' function to the url to obtain restaurants, bars, and POIs within the radius.  The JSON format was 'normalized' to a DataFrame, for which the table was tidied up,, such as renaming columns with the prefix 'fsq_' for clarity, and saved as a .csv file.

5. For Yelp, again, the same process was used as previously from Foursquare to obtain locations.  It was discovered that Yelp provides additional information as opposed to Foursquare, such as number of reviews and ratings.  I selected Yelp between comparisons because these variables would be useful to apply statistical modelling between variables.

6. The dataframes between CitiBikes and Yelp were joined using the Pandas function 'pd.merge' having identified the 'ids' under citibikes to be the unique variable, which would capture locations near a specific bike station.  Data was visualized with graphs showing the number of bikes between bike stations; number of available bikes and empty slots near POIs; and comparision of Yelp ratings and reviews between POIs.  In addition, the data was created, inserted, and stored in the SQLite database.

7. Lastly, a regression model using the statsmodel function was applied to demonstrate a relationship between the number of bikes and its variables with their POIs.

## Results
- I discovered that pinning down coordinates to get a bike station near a single location would be tricky as other locations would be captured within the radius depending on the size applied when I called the function to get location results  Any bike station would be at least 10 km away from the nearest restaurant, bar, or point of interest.  I had a conversation with a mentor, who suggested that I carry on with the project with my flawed original datasets having Foursquare and Yelp halt my requests due to excess limits.
- This is another project where bad data would yield bad statistical results - Garbage-In-Garbage-Out.  From my statistical modeling, it was difficult to fit the linear regression model due to scattered data plots between comparision of variables.  I find it to be inconclusive to see whether the number of bikes had any influence from the characteristics of any point of interests as the results of the bike stations were not closeby to any of locations obtained.
- The only relationship I could make between variables is that there is a negative correlation between empty slots and free bikes, meaning:
  - the more empty slots, the less free bikes are at a bike station.
  - the less empty slots, the more free bikes are at a bike station.
- Here are my thoughts to explore about the relationship between number of bikes and locations:
  - What is the mission statement of bike sharing companies?  Reference: https://www.mobibikes.ca/en/our-company for The City of Vancouver.
    - Reduce greenhouse gas emissions by reducing vehicles on the road, especially for short-travel commutes.
    - Increase accessibility of under-represented communities with lower socioeconomic status.
  - Places where bike stations would be built:
    - Follow public bike routes implemented by municipal governments around the city.
    - Provide a public service for locals and visitors to travel around landmarks and tourist attractions (e.g., Stanley Park).
    - Allow access around underprivileged neighbourhoods, such as rental housing, for people who cannot afford a vehicle or a personal bike to travel.
  - Other variables that I think they would affect the relationship between bikes and locations:
    - The time of the day and weather conditions depend on availibility of bikes.
    - Other forms of commute, such as subways (e.g., Skytrain) and ride-share programs (e.g., Uber and Lyft) that carry greater capacity of people.
    - Usage of bikes:
      - Is it geared toward a younger demographic or older demographic?
      - How comfortable are people using these bikes and navigating around traffic and intersections while sharing space with pedestrians and vehicles?
      - Is it easy to unlock a bike and return back to its station?
      - What is a short commute?  Is it a trip to a coffee shop or ice-cream parlour?
    - The prices that people would spend at locations.  Would there be a bike stations near restaurants with '$$$$' or '$$$$$' price rating?
  - Other variables that I think they would not affect the relationship between bikes and locations:
    - Reviews and ratings published on location services companies like Foursquare and Yelp.  Is there a relationship betweeen bikes and the number and quality of customer reviews?

## Challenges 
- Testing the data given we had limited calls with APIs depending on the organization.  Through my experience with Vancouver and verifying addresses through Google searches, I had trouble figuring out locations that were no where close to their nearest bike station.  I took the first row of data each from Foursquare and Yelp respectively to compare the details.  For example with Foursquare, a yogurt shop (Menchie's) located near the University of British Columbia was no where near a bike station located on West Broadway in Vancouver, which would be about 10 km apart, roughly 20 minute drive between the two destinations.  Another example with Yelp, it mimicked a similar error I encounted with Foursquare, where a restaurant (noodle shop) near the University of British Columbia is also 10 km apart to the same bike station located on West Broadway in Vancouver.  There must be something wrong with my Python 'for loop' function passing coordinates to the APIs versus entering a single coordinate for different location search results.
- HTML requests were repeated to test Python codes and revise data inputs, which led to exceeding my maximum API limits as a user.  Fortunately, I had original data saved in .csv files.  However, if I tested with a latitude and longitude of a bike station individually, it would yield locations that were within the search radius.  In the interest of time, I moved forward to fulfill the other requirements of this project.

## Future Goals
- I felt that I should have dedicated more time on the project as a whole instead of focusing the time and effort to further validate the data.  I would have liked to know what I have done incorrectly that allowed the search results of locations to be vastly out of range from their nearest bike stations.  I did not want poor data to be used in the statistical modeling, which would have misinterpreted my results.
- I would have liked to find other free APIs on the internet, such as Google Places, that could leverage Google's extensive resources to see if I could get better real-time location results and further information, such as traffic information and trip planning details.
- I wished that I had more time to assess my Python code to see if the steps and logic worked out.
- I could have implemented 'reponse status codes' to check if my HTML requests were successful or not, which would have prevented myself to further waste my API limits.
- If I had more time post-bootcamp, I could try to apply my theories and re-test this project.
