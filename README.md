### Cleaning-in-SQL

Scanned through data table manually and noticed missing/null values. Size of data set allowed me eliminate null values

## To select all rows that did not have null values

SELECT distinct *

FROM my-portfolio-387609.TV_Data.TV_Data

WHERE Brand IS NOT NULL

AND Resolution IS NOT NULL

AND Size_ IS NOT NULL

AND Selling_Price IS NOT NULL

AND Original_Price IS NOT NULL

AND Operating_System IS NOT NULL

AND Rating IS NOT NULL;

Rows reduced from 921 to 665

Noticed the Brand 'Samsung' had values with different cases, then changed all Brands names to Uppercase; 

## To change column 'Brand'  to Uppercase

SELECT *
FROM my-portfolio-387609.TV_Data.TV_Data
WHERE Brand ="SAMSUNG"

SELECT *
FROM my-portfolio-387609.TV_Data.TV_Data
WHERE Brand ="Samsung"


SELECT UPPER(Brand) AS Brand_, Resolution, Size_, Selling_Price, Original_Price, Operating_System, Rating
FROM my-portfolio-387609.TV_Data.TV_Data_Cleaned;

Saved the cleaned data as a new table; TV_Data_2

## To check for outliers in the ratings, which are over 5;

SELECT Max(Rating)
FROM my-portfolio-387609.TV_Data.TV_Data

## To combine the tables into on and export it in CSV format to a local drive with a new name; TV_Data_Cleaned

INSERT INTO TV_Data_2 (Brand_, Resolution, Size_, Selling_Price, Original_Price, Operating_System, Rating)
SELECT Brand_, Resolution, Size_, Selling_Price, Original_Price, Operating_System, Rating
FROM my-portfolio-387609.TV_Data.TV_Data_Cleaned;
