
# CS 424 - Project Page - Big Yellow Taxi
maintained by

Gautam Kushwah & Krishnan C.S.







# Important Links

[Link to Shiny App for Project 3](http://shiny.evl.uic.edu:3838/g16/kg-taxi/)

### Resources
[Link to Video Walkthrough](https://www.youtube.com/watch?v=15eiq648v3A)
<iframe width="560" height="315" src="https://www.youtube.com/embed/15eiq648v3A" frameborder="0" allowfullscreen></iframe>


# Introduction

The app is written in R and hosted on Shiny apps website. The app helps creates visualisation based on the data provided to it and helps the
user get a better understanding of the data and possibly make inferences.


### Software version
R version 4.1.2 (2021-11-01) -- "Bird Hippie"

RStudio 2021.09.1+372 "Ghost Orchid" Release (8b9ced188245155642d024aa3630363df611088a, 2021-11-08) for macOS
Mozilla/5.0 (Macintosh; Intel Mac OS X 12_2_1) AppleWebKit/537.36 (KHTML, like Gecko) QtWebEngine/5.12.10 Chrome/69.0.3497.128 Safari/537.36

### What is R?

R is a programming language for statistical computing and graphics supported by the R Core Team and the R Foundation for Statistical Computing


### What is Shiny?

Shiny is an R package that makes it easy to build interactive web apps straight from R. You can host standalone apps on a webpage or embed them in R Markdown documents or build dashboards


### Purpose of this App

The purpose of this app is to use the data provided on riders on the Chicago L over the past 20 years and use shiny to give people an interactive interface to create those visualizations. 
The app provides an interactive map with the locations of the stations marked on it with their respective line colors and tapping on the markers gives more information about the line that station serves and and the number of rides on a particular date.
The dashboard can also provide the difference in the number of rides between two dates on a particular station.

The data is presented on the map, in the form of a bar plot and also in the form of a table with controls for each of them

The app provides various data visualizations in the form of bar graphs breaking down data across all years, individual years, months, and even days in a week over a month.


The app could also help find interesting dates in the last 20 years which might have affected the behavior of the riders and thus help us understand the power of data and data visualization.

### How to use the App?

You can head over to the app [!here](https://gautam-kushwah.shinyapps.io/424_project2/). Upon opening the app, you would be greeted with a Shiny dashboard which would give you a map with locations of the stations marked and a bar plot for the toal number of rides for all the staions on that day. 

The app has three sections

1. Home Page
2. About Page
3. Yearly Plots page

These sections could be navigated through using the navigation bar on the left.
<img width="407" alt="image" src="https://user-images.githubusercontent.com/40148194/158264770-5178df3c-abef-4f86-adf9-9f2fe1809b1a.png">



## Home Page




### Different dates mode



### Bar chart sorted in a descending manner 






## Yearly Plots Page



## Data tables instead of bar charts






# About the Data


The data was obtained from Chicago Data portal, the link to the data could be found [here](https://data.cityofchicago.org/Transportation/CTA-Ridership-L-Station-Entries-Daily-Totals/5neh-572f)

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

  
