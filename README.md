

# **Walmart Sales Analysis - Factors affecting sales (2010-2012)**

Walmart Inc. is a large American company that runs supermarkets, discount stores, and grocery stores across the United States. Its main office is in Bentonville, Arkansas.

# **PROJECT OVERVIEW**

### **Introduction**

This project looks at Walmart's retail sales data to see how stores perform in different locations and factors affecting sales. I use Python to explore and visualize the data, finding patterns in sales, seasonal changes, and how things like holidays, weather, fuel prices, inflation, and unemployment affect sales. The goal is to give useful insights that help retail managers make better decisions and understand customer behavior and market trends.
**Dataset Summary**

- Columns: 8 (5 decimal, 2 integer, 1 string)
- Rows: 6,435
- Store: Store ID
- Date: Start of the sales week (should be converted to datetime for analysis)
- Weekly_Sales: Total sales for the week
- Holiday_Flag: Indicates if the week includes a holiday (Yes/No)
- Temperature: Air temperature in the region
- Fuel_Price: Fuel cost in the region
- CPI: Consumer Price Index
- Unemployment: Unemployment rate

Additional Notes:

- No missing data
- 45 unique stores in the dataset

### **Setup**

- Programming Language: Python
- Libraries Dependencies: The libraries mentioned are numpy, pandas, seaborn, matplotlib, scikit-learn's train_test_split, StandardScaler, accuracy_score, LogisticRegression, DecisionTreeClassifier, RandomForestClassifier, SVC, and KNeighborsClassifier.
- Dataset: Store, Date, Weekly_Sales, Holiday_Flag, Temperature, Fuel_Price, CPI, and Unemployment, providing a comprehensive view of Walmart sales data.

