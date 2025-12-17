# Car_Sales_EDA_Excel_Project

This project performs basic Exploratory Data Analysis (EDA) on car auction sales data using Excel. It analyzes selling price, condition, and odometer using summary statistics, price flags, and pivot tables to understand value patterns, quality levels, and how car condition relates to pricing.

## Data_set Used
 <a href="https://github.com/MSaad-data/Car_Sales_EDA_Excel_Project-/blob/main/Car_Sale_Dataset.xlsx">Dataset view</a>

 ## Introduction
 
Cars are sold every day, and each sale tells a small story. Some cars are new and clean, some have been driven a lot, and some sell for much more money than others. This project looks at car sales data from California to understand what is really happening behind those prices.

The data comes from a public dataset on Kaggle called Vehicle Sales Data. It includes real car sale records with details like car make, model, condition, mileage, selling price, and sale date. The full dataset is very large, with more than five hundred thousand records, so this project focuses on a smaller set of two thousand sales. This keeps the file easy to handle while still showing clear and useful patterns.

The main goal of this project is to explore the data step by step using Exploratory Data Analysis (EDA). Simple statistics are used to understand how selling prices, car condition, and odometer readings are spread across the data. This helps show what a typical car looks like, what is common, and what stands out as unusual.

Along with EDA, this project also uses Excel tools such as VLOOKUP and text functions to connect values, label data, and create clearer categories. Pivot tables are then used to summarize and compare results in a clean and organized way. By the end, the raw sales data turns into an easy-to-read story about car prices, quality, and mileage in real vehicle sales.

## Dataset Overview

This dataset contains detailed information about car sales. Each row represents one car sale, and each column describes a different part of that sale. Together, these columns help explain what kind of car was sold, where it was sold, and how much it sold for.

The data includes basic car details such as the model year, brand, model name, trim, body type, and transmission. It also contains identifying and location information like VIN, state, seller name, and exterior and interior colors. These fields help describe the car itself and the context of the sale.

In addition, the dataset includes key numeric fields used for analysis. The condition score shows the overall quality of the car, the odometer shows how much the car has been driven, the MMR value gives a market reference price, and the selling price shows the final sale amount. The sale date was converted into a sale year to make time-based analysis simpler and clearer.

## New Columns

New columns were created to clean the data and make analysis easier. These columns turn raw values into clear and usable information that works better for summaries, pivot tables, and comparisons.

The **sale_year** column was created using the formula
VALUE(INDEX(TEXTSPLIT(P2," "),4)).
This formula breaks the sale date text into parts, picks only the year, and converts it into a number. This removes extra text like time and timezone and makes the date easy to analyze by year.

The **car_full_name** column was created using
TEXTJOIN(" ", TRUE, B2, C2, D2).
This combines the make, model, and trim into one clear name. It helps identify each car in a simple way and makes lookups and summaries easier to read.

The **condition_flag** column was created using
IFS(I2>=40,"High", I2>=20,"Medium", I2<20,"Low").
This groups the condition score into easy labels. Instead of working with raw numbers, the cars are now grouped as high, medium, or low condition.

The price_flag column was created using
IFS(O2<18200,"Low", O2<=50000,"Medium", O2>50000,"High").
This groups selling prices into simple ranges. These labels make it easier to compare prices, build pivot tables, and understand how cars are distributed across price levels.

##EDA

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/88749f3c-f795-47bc-8692-44299184d96d" />
This dataset has 1,999 cars. The average selling price is $20,393, and the median is $18,200. Most cars cost between $12,100 (Q1) and $25,000 (Q3). The cheapest car is a Nissan Maxima at $1,000, and the most expensive is a Ferrari California at $154,000. Prices vary a lot, showing a mix of cheap and expensive cars in the market.


<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/1bbb0e29-e662-4506-a35f-e36f96cbaf65" />

The dataset has 1,944 cars. Condition scores range from 1 (Nissan Altima) to 49 (Audi Q5). The average score is 33.5, and the median is 38. Most cars fall between 29 and 43. The most common score is 44. This shows most cars are in decent condition with some variation.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/c4d40ebd-813e-4882-bb58-73c62f14df7d" />

The dataset has 1,999 cars. Odometer readings range from 1 mile (likely a new or demo car) to 999,999 miles (very high mileage or placeholder). The average is 35,371 miles, and the median is 32,906 miles. Most cars fall between 21,323 and 43,261 miles. The mode is 13,661 miles. This shows most cars are moderately used, with some outliers at very low or very high mileage.

These **VLOOKUP** formulas were used:
=VLOOKUP(B6, car_sale_raw_dataset!O:R, 4, FALSE)
=VLOOKUP(F6, car_sale_raw_dataset!$I:$R, 10, FALSE)
=VLOOKUP(J6, car_sale_raw_dataset!$J:$R, 9, FALSE)

##Pivot tables

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/070ec6fb-7b5a-43bb-a459-9fcfa41cae1d" />

The most common car makes are BMW with 330 cars, Infiniti with 249, Nissan with 244, Hyundai with 189, and Ford with 137. The top models are 3 Series (151), G Sedan (181), Altima (118), Elantra (53), and Sonata (54). Popular trims include 328i (109), G37 Journey (139), Base (173), GLS (86), and SE (88).
For body types, Sedan appears most often, followed by SUV, G Sedan, Hatchback, and Convertible. This shows that certain makes, models, trims, and body types are more frequently sold than others, highlighting trends in car popularity.


<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/38e7d849-8e00-407d-86c7-716b08d02bfd" />

The count of car_full_name shows how cars are spread across quality levels based on condition. Most cars fall into the Medium condition group, with 886 cars in this range. There are 771 cars in the High condition group, while 342 cars are in the Low condition group. This shows that most cars are neither very poor nor very high in condition, but sit in the middle range.

The count of price_flag follows the same pattern. There are 886 cars in the Medium price group, 771 cars in the High price group, and 342 cars in the Low price group. This suggests that pricing closely follows the condition of the cars, with medium-condition cars mostly priced in the medium range, and fewer cars falling into the low and high price groups.


##Summary

This project analyzes 2,000 car auction sales from California to understand how selling price relates to car condition and mileage. The work starts by cleaning raw data taken from a large Kaggle dataset with over 500,000 records. Text functions such as TEXTSPLIT, VALUE, and TEXTJOIN were used to extract the sale year from date text and to create a clear car name by combining make, model, and trim. Lookup formulas like VLOOKUP were used to identify which cars sold at the lowest and highest prices, linking numeric results back to real vehicles.

After cleaning, the project applies basic EDA using Excel statistics and pivot tables. Selling prices show a strong middle range, with most cars priced between $12,100 and $25,000, while extreme values include a $1,000 Nissan Maxima and a $154,000 Ferrari California. Condition and odometer analysis reveal that most cars are in medium condition with moderate mileage, while very low mileage and very high mileage cars appear as clear outliers. Price and condition flags were created using IFS formulas, and pivot tables show that cars with higher condition scores mostly fall into higher price groups. Overall, the project turns raw auction data into a clear story using Excel formulas, lookups, pivot tables, and simple EDA techniques to explain how car quality, usage, and price connect in real sales data.







