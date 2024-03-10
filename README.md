# Statistical Modelling with Python

## Project/Goals

In this project, we will combine and practice implementing what we have learned throughout this course, including:

* Accessing data using APIs
* Cleaning and transforming data using Python
* Loading data into a database using Python
* Performing EDA, including using both statistics and visualizations
* Identifying trends and patterns in data using statistical models
* Interpreting the results of the statistical models

In my case specifically i plan to investigate the relationship between the `average distance each venue result is from each bike station` and the `distance between the bike station and the city center`

## Process / Results discussion

### Citybik.es

The objective here was to access the `Citybik.es` API to get results for Hamilton Ontario. This was a series of simple requests each requiring the `normalization of JSON objects`. I ended up with a DF of Bike stations operated by the only bike share in Hamilton.

### Foursquare & Yelp

Using the DF from the last step the next obecive was to use the Longitude and Latitude data from the bike stations to request results for general points of interest around each station. Both Foursquare and Yelp returned the results as `nested JSON object` which needed to be flattened/normalized into a more readable table using the pandas DF. Both results contained common thing like Addresses and Coordinates for each venue. But i found Yelps results to be more robust for average consumers with data like ratings and phone numbers.

### EDA and visualizations

This part felt a little vague because there was no immidiate obvious pattern for me to breakdown and it was at this stage in my process where i decided to investigate the relationship between the `average distance each venue result is from each bike station` and the `distance between the bike station and the city center`. I created visualizations based on this idea. All my investigative plots are available in the `\\data\\...` directory of this github but here are the main one showing the linear regression plots

for FS !['Linear regression plot comparing average distance between each venue and the venues distance to downtown hamilton'](https://github.com/Hounder23/LIGHTHOUSE-p2/blob/main/images/LINEAR%20REG%20FS%20-%20AVG%20VENU%20DIST%20vs%20DIST%20TO%20CENTER%20.png)

and Yelp ![Linear regression plot comparing average distance between each venue and the venues distance to downtown hamilton](https://github.com/Hounder23/LIGHTHOUSE-p2/blob/main/images/LINEAR%20REG%20YELP%20-%20AVG%20VENU%20DIST%20vs%20DIST%20TO%20CENTER%20.png)

### Creating sqlite3 db

This was pretty straightforward after reviewing some of the documentation of the sqlite3 python library. The DB file can be found at `\\data\\bike_stations_FS_Yelp.db`.
I did not however have the time to set up the table relationships though there are some.

### Model building

Here the objective was again vague so i decided to narrow it with a question. Can i model a relationship between the number of bikes available and the distances described above i.e. distance away from the center, avg Foursquare, and Yelp venue distances from the Bike stations.

This was good practice using the Backwards elimination approach for determining the strong features for creating the model. The only feture that was strong enough for me to keep and still have a model was the Distance away from the city center data. All the OLS Regression Results can be found in the `\\notebooks\\model_building.ipynb` file but here is a visualization of the final model ![Final model: Fitted values vs Residuals with confidence intervals and regression line](https://github.com/Hounder23/LIGHTHOUSE-p2/blob/main/images/FITTED%20VALUES%20vs%20RESIDUALS%20W%20CONFIDENCE%20INTERVALS.png)

## Challenges

Some challenges i faceed had to do with the Yelp API since we had yet to work with it during any of the course work thus far, and the normalization of JSON Objects into pandas DFs since this was one of the modukles during the course work i had most trouble with. However with the completion of this project i am now more confident in these 2 skills.

## Future Goals

* flesh out the db relationships
* find other meaningful models to predict available bikes at each station with the spare data in the other 2 tables
