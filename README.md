# R-Markdown-project
The data used come from http://www.worldatlas.com/articles/most-dangerous-cities-in-the-united-states.html

This show the most Dangerous Cities In The United States

setwd("C:/Users/olivier.detandt/Documents/Doc/DataScience/Product Development")
data<-read.csv("Map.csv",sep=";")

library(leaflet)
## Warning: package 'leaflet' was built under R version 3.4.2
my_map <- data %>%
        leaflet() %>%
        addTiles() %>%
        setView(lng = -85, lat = 40, zoom = 5) %>%

        addMarkers(popup = "Test", 
                   lng = data$Lat, 
                   lat = data$Long)%>% 
        addCircles(weight=1,radius=sqrt(data$HomicieRate)*30000)

my_map

