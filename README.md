# Customer e-commerce behavior dashboard

### Dashboard Link :https://github.com/ramesh971997/BI-Dashboard/blob/main/Customer%20e-commerce%20behavior.pbix
## Problem Statement

The E-commerce Customer Behavior and Purchase Dataset is a synthetic dataset generated using the Faker Python library, designed to simulate a comprehensive e-commerce environment. This dataset captures various aspects of customer behavior and purchase history, making it ideal for data analysis and predictive modeling in the e-commerce domain. The dataset includes detailed customer information, such as unique identifiers, names, ages, and genders, along with purchase-related details like purchase dates, product categories, prices, quantities, total purchase amounts, payment methods, and return statuses. It also contains a binary churn indicator to identify customers who have stopped using the platform.
Key insights derived from the dataset reveal that female consumers make up a slight majority (50.2%) of the customer base, while male consumers account for 49.8%. Female customers purchased around 376,000 items, slightly more than male customers, who purchased about 374,000 items. The overall churn rate, representing both male and female customers who have stopped using the platform, stands at 80.09%.
This dataset can be used for a variety of tasks, including customer churn prediction, market basket analysis, recommendation system development, and trend analysis. It provides a valuable resource for researchers, data scientists, and analysts to model customer behavior, enhance e-commerce strategies, and develop data-driven insights for improving customer engagement and retention. The dataset is synthetic and intended for educational, research, and experimental purposes, offering a versatile foundation for exploring various data science and machine learning techniques in the e-commerce sector.


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

### Outcomes  
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
![donut](https://github.com/user-attachments/assets/1b704551-5a31-42ae-9734-a5c6aa63a99d)

Donut chart represent the genderwise whole distribution with each product price.With a notable 50.2% majority, female consumers have embraced the e-commerce platform, making it their preferred shopping destination.


Snapshot of Sum of Product Price by Churn situation
![pie](https://github.com/user-attachments/assets/15173b09-8641-445f-afab-913e2b8545ba)

The pie chart captures the uncertainty consumers face when making a purchase decision. The majority, a striking 80.09%, tend to reconsider or abandon their purchase primarily when comparing product prices.

Snapshot of timeline of the purchase date
![timeline](https://github.com/user-attachments/assets/1e43390e-288e-4ab7-bb30-54c067dbb123)

The timeline offers a versatile view of data, neatly grouped by annual, monthly, quarterly, weekly, and daily records. The added flexibility to adjust time intervals is a significant advantage, allowing for tailored insights at a glance.


