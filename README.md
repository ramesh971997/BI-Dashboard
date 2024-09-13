# Customer e-commerce behavior dashboard

### Dashboard Link :https://github.com/ramesh971997/BI-Dashboard/blob/main/Customer%20e-commerce%20behavior.pbix
## Problem Statement

This dashboard helps the airlines understand their customers better. It helps the airlines know if their customers are satisfied with their services. Through different ratings, they get to know their improvement area, & thus they can improve their services by identifying these area. It also lets them know the average delay & departure time, thus since by using this dashboard they have identified this problem, they can further work on factors responsible for these unwanted delays.

Since, number of neutral/dissatisfied customers (almost 57 %) are more than satisfied customers (around 43 %), thus in all they must work on improving their services. 

Also since average delay in arrival & departure both is 15 minutes, thus they must try to reduce it.


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a excel file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that in none of the columns errors & empty values were present.
- Step 5 : In the report view, under the view tab, theme was selected. 
- Step 6 : Applied two slicers to select payment method and gender, according to the requirement apply the relevant tiled selection option. 
- Step 7 : Since the data contains various ratings, add a timeline to represent the purchase date of relative good. 
- Step 8 : Added two matrixes to highlight the customer's productwise qualitative involvement to buy product categories & the other matrix represent the genderwise payment methods quantities for four product categories.
- Step 9 : Two card visuals were added to the canvas, one representing quantity of the goods that customer purchased & other representing total purchased amount.
           Using visual level filter from the filters pane, basic filtering was used & null values were unselected for consideration into average calculation.
           
- Step 10 : Two bar charts were also added to the report design area representing the product price according to the categorized age. While creating this visual, the reason behind, age is continuous variable, therefore seggregated the age into same difference groups. 
- Step 11 : Add a donut chart to represent the Product Price by Gender.
- Step 12 : Plot a pie chart to visualize the how customers spend money to buy goods according to the churn situation. (A binary column indicating whether the customer has churned (0 for retained, 1 for churned ))
  

All these values have been ignored while calculating average rating for each of the parameters mentioned above.

- Step 13 : The purpose of plot the bar graph age has categorized into same size groups. For creating that categorized age variable the DAX expression was written below

      Age Category = 
      VAR Age = MAX('ecommerce_customer_data_custom_'[Age]) // Using MAX to aggregate the age values
      RETURN
       SWITCH(
          TRUE(),
          Age < 25, "18-24",
          Age >= 25 && Age < 35, "25-34",
          Age >= 35 && Age < 45, "35-44",
          Age >= 45 && Age < 55, "45-54",
          Age >= 55 && Age < 65, "55-64",
          Age >= 65 && Age < 75, "65-74",
          Age >= 75, "75+"
       )
Snapshot of the Sum of Product price and Age Category by Age
![bar chart](https://github.com/user-attachments/assets/e48543f2-f86e-436e-b123-0c6365ff20ef)
Step 13 DAX code visualize the final outcome from this attached snapshot.

Snapshot of the Sum of Product price by Gender and Product Category
![bar chart 2](https://github.com/user-attachments/assets/8eb98bc0-e221-4af4-b45a-196a879af57f)
Distribution of the product price categorized by 4 main product types(Books,Clothes, Electricity, Home) and Gender represent this bar graph. When consider 2020-2023 time period, clearly customers allocate their money to buy clothes and books.(Nearly 10M for all products.) 

Snapshot of Matrix highlighted the quantity distribution of four products by gender and payment method
![Matrix_1](https://github.com/user-attachments/assets/0f82ea81-1646-47e5-96e4-112231657fb3)
This matrix illustrates the distribution of products based on gender, revealing key purchasing patterns. It shows that male customers have a stronger preference for books, with 112,232 purchases, and electronics, with 75,439 purchases. On the other hand, female customers are more inclined towards clothing, with 113,915 purchases, and home-related items, with 75,097 purchases. Overall, the data indicates that female consumers are more actively engaging with e-commerce platforms across a wider range of product categories.

Snapshot of Sum of Product Price by Gender

Donut chart represent the genderwise whole distribution with each product price.With a notable 50.2% majority, female consumers have embraced the e-commerce platform, making it their preferred shopping destination.


Snapshot of Sum of Product Price by Churn situation

The pie chart captures the uncertainty consumers face when making a purchase decision. The majority, a striking 80.09%, tend to reconsider or abandon their purchase primarily when comparing product prices.

Snapshot of timeline of the purchase date


The timeline offers a versatile view of data, neatly grouped by annual, monthly, quarterly, weekly, and daily records. The added flexibility to adjust time intervals is a significant advantage, allowing for tailored insights at a glance


