# COMSE6998.004 Assignment 1 

# Instagram Weather Triangulator

# - Adnan Firoze (af2728)
# (Dual MS in CS & Journalism)

This project/assignment polls Instagram API's ***recent tags endpoint*** and pulls out selected tags by the user and more specifically some that are helpful in triangulating catastrophic phemomenon such as flood, rain, storm, hurricane and the like. For demo purposes, I have included the hashtags #food, #selfie, #l4l so that you do not need to wait too long to see results. By default the polling is done using a two (2) seconds interval but it can be adjusted from the web front-end. **How-to and technical details is at the end of "Part 1."**

# Part 1:

**The Stream:**

The stream I selected is the Instagram recently uploaded hashtag stream from the API endpoint: https://api.instagram.com/v1/tags/latergram/media/recent?access_token=186174857.3d82e12.e8205e331f0a47499a1e4008c3b86f3b
Note that the access token is mine. 

**What it means in the real world:**

The primary objective of this is to triangulate the locations of events that can be classified as natural or man-made catastrophe such as rain, flood, fire, hurricane, snow etc. For demo purposes, I have added in the hashtags selfie, food and l4l (like for like) since they are most commmon. 

**What each message mean?**

Every message polled from this refers to the event of a person taking a picture of a specific event (at this moment) that relates to the hashtags mentioned. Note that I used a subsring search so even if I am searching for "rain" I will get hashtags like "raining", "rainy" etc. and similarly "stormy", "snowstorm", "sandstorm" etc. Moreover, I am only accepting posts with Geolocation for verificaiton purposes and returning location name, longitude and latitude from where it was taken. This I am filtering out the unverifiable posts. 

**Volume of Message expected:**

The volume of message really depends on user preference of hashtags and polling interval. For demo purposes, if you select all the hashtags and a polling interval of 2 seconds, you can expect to get 10-12 result in a minute. This can drastically reduce if you were to only triangulate #earthquake. 


# Documentation for Parts 2 and 3 
**The nitty-gritty of the codes are well comprehensively commented in the source files)**

# Files of Relevance

1. instagram.py
2. index.html

# How to run:

Assuming you are in a Mac and have the prerequisites (Python 2.7, websocketd) installed the steps are as follows:

1. Download this directory to your computer
2. In the terminal, change to the directory to the directory where the files have been downloaded.
3. **Part 2:** I used Python 2.7 (it will not work properly in Python 3.x). Simply type "python instagram.py" (without quotes) and hit enter. You will receive some warning messages but ignore those because they are expected since you will not be using OAuth but my access token. If you wait a minute you will start seeing results. Sample result would be as follows:

"/Library/Python/2.7/site-packages/requests/packages/urllib3/util/ssl_.py:120: InsecurePlatformWarning: A true SSLContext object is not available. This prevents urllib3 from configuring SSL appropriately and may cause certain SSL connections to fail. For more information, see https://urllib3.readthedocs.org/en/latest/security.html#insecureplatformwarning
InsecurePlatformWarning

food

Gracias Madre

2016-02-09 20:31:13

-118.3870668
34.0809382

food

2Amy's Neapolitan Pizzeria

2016-02-09 20:31:05

-77.0730667

38.9337196

selfie

Denton, Texas

2016-02-09 20:31:02

-97.1292

33.2163

selfie

Bottom of the Delaware River

2016-02-09 20:30:39

-75.137075186

39.957822561

  InsecurePlatformWarning

food

Gracias Madre

2016-02-09 20:31:13

-118.3870668

34.0809382"

**Part 3:** [I used Jquery, Javascript, JQueryUI, HTML and Bootstrap to build the frontend] 

 * Setting up web socket: Now open a new tab in the terminal (while being in the same directory) and type in the following (without quotes): "websocketd --port 8080 python instagram.py" and hit enter. The web socket will be up and running and will be serving over port 8080. 
 * Setting up web server: Again open a new terminal tab (WHILE THE PREVIOUS ONE IS RUNNING) and type in "python -m SimpleHTTPServer" (without quotes) and hit enter. Now we are good to go as we have this directory serving over port 8000. 
 * Load up the front end: Go to Google Chrome and browse to http://localhost:8000/ . 
 * For demo purposes, you should select ALL hashtags so that you see a populated table in seconds. After selecting all hashtags (turning them from Green to White), click "Go." The streaming will start and you can see results.

## Video demo: 

[![Video-demo](http://img.youtube.com/vi/keRvLc7Hibk/0.jpg)](http://www.youtube.com/watch?v=keRvLc7Hibk)

**The webpage will go on forever so you need to reload it (as mentioned in the Assignment instructions)**
