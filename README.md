# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
The project was to showcase our fundamentals and knowledge of Python functions, including NumPys and Pandas, as well as applications of Exploratory Data Analysis and Statistical Modelling. The goal was to use APIs to scrape data from CitiBikes, Foursquare, and, Yelp and establish relationships, if any, between the number of bikes and various locations (points of interests) with the city of our choosing.  The data was collected to wrangle, clean, and combine for exploratory and visual analysis.

## Process
1. For my choice of city, I selected Vancouver, British Columbia, being borned in raised in the city.  Plus, the familiarity of the Greater Metro Vancouver Area could be useful to identify places based on names, addresses, and landmarks.
   
2. Accounts were created to obtain API keys for CitiBikes, Foursquare, and Yelp to submit HTTP requests for return of their respective information.  It was important to stress that these API Keys need to be used security via environment variables to keep them out of the hands of malicious users.

3. For CitiBikes, I used the 'for loop' function to collect the bike network IDs under Vancouver and store them in an empty list.  Thus, the Vancouver bike IDs were passed to the url (.../networks/network_id) to get the information on bike stations in Vancouver.  As a result, the 'latitudes', 'longitudes', and 'number of bikes' were collected and saved in a .csv file.

4. For Foursquare, the coordinates from the CitiBikes.csv were imported as a dataframe in order to pass along the 'latitudes' and 'longitudes' using the Python's 'for loop' function to the url to obtain restaurants, bars, and POIs within the radius.  The JSON was 'normalized' to a DataFrame, for which the table was tidied up,, such as renaming columns with the prefix 'fsq_' for clarity, and saved as a .csv file.

5. For Yelp, again, the same process was used as previously from Foursquare to obtain locations.  It was discovered that Yelp provides additional information as opposed to Foursquare, such as ratings, number of reviews, and prices.  These variables would be useful to apply statistical modelling between variables, but I opted to choose Foursquare as my choice for joining its data with CitiBikes for reasons to be explained later in this .README. 

6. The dataframes between CitiBikes and Foursquare were joined using the Pandas function 'pd.merge' having identified the 'ids' under citibikes to be the unique variable, which would capture locations near a specific bike station.  Data was visualized with graphs showing the number of bikes between POIs and number of bike stations between POIs.  In addition, the data was created, inserted, and stored in the SQLite database.

7. Lastly, a regression model was applied to demonstrate a relationship between the number of bikes and its variables with their POIs.

## Results
- I discovered that pinning down coordinates to get a bike station near a single location would be tricky as other locations would be captured within the radius depending on the size applied.  While I obtained approximately 250 bike stations in Vancouver, I was only able to generate 10 to 20 Foursquare and Yelp locations.

## Challenges 
- Testing the data given we had limited calls with APIs depending on the organization.  As I had trouble figuring out locations that were no where close to their nearest bike station, HTML requests were repeated, which led to exceeding my maximum API limits as a user.  Fortunately, I had the original data saved in .csv, but the data was clearly flawed.  For example, a yogurt shop (Menchie's) located near the campus at the University of British Columbia was no where near a bike station located on West Broadway, which would be about 10 km apart, equivalent to a a 20 minute drive between the two locations.

## Future Goals
(what would you do if you had more time?)
