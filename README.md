# Windrose-in-R-for-any-location

#Load the libraries

library(openair)
library(nasapower)

# Download the data 

windrose_data <- get_power(
  community = "ag",
  lonlat = c(9.9932124954781, 76.32436109915098),
  pars = c("WS10M", "WD10M"),
  dates = c("2022-10-15", "2022-12-20"),
  temporal_api = "daily")

# Select the columns and rename

Wind_rose_final<-windrose_data[,8:9]

colnames(Wind_rose_final)<-c("ws","wd")

#Plotting

windRose(Wind_rose_final,paddle = FALSE,breaks = c(1,5,10,15,20),
         col=c("#4f4f4f", "#0a7cb9", "#f9be00", "#ff7f2f"))



