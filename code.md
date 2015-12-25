# Coursera-r-Assignment-1
Write a function named 'pollutantmean' that calculates the mean of a pollutant (sulfate or nitrate) across a specified list of monitors. The function 'pollutantmean' takes three arguments: 'directory', 'pollutant', and 'id'. Given a vector monitor ID numbers, 'pollutantmean' reads that monitors' particulate matter data from the directory specified in the 'directory' argument and returns the mean of the pollutant across all of the monitors, ignoring any missing values coded as NA.
pollutantmean <- function(directory, pollutant, id = 1:332) {
	setwd(file.path(getwd(), directory))
	total <- 0
	observations <- 0
	if(pollutant == "sulfate") {
		for(i in id) {
			i <- sprintf("%03d", i)
			data <- read.csv(paste(i, ".csv", sep = ""))
			r <- nrow(data)
				for(j in 1:r) {
					if(is.na(data[j, 2]) == "TRUE") {
					}
					else {
						total <- total + data[j, 2]
						observations <- observations + 1
					}
				}
		}
	mean <- total/observations
	return(mean)
	}
	if(pollutant == "nitrate") {
		for(i in id) {
			i <- sprintf("%03d", i)
			data <- read.csv(paste(i, ".csv", sep = ""))
			r <- nrow(data)
				for(j in 1:r) {
					if(is.na(data[j, 3]) == "TRUE") {
					}
					else {
						total <- total + data[j, 3]
						observations <- observations + 1
					}
				}
		}
	mean <- total/observations
	return(mean)
	}
	else {
		print("Wrong Parameters")
	}
}
			
