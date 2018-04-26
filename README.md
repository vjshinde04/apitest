# apitest
R.O.C.K.S screening task


Create a repo on github or bitbucket, please name it "apitest"

​use any language, but you have to use postgresql
Database setup : (NOTE: Enable geolocation features in Postgresql with extensions : cube and earthdistance. 
Use the specific data types to create latitude and longitude

--------Interview Stage 1--------
create a new table in postgres and load this CSV that denotes the mapping between pincode and lat/long (https://github.com/sanand0/pincode/blob/master/data/IN.csv).
Create Two APIs in flask : Get,Post.
Post : Post lat,lng of any location with pin code+address+city and you can add new pin code in db. This api will be /post_location. Remember to check if pin code 
already exists or if there are existing latitude+longitude THAT ARE CLOSE ENOUGH TO BE THE SAME (dont assume that they will exactly be the same.)

Write testcases (using the test framework in your language. please use a test framework, do NOT just write functions and call it tests). 
Test different situations of adding data.

--------Interview Stage 2--------
Get : There are two GET apis. Given a location, fetch all the nearby pin codes within a radius. For example, I can ask - give me all points within 5km radius 
of (45.12, 71.12) . To do this you will need to do mathematical computation of radius. there are two ways to do this:
You can use postgres "earthdistance" to compute all points in 5km radius. This api will be /get_using_postgres
Implement the mathematical computation yourself. this api will be /get_using_self

Write testcases (using the test framework in your language. please use a test framework, do NOT just write functions and call it tests). Test results between /get_using_postgres and /get_using_self. 

--------Interview Stage 3--------
a Geojson is a json file which defines shapes of locations - for example the shape of delhi, gurgaon, etc. This geojson is used to define delhi and its areas. https://gist.github.com/ramsingla/6202001?short_path=7d9a995
you can check it out by going to http://geojson.io and pasting the raw json on the right side (on tab marked JSON).
You will then parse this json, and load the boundaries latitude and longitude (geometry -> coordinates) into postgresql in a new table. you can use any structure, 
but remember that one place will have lots of lat/long (because it marks the boundaries).
Write a new API : given a latitude/longitude, it will tell you which place it falls within.

Write testcases.
