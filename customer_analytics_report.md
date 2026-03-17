
# Customer Analytics Project Report

## Project Overview
This project focuses on performing advanced customer analytics using SQL window functions and Python libraries (pandas, matplotlib, seaborn). The goal is to gain insights into customer behavior, revenue trends, and identify valuable customers from a synthetic transactional dataset stored in an SQLite database.

## Data Setup
A synthetic dataset of customer orders was created and stored in an SQLite database named `customer_analytics.db`. The dataset includes `OrderID`, `CustomerID`, `OrderDate`, and `OrderAmount` for 10 sample orders.

```python
# Connect and create sample customer data
conn = sqlite3.connect('customer_analytics.db')

# Creating a table with 10 synthetic orders
data = {
    'OrderID': range(1, 11),
    'CustomerID': [101, 102, 101, 103, 104, 102, 101, 105, 103, 104],
    'OrderDate': ['2026-01-10', '2026-01-15', '2026-02-01', '2026-02-10', '2026-02-15',
                  '2026-03-01', '2026-03-05', '2026-03-10', '2026-03-12', '2026-03-15'],
    'OrderAmount': [2500, 1200, 3000, 500, 4500, 1100, 2000, 8000, 600, 4000]
}
df = pd.DataFrame(data)
df.to_sql('orders', conn, index=False, if_exists='replace')
print("Database 'customer_analytics.db' ready for Advanced SQL Analysis!")
```

## Analysis Performed

### 1. Customer Loyalty (Frequency & Total Spend)
This analysis identifies loyal customers based on their total orders and total spending. It provides insights into which customers contribute most to the business.

**Key Findings**: Customer 104 and 105 are the highest spenders, while Customer 101 has the most orders. The plots vividly show their contribution.

### 2. Cumulative Revenue
This section tracks the running total of revenue over time, providing a clear picture of how revenue accumulates.

**Key Findings**: The cumulative revenue shows a steady increase, reaching \$27,400 by March 15, 2026.

### 3. Customer Growth: Month-over-Month (MoM) Revenue
Analyzes monthly revenue and calculates the month-over-month difference to understand growth trends.

**Key Findings**: The monthly revenue consistently increased from January to March, with significant growth in revenue difference each month.

### 4. Identifying "Whale" Customers (Percentiles)
Customers are segmented into tiers (quartiles) based on their total spending, helping to identify top-tier customers.

**Key Findings**: Customer 104 and 105 are in the top tier (Tier 1), representing the "whale" customers with the highest spending.

### 5. Order Frequency Analysis (Day Gaps)
This analysis calculates the number of days between consecutive orders for each customer, indicating their purchasing frequency.

**Key Findings**: The analysis provides insight into the re-purchase cycles of customers. For instance, Customer 101 has placed orders with gaps of 22 and 32 days, while Customer 102 has a gap of 45 days between orders.

### 6. Revenue Contribution by Customer (Pie Chart)
A pie chart visualizes the proportion of total revenue contributed by each customer.

**Key Findings**: Customer 104 and 105 are the largest contributors to the total revenue.

## Technologies Used
*   **Python**: Programming language
*   **pandas**: Data manipulation and analysis
*   **sqlite3**: Database connection and SQL execution
*   **matplotlib.pyplot**: Data visualization
*   **seaborn**: Enhanced data visualization
