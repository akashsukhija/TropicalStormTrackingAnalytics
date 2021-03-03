# Tropical Storm Tracking Analytics

The NOAA National Hurricane Center has several databases available. We’re going to work with a historical
one called “HURDAT2”. From http://www.nhc.noaa.gov/data/#hurdat we can download two data files (Pacific
and Atlantic) in a non-standard CSV/fixed-width format. The strangeness is due to the mixture of two
interrelated line formats, the lack of column headers, and many missing data values (-99 &-999). There are
accompanying PDFs on that same webpage that describe the data format in fine detail.

Download both HURDAT2 data files and the descriptive PDFs. Read through the PDFs and peruse the data files
to get familiar with the custom data structure.

Created a solution that does not read in or retain the entire data set in memory at once. The data
files are already sorted chronologically, so you I have taken advantage of that. An incremental algorithm is implemented
here which is more memory efficient and theoretically unlimited in how much data it can handle.  This means the program will  
release the detail rows for each storm from memory before it proceeds to load the next storm.

As it processes each file, it computes and print out the following data for each storm:
a. Storm system ID. Also show its name if it had one.
b. Date range recorded for the storm (show start date and end date).
c. The highest Maximum sustained wind (in knots) and when it first occurred (date & time).
Don’t rely on finding a Record Identifier of value “W” for this, because not all storm records
have these. So, you must find the maximum numerically.
d. The total pressure change in millibars. (highest minus lowest)
e. How many times it had a “landfall”

After all the storm-specific output above, the program outputs these aggregate annual
statistics, arranged as aligned fixed-width columns, sorted chronologically, by year from 1851-2018. Do
not omit years that have no storms at all, but show zeroes. The column to show are:
a. “Year”
b. “Storms” - Total number of storms tracked per year (e.g. 6 in 1851).
c. “Cat.1” – the number of storms (not rows) of Category 1 or higher. (e.g. 3 in 1851)
d. “Cat.2” – same as above, for Category 2 or higher.
e. “Cat.3”
f. “Cat.4”
g. “Cat.5”

Refer to https://www.nhc.noaa.gov/aboutsshws.php for what the Category strength ranges are.

