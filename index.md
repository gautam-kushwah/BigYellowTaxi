
# CS 424 - Project Page - Big Yellow Taxi
maintained by

Gautam Kushwah & Krishnan C.S.







# Important Links

[Link to Shiny App for Project 3](http://shiny.evl.uic.edu:3838/g16/kg-taxi/)

### Resources
[Link to Video Walkthrough](https://www.youtube.com/watch?v=15eiq648v3A)
<iframe width="560" height="315" src="https://www.youtube.com/embed/15eiq648v3A" frameborder="0" allowfullscreen></iframe>


# Introduction


This app was built as part of CS 424 - Visualization and Visual Analytics Course  under Dr. Andrew Johnson in Spring 2022.  The app is written in R and hosted on the evl(electronic visualization laboratory) shiny app server.
This app visualizes data on Taxi rides in and outside Chicago in multiple ways using R, Shiny, leaflet and Shiny Dashboard  to help the user get a better understanding of the data and make inferences.

The app is made to be served on a large screen size (11,520 X 3, 240 pixels). Therefore viewing it on a smaller screen would lead to the layout breaking up. A simple solution is to emulate a large screen size using chrome or some other browser.


### Software version
R version 4.1.2 (2021-11-01) -- "Bird Hippie"

RStudio 2021.09.1+372 "Ghost Orchid" Release (8b9ced188245155642d024aa3630363df611088a, 2021-11-08) for macOS
Mozilla/5.0 (Macintosh; Intel Mac OS X 12_2_1) AppleWebKit/537.36 (KHTML, like Gecko) QtWebEngine/5.12.10 Chrome/69.0.3497.128 Safari/537.36

### What is R?

R is a programming language for statistical computing and graphics supported by the R Core Team and the R Foundation for Statistical Computing


### What is Shiny?

Shiny is an R package that makes it easy to build interactive web apps straight from R. You can host standalone apps on a webpage or embed them in R Markdown documents or build dashboards


### Purpose of this App

The purpose of this app is to use the data provided on Taxi rides in and outside Chicago in 2019 and use shiny to give people an interactive interface to create those visualizations. Since the 2019 data is pre-COVID it is more representative of a 'typical' year.  

The data is presented in various ways, in the form of a map, a heatmap, bar plots and also in the form of tables with controls for each of them.

The app provides various data visualizations in the form of bar graphs breaking down rides in and outside chicago across days,  months, and days of the week and by the starting hour. It also includes plots for percentage of rides to/from each community, and taxi company. 

The user can choose to view the data in km/miles, the hour in 24/12hr formats, and to/from community area. There are also options for the user to select a community area and taxi company. The user may choose to include rides outside chicago as well. There is also a map of Chicago community areas using which the user may select the community area to view a heatmap showing the  percentage of rides to/from the community. The user may also select taxi company to subset this heatmap, showing percentage of rides to/from that community by that taxi company only. 

The app could also help the user find interesting things about the data which might have affected the behavior of the taxi rides and thus help us understand the power of data and data visualization.


### How to use the App?

You can head over to the app [here](http://shiny.evl.uic.edu:3838/g16/kg-taxi/). Upon opening the app, you would be greeted with a Shiny dashboard which would give you a map of chicago communities with their boundaries marked, bar plots for the toal number of rides, and those rides filtered through  hourly entries, entries for day of the week, month, mileage and trip time. 

The app has two sections

1. Home Page
2. About Page


These sections could be navigated through using the navigation bar on the left.

<img width="337" alt="image" src="https://user-images.githubusercontent.com/40148194/165185954-a3fa0b63-e61e-406b-ae0e-87a2cd7bb377.png">




## Home Page
<img width="1429" alt="image" src="https://user-images.githubusercontent.com/40148194/165186139-b6f3f1ba-7cbc-4b82-80d3-14e57f2b1434.png">

The home page has all the controls for the visualisations shown i.e the map with community areas locations and their data, in a separate section marked input controls.
<img width="132" alt="image" src="https://user-images.githubusercontent.com/40148194/165186554-54b2d0b6-b95e-49e5-99ea-b077d231c951.png">


There are 7 input controls
1. Outside Chicago checkbox: A checkmark to decide whether or not to include data for trips ending or beginning outside chicago
2. Mode: A radio button to select whether the ride ends or originates from a selected community
3. Select Community: A dropdown list of all the chicago community areas. Includes "Outside Chicago" if the Outside Chicago checkbox is checked
4. Select Taxi Company: A dropdown list of all the taxi companies included in the dataset
5. Time Format: To select whether to view the time in 12hr or 24hr format on the visualisations
6. Show Distance in: To select whether to show distance in km or miles on the visualisation
7. Chicago Community Map: The map itslef can be used an input to select the community areas.


The app has 8 visualisations




### 1.Bar chart for all the entries across the year
<img width="562" alt="image" src="https://user-images.githubusercontent.com/40148194/165187589-5168429d-214e-4b13-afb9-1572583ceeb4.png">



### 2. Bar chart for rides binned by hour of the day
<img width="555" alt="image" src="https://user-images.githubusercontent.com/40148194/165187861-be1c99af-b910-45c6-b566-9c1ac11029e3.png">

### 3. Bar chart for rides binned by day of the week
<img width="559" alt="image" src="https://user-images.githubusercontent.com/40148194/165187974-13ab2a64-6d91-4e5c-a0df-0f42936a9654.png">

### 4. Bar chart for rides binned by month
<img width="575" alt="image" src="https://user-images.githubusercontent.com/40148194/165188397-6350e7ec-421a-4c42-9c0a-0d375d2e7455.png">

### 5. Bar chart for rides binned by mileage
<img width="558" alt="image" src="https://user-images.githubusercontent.com/40148194/165188613-f4477750-4b22-448d-9766-92b159a64763.png">


### 6. Bar chart for rides binned by trip time
<img width="579" alt="image" src="https://user-images.githubusercontent.com/40148194/165188661-11a37ed2-3d82-47a4-9607-536bbaabd1d5.png">


### 7. Heatmap for percentage of rides ending or starting in a community
<img width="604" alt="image" src="https://user-images.githubusercontent.com/40148194/165189055-06c3b2c2-18a9-4743-b00e-9821fb5813b5.png">
<img width="489" alt="image" src="https://user-images.githubusercontent.com/40148194/165189283-3c908eed-85e8-4c10-ad96-9ffbcae71c5b.png">


### 8. Bar plot for percentage of rides ending or starting in a community
<img width="241" alt="image" src="https://user-images.githubusercontent.com/40148194/165189335-a50df93a-3553-4e1b-98ad-e2c1eea9a3f9.png">



All of these visualisations, except 7 and 8, could also be viewed in the form of a table.










# About the Data


The trip data was obtained from Chicago Data portal, the link to the data could be found [here](https://data.cityofchicago.org/Transportation/CTA-Ridership-L-Station-Entries-Daily-Totals/5neh-572f)

The map data was also taken from the Chicago Data portal and tge link could be found [here](https://data.cityofchicago.org/Facilities-Geographic-Boundaries/Boundaries-Community-Areas-current-/cauq-8yn6)

This list shows daily totals of ridership, by station entry, for each 'L' station dating back to 2001. Dataset shows entries at all turnstiles, combined, for each station.

The data consists of 5 columns and about 1.09 million rows.

The columns are as follows
**station_id** - Unique ID for a station

**stationname** - The name of the station

**date** - The date of the entries

**daytype** - W=Weekday, A=Saturday, U=Sunday/Holiday

**rides** - total number of ridership on that date



The other files which contained the latitude and longitude of the stations was also taken from Chicago data portal which could be found [here](https://data.cityofchicago.org/Transportation/CTA-System-Information-List-of-L-Stops/8pix-ypme)

The columns are as follows

**STOP_ID**  

**DIRECTION_ ID** Normal Direction of train taffic at the platform

**STOP_NAME**

**STATION_NAME**

**STATION_DESCRIPTIVE_NAME**	- A more fully descriptive name of a station. 

**MAP_ID**

**ADA**	- Boolean (if the station is ada compliant)

**RED** - Boolean (if the station serves red line)

**BLUE** - Boolean (if the station serves blue line)

**G** - Boolean (if the station serves green line)

**BRN** - Boolean (if the station serves brown line)

**P** - Boolean (if the station serves purple line)

**Pexp** - Boolean (if the station serves Purple Express line)

**Y** - Boolean (if the station serves Yellow line)

**Pnk** - Boolean (if the station serves Pink line)

**O** - Boolean (if the station serves Orange line)

**Location** - The latitude and longitude values




### R Libraries required to process the data

```
library(lubridate)
library(ggplot2)
library(leaflet)
library(leaflet.extras)
library(dplyr)
library(scales)
library(shiny)
library(shinyjs)
library(shinydashboard)
library(data.table)
library(purrr)
library(rgdal)
library(RColorBrewer)
library(DT)
library(pryr)

```

The date was provided in a chr format, therefore it had to be converted into a usable format which was achieved through a R library called **lubridate**

The data was downloaded in tsv format, since the free version of Shiny allows us to only work with files which are <5 mb, I used shell script to break it down into smaller files using shell and the following command

```
#Splitting data file into smaller chunks
no_of_chunks <- 15
split_vector <- ceiling(1: nrow(taxi)/nrow(taxi) * no_of_chunks)
res <- split(taxi, split_vector)
map2(res, paste0("part_", names(res), ".csv"), write.csv, row.names=FALSE)
```




I then used a code editor to verify if the files were broken down correctly, and upon verifying that I loaded the filenames in a list in R and then stitched them together into a single table, hence being able to work with all the rows, using the code below
  
```
#read all file names in a temp variable
temp = list.files(pattern="parta..tsv")
allData2 <- lapply(temp, read.delim)
allData <- do.call(rbind, allData2)
```

I then extracted the the info on the lines the stop serves from  STATION_DESCRIPTIVE_NAME and created a new column and then merged the ridership data table with the stop info table
 
```
lat_long <- read.table(file = "CTA_-_System_Information_-_List_of__L__Stops.tsv", sep = "\t", header = TRUE, quote = "\"")
lat_long$lines <- str_extract(lat_long$STATION_DESCRIPTIVE_NAME, "\\(.*\\)")
lat_long$lines <- str_remove_all(lat_long$lines, "[\\(\\)]")
lat_long <- lat_long %>% distinct(MAP_ID, lines, .keep_all = TRUE)
mergedData <- merge(x = allData, y= lat_long, by.x = c("station_id"), by.y = c("MAP_ID"), all.x = TRUE)
```
  
Next step was mapping the data onto the map for which I used the library **Leaflet**
  
The basic syntax is below and a more detailed one could be viewed on the github repo the link for which has been provided above
```
map <- leaflet(options= leafletOptions()) %>%
      addTiles(group="Base") %>% 
      addCircleMarkers(data = df, lat = ~lat, lng = ~long, )
```

The code for plotting various tables and bar graphs could also be found there





# Github


The github repo for the source code could be found below
[Github Repo CS424](https://github.com/gautam-kushwah/424_project2)

The source code is the file called **app.R**, with all the broken uptsv files named from partaa.tsv to partah.tsv and also the location data file.

To run the code you would need to download and install R and R-Studio the links to which could be found [!here](https://repo.miserver.it.umich.edu/cran/) and [here](https://rstudio.com/products/rstudio/download/) respectively 

Either clone or download the zip file from the repo and unzip it on your machine in your preferred location.
Now to run the app follow these steps:

1 Open R-studio
  
2 Click on File->New Project
  
3 Choose existing directory from the pop-up window
  
4 Now select the directory where you have downloaded the project
  
5 Follow the on screen instruction

Once the project has been created/opened go to app.R from the navigation tab on the bottom right of the IDE
Then in the file editor window on the top left, you would find a run app button, alternatively you could also use the R console and type in the command “runApp()”

The app would be launched in a separate window.

You could also open it in your web-browser by clicking on “open in web browser” button in the app window

To refer to the instructions on how to use and interact with app, please read the **How to Use the App** section above



# Observation and Inferences 

  
