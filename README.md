# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
The project was to showcase our fundamentals and knowledge of Python functions, including NumPys and Pandas, as well as applications of Exploratory Data Analysis and Statistical Modelling. The goal was to use APIs to scrape data from CitiBikes, Foursquare, and, Yelp and establish relationships, if any, between the number of bikes and various locations (points of interests) with the city of our choosing.  The data was collected to wrangle, clean, and combine for presentation.

## Process
1. For my choice of city, I selected Vancouver, British Columbia, being borned and raised in the city.  Plus, the familiarity of the Greater Metro Vancouver Area could be useful to identify places based on names, addresses, and landmarks.
   
2. Accounts were created to obtain API keys for CitiBikes, Foursquare, and Yelp to submit HTTP requests for return of their respective information.  It was important to stress that these API Keys need to be used security via environment variables to keep them out of the hands of malicious users.

3. For CitiBikes, I used the 'for loop' function to collect the bike network IDs under Vancouver and store them in an empty list.  Thus, the Vancouver bike IDs were passed to the url (.../networks/network_id) to get the information on bike stations in Vancouver.  As a result, the 'latitudes', 'longitudes', and 'number of bikes' were collected and saved in a .csv file.

4. For Foursquare, the coordinates from the CitiBikes.csv were imported as a dataframe in order to pass along the 'latitudes' and 'longitudes' using the Python's 'for loop' function to the url to obtain restaurants, bars, and POIs within the radius.  The JSON was 'normalized' to a DataFrame, for which the table was tidied up,, such as renaming columns with the prefix 'fsq_' for clarity, and saved as a .csv file.

5. For Yelp, again, the same process was used as previously from Foursquare to obtain locations.  It was discovered that Yelp provides additional information as opposed to Foursquare, such as number of reviews and ratings.  I selected Yelp between comparisons because these variables would be useful to apply statistical modelling between variables.

6. The dataframes between CitiBikes and Yelp were joined using the Pandas function 'pd.merge' having identified the 'ids' under citibikes to be the unique variable, which would capture locations near a specific bike station.  Data was visualized with graphs showing the number of bikes between bike stations; number of available bikes and empty slots near POIs; and comparision of Yelp ratings and reviews between POIs.  In addition, the data was created, inserted, and stored in the SQLite database.

7. Lastly, a regression model using the statsmodel function was applied to demonstrate a relationship between the number of bikes and its variables with their POIs.

## Results
- I discovered that pinning down coordinates to get a bike station near a single location would be tricky as other locations would be captured within the radius depending on the size applied when I called the function to get location results  Any bike station would be at least 10 km away from the nearest restaurant, bar, or point of interest.  I had a conversation with a mentor, who suggested that I carry on with the project with my flawed original datasets having Foursquare and Yelp halt my requests due to excess limits.
- This is another project where bad data would process bad statistical results - Garbage-In-Garbage-Out.  From my stastical modeling, it was difficult to fit the linear regression model due to scattered data plots between variables.  I find it to be inconclusive to see whether the number of bikes have any influence from the characteristics of any point of interests as the results of the bike stations were not closeby to any of locations obtained.
- Here are my thoughts about the relationship between number of bikes and locations:
  - Do we know the comparisons betwee the mode of commutes to locations, whether car, bike, or walk?
  - Time of the day and weather conditions would affect usage of bikes.
  - Would it make sense to input a bike station in an area with high traffic with urban areas with busy residential and commercial activity?  Also, it might go hand-in-hand especially when municipal governments implement public bike routes around the cities.  One example, people who bike near waterfronts on a hot and sunny day could drive their decisions to make a stop for a cool beverage or treat.
  - Would customers rent bikes to ride and go to a certain location, such as a park, coffee shop, or ice cream parlour, as opposed to a dine-in restaurant or a rural area with less points of interests?
  - Who are the target customers?  Are people more likely to use their own bikes versus renting a bike from a bike station?
  - Would the younger demographic likely use Foursquare or Yelp as opposed to the older demographic?
  - Are crowd-sourced reviews legitimate with respect to quantity and quality?  Are people leaving honest feedback about a location or are people using the opportunity to make bad comments on a location due to poor customer service?

## Challenges 
- Testing the data given we had limited calls with APIs depending on the organization.  Through my experiene with Vancouver checking through Google searches, I had trouble figuring out locations that were no where close to their nearest bike station.  I took the first row of data each from Foursquare and Yelp.  For example with Foursquare, a yogurt shop (Menchie's) located near the University of British Columbia was no where near a bike station located on West Broadway in Vancouver, which would be about 10 km apart, roughly 20 minute drive between the two destinations.  Another example with Yelp, it mimicked a similar error I encounted with Foursquare, where a restaurant (noodle shop) near the University of British Columbia is also 10 km apart to the same bike station located on West Broadway in Vancouver.
- HTML requests were repeated to test Python codes and revise data inputs, which led to exceeding my maximum API limits as a user.  Fortunately, I had original data saved in .csv files.  However, if I tested with a latitude and longitude of a bike station individually, it would yield locations that were within the search.  

## Future Goals
- I felt that I should have dedicated more time on the project as a whole instead of focusing the time and effort to further validate the data.  I would have liked to know what I have done incorrectly that allowed the search results of locations to be vastly out of range of the bike stations.  I did not want poor data to be used in the statistical modelling, which would have misinterpreted my results.
- I would have liked to find other free APIs on the internet, such as Google Places, to see if I could get better location results.
- I wished that I had more time to get my Python code to see if the steps and logic worked out.
- I could have implemented 'reponse status codes' to check if my HTML requests were successful or not, which would have prevented myself to further waste my API limits.