![image](https://github.com/user-attachments/assets/c4ba5676-6f83-4069-ba65-fccb347a3ee9)


### **Importing Libraries and Loading Data:**

- File name: “walmat_data_Walmart_Sales.csv"
![Screenshot 2025-02-25 134511](https://github.com/user-attachments/assets/bbf087f3-53c9-4994-af4c-cd5750bba5e2)


### **Data Preprocessing**

### **1. Preparing the Data**

### **1.1 Cleaning the Data:**

![Screenshot 2025-02-25 134714](https://github.com/user-attachments/assets/a057b18a-1303-421e-90b1-0dc190e46a53)


- Fix column names.
- Handle missing values.
- Remove duplicate rows.
- Convert data types if needed.

### **1.2 Exploring the Data:**

- Get basic statistics (mean, median, min, max)
- Check dataset size and structure.

![Screenshot 2025-02-25 135050](https://github.com/user-attachments/assets/001308b3-c583-4e94-8139-fbefe4971f78)


### **Feature Engineering**

- Create new features from the date column (day, month, year, weekday, holiday)
- Identify key factors like weekly sales, temperature, fuel price, CPI, and unemployment rate.

### **Exploratory Data Analysis (EDA)**

**1. Visualizing list of features**

![Screenshot 2025-02-25 140104](https://github.com/user-attachments/assets/26059de9-b8f6-4036-81e4-548941fff0fd)


- Use histograms or density plots to see number trends.

![image (1)](https://github.com/user-attachments/assets/6469eb73-9f63-49d6-a19c-0922587da0a8)


- Use bar charts or count plots for categories.

![image (2)](https://github.com/user-attachments/assets/8005ad91-70b2-403b-a7c2-c98d9cc28cb7)


- Most sales are on the lower side, with occasional spikes, showing that high sales are less common. Temperature and unemployment follow a stable pattern, with most values near the average. Fuel price and CPI have two peaks, suggesting shifts in the economy or consumer behavior.

- Check relationships between numbers using a correlation matrix.

![image (3)](https://github.com/user-attachments/assets/18e16e8d-61e9-4943-a6d6-50d272110398)


- **Visualizing correlation matrix of features**
The correlation matrix helps us understand how different factors affect weekly sales. Sales slightly decrease when temperature, fuel price, and unemployment rise but increase a little when CPI goes up. Temperature has a small positive effect on fuel price, CPI, and unemployment. Fuel price has a weak negative impact on CPI and almost no effect on unemployment. CPI and unemployment have a stronger negative relationship, meaning when CPI rises, unemployment tends to drop. The matrix uses colors to show these patterns, with red indicating a positive link and blue showing a negative one.

**1.2 Grouping & Summarizing:**

- Store sales data by season and year.

![image (4)](https://github.com/user-attachments/assets/fd620dd1-5457-42a2-8d22-26eccc65cf85)


- Count how often holidays appear each year.

**1.3 Understanding Variables:**

- Group by year and holiday_flag to get counts.
- Target Variable (What We Predict): Weekly Sales
- Other Factors (What Might Affect Sales): holiday_flag, temperature, fuel price, cpi, unemployment.

**Temperature**
Key observations for temperature show that most temperatures in the dataset fall between 60 and 75 degrees Fahrenheit (°F)., making this the most common range. The histogram bars show how often each temperature appears, while the smooth density line highlights the overall pattern. Extreme temperatures are rare, meaning the data is mostly centered around the average. This helps us see temperature trends and can be useful for further analysis.

![image (5)](https://github.com/user-attachments/assets/7627fabf-fe55-4f2d-a906-cac8b6f264c2)


# Conducting Analysis with Python in a Jupyter Notebook on Visual Studio Code

**Holiday Impact on Sales**
Key observations for Holiday Impact on Sales from the graphs show that most records are for non-holidays, with 5,985 non-holiday entries (93.01%) and only 450 holiday entries (6.99%). The bar chart highlights the large gap between the two, while the pie chart visually confirms that holidays make up a small portion of the data. This suggests that holiday periods are rare compared to regular days.

![image (6)](https://github.com/user-attachments/assets/5c3fc778-a4c5-4bb6-9657-77f9af5eb308)


**Sales comparision: Holiday vs. Non-Holiday**
Key observations for Holiday and Non-Holiday from the bar chart shows that most of Walmart's weekly sales come from regular shopping weeks, totaling over $6 billion, while holiday sales are much lower at $505 million. This large gap suggests that factors like reduced store hours, consumer spending habits, and promotions outside holiday seasons may play a role in the difference.

![image (7)](https://github.com/user-attachments/assets/f083d84e-bcfb-4cc1-97dd-8da3329645ac)


**Total weekly sales per year**
Key observations for total weekly sales per year from the bar chart shows total weekly sales for 2010, 2011, and 2012. Sales were highest in 2011 at about $2.45 billion, slightly increasing from $2.29 billion in 2010. However, in 2012, sales dropped to $2.00 billion, showing a clear decline compared to the previous years. This suggests that after a peak in 2011, sales faced a downward trend in 2012.

![image (8)](https://github.com/user-attachments/assets/a2167f5e-c35a-44bc-b2f5-9c9c6dd24269)


**Unemployment rate vs. Weekly sales**
The scatter plot shows that as unemployment increases, weekly sales fall, indicating a negative correlation, meaning slight negative relationship between unemployment rate and weekly sales. The trend line confirms this downward pattern, suggesting that higher unemployment may lead to lower consumer spending.

![image (9)](https://github.com/user-attachments/assets/590fb4bb-af3a-41fd-9b3e-36e7dd9b700d)


**Impact of Holidays on Weekly Sales**
The bar chart shows that average weekly sales are a bit higher during holiday weeks compared to non-holiday weeks. It uses the x-axis to indicate if it's a holiday week (1 for yes, 0 for no) and the y-axis to show average weekly sales in millions.

**Conclusion:** Holidays seem to boost weekly sales, probably because people spend more during these times. Businesses can use this information to plan their marketing and manage stock better.

![image (10)](https://github.com/user-attachments/assets/3bd6488b-331c-4100-817a-62ae2dda5745)


**Weekly Sales Performance Across 45 Stores**
Store 20 and Store 4 make around two million dollars, making them the best-performing stores. About 27 stores, or 60% of them, have sales below one million, showing much lower performance. These differences may be due to location, promotions, or the types of marketing, or special offers, customers each store attracts.

![image (11)](https://github.com/user-attachments/assets/6dba8dcf-a96b-4e23-8962-8db6efbc91bc)


**The Store Sales War**
Store 20 has the highest sales, followed closely by stores 4, 14, and 13. A few stores make a lot of money, while many others have much lower sales. The stores on the right side of the chart have the lowest sales. This suggests that some stores perform much better than others, likely due to location, promotions, or customer demand.

![image (12)](https://github.com/user-attachments/assets/f8093945-0754-482e-8dd4-d0284c16b441)


**Top Stores Crushing Sales**
The top 10 stores with the highest weekly sales. Store 20 leads with about $301 million, followed closely by Store 4 at nearly $300 million. Other top performers, like Stores 14 and 13, also make around $280–290 million. The lowest in the top 10, Store 39, still sells over $200 million. These numbers show big differences in sales between stores, likely due to location, promotions, or customer demand.

![image (13)](https://github.com/user-attachments/assets/a0e0478b-9a14-4306-9924-5e35421bf96f)


**Stores with the Lowest Sales**
The 10 stores with the lowest weekly sales. Store 29 has the highest sales in this group at about $77 million, while Store 33 has the lowest at around $37 million. The other stores fall somewhere in between, with sales ranging from $43 million to $74 million. These stores are selling much less compared to the top-performing ones, possibly due to lower customer traffic, smaller store size, or fewer popular products.

![image (14)](https://github.com/user-attachments/assets/ebb54159-b918-44ab-b9cc-aaea884e2e96)


# Performing Data Analysis with Tableau

![Dashboard 1Screenshot 2025-02-25 173205](https://github.com/user-attachments/assets/2f45a414-1bfc-447d-b00c-05090da406e2)


The "Walmart Sales Analysis (2010-2012)" summarizes key financial metrics, including a profit of $6,737.22M, weekly sales of $1.05M, holiday-related sales of $6,231.92M, and $505.30M during peak holiday periods. Additionally, it highlights an unemployment trend value of 7.999. These metrics offer a clear overview of Walmart's sales performance and the influence of external factors during the specified period.

![Screenshot 2025-02-25 153726](https://github.com/user-attachments/assets/a6be044c-9bfc-4f7d-a92b-e23a767a395e)


The "Weekly Sales Pulse" dashboard reveals fluctuating sales trends, with steady performance early on, followed by more significant fluctuations from Week 41 onwards, particularly around Weeks 43 and 48. These trends suggest potential external factors influencing sales, which could inform strategic decisions for inventory management and marketing.

![Screenshot 2025-02-25 154317](https://github.com/user-attachments/assets/5003ba73-9fe7-4f78-b819-e5208794662d)
The line graph titled "Monthly Revenue Surge" shows that revenue peaks around June and July at approximately 650M, and dips significantly in November before rising again in December. This suggests strong revenue performance during mid-year months and holiday seasons, with a notable dip in early winter.

![Screenshot 2025-02-25 154619](https://github.com/user-attachments/assets/b586b6f3-83d4-4b41-b154-8574ded7b46d)



The bar graph titled "Fuel Costs vs. Sales" indicates two significant peaks in sales or fuel costs around $31,712,494 and $38,803,767. This suggests a correlation between higher fuel costs and increased sales within the observed range
![Screenshot 2025-02-25 155002](https://github.com/user-attachments/assets/c5273e45-3749-4339-acc8-69ee091e1a2a)



Store 20 has the highest sales at $301.4M, while Store 33 has the lowest at $37.2M. Overall, sales figures show a descending trend across the stores.

![Screenshot 2025-02-25 155328](https://github.com/user-attachments/assets/f0034083-d1df-4352-bbf8-324255eecc6f)


"How Temperature Drives Sales" show that sales are highest in mild temperatures ($3,379.19M) and lowest in cold temperatures ($1,069.50M). This indicates that mild weather positively influences sales, while cold weather has the least impact.

![Screenshot 2025-02-25 155648](https://github.com/user-attachments/assets/f2cd531f-a127-4679-bb9b-83470827753f)


"Holiday Sales Boom" shows that Non-Holiday sales dominate, amounting to $6,536.99M. In contrast, holiday sales figures are significantly lower, with Thanksgiving at $65.82M, Super Bowl at $48.34M, Labor Day at $45.63M, and Christmas at $40.43M.

![Screenshot 2025-02-25 155843](https://github.com/user-attachments/assets/6080a09f-7ff2-4872-abb5-3e458c55e7f3)


"Sales Across Seasons" reveals that summer consistently has the highest sales each year from 2010 to 2012. In contrast, winter generally experiences the lowest sales, with a significant dip in winter 2010.

![Screenshot 2025-02-25 160329](https://github.com/user-attachments/assets/c248a981-e01c-4502-b821-844cf60e5c8d)


"Sales Growth Trend" showcases significant fluctuations in sales growth percentages over time, with notable peaks at 45.86, 30.91, and 43.40. Meanwhile, the troughs at -50.04 and -40.20 indicate periods of substantial decline just after Christmas.

![Screenshot 2025-02-25 160532](https://github.com/user-attachments/assets/4a4f6508-cd2c-437b-a212-584459ab6d27)


![Screenshot 2025-02-25 161119](https://github.com/user-attachments/assets/b3b79c13-eed6-4347-bf74-5feeb8eb07fd)


"Yearly Sales Trends" shows weekly sales data from January to December, with significant sales peaks in February, May, and November, and a notable rise in December. This indicates clear seasonal variations in sales performance. indicates fluctuating weekly sales throughout the year, with significant peaks around March, July, and November. Notably, there is a marked increase in sales in December, highlighting a seasonal sales boost.

![Screenshot 2025-02-25 161318](https://github.com/user-attachments/assets/4212a764-aaa3-4f25-b210-0c41da0deec9)


![dashbaords 2Screenshot 2025-02-25 173420](https://github.com/user-attachments/assets/eb7ec7dc-219c-4e71-bf17-5795b01c7710)


## **Conclusion**

This analysis of Walmart's sales from 2010 to 2012 provides key insights into seasonal trends, holiday impacts, external factor influences, and store performance. The findings suggest that strategic pricing, holiday promotions, and tailored marketing initiatives can significantly boost sales. By leveraging data-driven decision-making and optimizing store-specific strategies, Walmart can enhance overall profitability and adapt to market fluctuations effectively.


### Links
[GoogleSheets](https://docs.google.com/spreadsheets/d/1jl2yEBY5NVjPV1UoIVLrylGwZzRkc_g1TExDUuNjoXk/edit?usp=sharing),
[Tableau](https://public.tableau.com/app/profile/kay.afu/viz/WALMARTSALESANALYSIS2010-2012/Main),
[Kaggle](https://www.kaggle.com/datasets/mikhail1681/walmart-sales)
[Documentation]


