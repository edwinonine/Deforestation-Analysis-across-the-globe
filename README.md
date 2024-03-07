# Deforestation-Analysis-across-the-globe
![](https://github.com/edwinonine/Deforestation-Analysis-across-the-globe/blob/main/irina-iriser-2Y4dE8sdhlc-unsplash.jpg)

## DOCUMENTATION ON FINAL PROJECT ON DEFORESTATION ANALYSIS USING SQL

## INTRODUCTION

This is an sql project on deforestation. The project is carried out to review, analyze and derive insight to answer crucial questions on deforestation round the globe from 2019 to 2023 
and help gain deeper understanding and make data driven decision.

## PROBLEM STATEMENT
deforestation is a critical environment issue that has a far-reaching consequences for ecosystem, climate, and biodiverty. 
understanding the patterns, drivers, and impacts of deforestation is essential for informed decision-making and effective conservation efforts.
we aim to identify trends, contributing factors and potential mitigation strategy.

## RESEARCH QUESTION

we aimed to find solutions to the issues facing deforestation by answering the following questions:

question 1. What are the total number of countries involved in deforestation? 

Question 2. Show the income groups of countries having total area ranging from 75,000 to 150,000 square meter?

Question 3: Calculate average area in square miles for countries in the 'upper middle income region'. Compare the result with the rest of the income categories.

Question 4: Determine the total forest area in square km for countries in the 'high income' group. Compare result with the rest of the income categories.

Question 5: Show countries from each region(continent) having the highest total forest areas. 

## SKILL DEMONSTRATED:

In analyzing the dataset, I applied certain skills in analyzing and deriving insight. 
These skills include carrying out windows function to create a frame in other to group based on category, common table expression (cte) the dataset, data cleaning/transformation.

## DATA SOURCE
the dataset set used for this analysis are 'forest_Area.csv','Land_Area.csv', and 'Region.csv; files containing details of deforestation across the globe across the world/globe between
2019 to 2023.

## TOOLS 
1. sql server, used for analysis, data cleaning and reporting.


## DATA TRANSFORMATION/DATA CLEANING
In ensuring quality and reliability of the dataset. Columns were checked for duplicates, checked for inconsistencies, errors, and inaccuracies, Null values and outliers within the dataset. The following were keys steps used in ensuring the dataset was ready for analysis.
1. Data loading and inspection
2. handling Null values, by using the update function and the case statement 
3. Converting decimal values into three (3) decimal places.

```
select * from Forest_Area
 where forest_area_sqkm is null;
```


```update Forest_Area
set forest_area_sqkm = case when forest_area_sqkm is null then 0
else forest_area_sqkm
end;
```

```update Forest_Area
set forest_area_sqkm = round(forest_area_sqkm,3);
```

```update Land_Area
set total_area_sq_mi = case when total_area_sq_mi is null then 0
else total_area_sq_mi
end;
```

##  ANALYSIS THE DATASET
In an attempt to tackle the issue of deforestation question, we delved into exploring the datasets provided 'forest_Area.csv','Land_Area.csv', and 'Region.csv; files. the following questions where asked

question 1. What are the total number of countries involved in deforestation? 

Question 2. Show the income groups of countries having total area ranging from 75,000 to 150,000 square meter?

Question 3: Calculate average area in square miles for countries in the 'upper middle income region'. Compare the result with the rest of the income categories.

Question 4: Determine the total forest area in square km for countries in the 'high income' group. Compare result with the rest of the income categories.

Question 5: Show countries from each region(continent) having the highest total forest areas. 






















