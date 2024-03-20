# Deforestation-Analysis-across-the-globe
![](https://github.com/edwinonine/Deforestation-Analysis-across-the-globe/blob/main/irina-iriser-2Y4dE8sdhlc-unsplash.jpg)

## DOCUMENTATION ON FINAL PROJECT ON DEFORESTATION ANALYSIS USING SQL

## INTRODUCTION

This is an sql project on deforestation. The project is carried out to review, analyze and derive insight to answer crucial questions on deforestation round the globe from 1990 to 2016 
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

## SKILL DEMONSTRATED

In analyzing the dataset, I applied certain skills in analyzing and deriving insight. 
These skills include carrying out windows function to create a frame in other to group based on category, common table expression (cte) the dataset, data cleaning/transformation.

## DATA SOURCE
the dataset set used for this analysis are 'forest_Area.csv','Land_Area.csv', and 'Region.csv; files containing details of deforestation across the globe across the world/globe between
1990 to 2016.

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
   Before
   
![](https://github.com/edwinonine/Deforestation-Analysis-across-the-globe/blob/main/dirty_forest_areaPNG.PNG)


```
update Forest_Area
set forest_area_sqkm = case when forest_area_sqkm is null then 0
else forest_area_sqkm
end;
```
  After
  
![](https://github.com/edwinonine/Deforestation-Analysis-across-the-globe/blob/main/cleaned_forest_areatozero.PNG)
 
```
update Forest_Area
set forest_area_sqkm = round(forest_area_sqkm,3);
```
  Before
  
![](https://github.com/edwinonine/Deforestation-Analysis-across-the-globe/blob/main/forest_area%20_decimal_dirty.PNG)

  After
  
![](https://github.com/edwinonine/Deforestation-Analysis-across-the-globe/blob/main/forest_area_decimalcleaned.PNG)

```
update Land_Area
set total_area_sq_mi = case when total_area_sq_mi is null then 0
else total_area_sq_mi
end;
```

 Before
    
 ![](https://github.com/edwinonine/Deforestation-Analysis-across-the-globe/blob/main/dirty_landArea_NullPNG.PNG) 

   After
   
   ![](https://github.com/edwinonine/Deforestation-Analysis-across-the-globe/blob/main/cleaned_landarea0.PNG)

##  ANALYSIS THE DATASET
In an attempt to tackle the issue of deforestation question, we delved into exploring the datasets provided 'forest_Area.csv','Land_Area.csv', and 'Region.csv; files. the following questions where asked

question 1. What are the total number of countries involved in deforestation? 

Question 2. Show the income groups of countries having total area ranging from 75,000 to 150,000 square meter?

Question 3: Calculate average area in square miles for countries in the 'upper middle income region'. Compare the result with the rest of the income categories.

Question 4: Determine the total forest area in square km for countries in the 'high income' group. Compare result with the rest of the income categories.

Question 5: Show countries from each region(continent) having the highest total forest areas. 

## Question 1
In answering question one, from analysis using the forest_area dataset, we had only 524 countries only 208 countries are involded in deforestation, 
while 316 countries are not involded in deforestation.
```
select count(distinct country_name) as countries_not_involed_in_deforestation from Forest_Area
where forest_area_sqkm != 0;
```

![](https://github.com/edwinonine/Deforestation-Analysis-across-the-globe/blob/main/question%201.PNG)


## Question 2
In answering question two, from the analysis only 19 countries from the group income having total area ranging from 75,000 to 150,000 square meter, with
upper middle income group having three (3) countries, lowe income group having three (3), lower middle income group four (4), the high income group had nine (9) and the upper middle income group having three
(3). 
```
select  distinct region.country_name,income_group from Region full join Land_Area on 
Region.country_code=Land_Area.country_code
where total_area_sq_mi between 75000 and 150000;
```

![](https://github.com/edwinonine/Deforestation-Analysis-across-the-globe/blob/main/question%202.PNG)


## Question 3
from the analysis, after comparing we observed that the upper middle income group has the highest  average total area with 383023.57781283sqmi, while 
while the high income group had a total of 182512.633844445sqmi, the lower miidle income had 161929.039350669sqmi and the low income had 
a total of 161626.848239651sqmi
```
select  income_group, AVG(total_area_sq_mi) as Average_total_area from Region full join Land_Area on 
Region.country_code=Land_Area.country_code
group by income_group
having income_group in ('upper middle income','high income','low income','lower middle income')
order by  AVG(total_area_sq_mi) desc;
```
![](https://github.com/edwinonine/Deforestation-Analysis-across-the-globe/blob/main/question%203.PNG)


## Question 4
from the analysis, after comparing we deduced that the upper middle income group has the highest
sum foresttotal area with 537631841.151, while 
while the high income group had a total of 280145166.716sqmi, the lower miidle income had 280145166.716sqmi and the low income had 
a total of 280145166.716 sqmi 
```
select Region.income_group, sum(forest_area_sqkm) as totalforest_area from Forest_Area  join Region on 
Forest_Area.country_code=region.country_code
group by Region.income_group
having income_group in ('high income','low income','upper middle income','lower middle income')
order by sum(forest_area_sqkm) desc;
```
![](https://github.com/edwinonine/Deforestation-Analysis-across-the-globe/blob/main/question%204.PNG)


## Question 5
from the analaysis, insight obtained depicts that brazil from latin america and carribbean has the higest forest_area_sqmi with a 
figure 5467050 sqmi, followed by canada from the region of North America with a figure 3482730sqmi, china  from East Asia and pacific
came third with a figure of 2098635sqmi, congo democratic republic from sub saharan Africa has a figure of 1603630sqmi, india
from south Asia has a figure of 708604sqmi, Iran, Islamic Rep. from the Middle East & North Africa with a figure 106919.805sqmi, 
and Russian Federation from Russian Federation figure 8151356sqmi.
```
with eddy_cte as
(select   distinct Forest_Area.country_name,region.region, forest_area_sqkm, 
row_number () over(partition by region.region order by forest_area_sqkm desc) as rank from region  join forest_area
on region.country_code=forest_area.country_code)
select * from eddy_cte
where rank = 1
```
![](https://github.com/edwinonine/Deforestation-Analysis-across-the-globe/blob/main/question%205.PNG)


## INSIGHT 
1. The total number of countries involved in deforestion are 524 in total, only 208 countries are involded in deforestation, 
   while 316 countries are not involded in deforestation.
2. From the analysis only 26 countries from the group income having total area ranging from 75,000 to 150,000 square meter, with upper middle income having six (6) countries, lower income group having three  
   (3), lower middle six (6) and the upper middle group having five (5) income group.
3. From the analysis, after comparing we observed that the upper middle income group has the highest  average total area with 383023.57781283 sqmi, while the high income group had a total of 
   182512.633844445 sqmi, the lower middle income had 161929.039350669 sqmi and the low income had a total of 161626.848239651 sqmi
4. From the analaysis, insight obtained depicts that brazil from latin america and carribbean has the higest forest_area_sqmi with a figure 5467050 sqmi, followed by canada from the region of North America 
   with a figure 3482730sqmi, china  from East Asia and pacific came third with a figure of 2098635sqmi, congo democratic republic from sub saharan Africa has a figure of 1603630sqmi, india
   from south Asia has a figure of 708604sqmi, Iran, Islamic Rep. from the Middle East & North Africa with a figure 106919.805sqmi, and Russian Federation from Russian Federation figure 8151356sqmi.

## RECOMMENDATION
1. Deforestation only took place in 208 nations, leaving out 316 nations. countries should be encourage to implement mechanism that generates economic value from forests, such as ecotourism, carbon credits, 
   or Sustainable timber harvesting. these approaches can incentivize forest conservation
2. Promote tree planting initiatives to restore degraded areas and expand forest cover.
3. Provide financial incentives for sustainable forestry, agroforestry, and reforestation project.
4. Encourage private sector involvement in sustainable supply chains







