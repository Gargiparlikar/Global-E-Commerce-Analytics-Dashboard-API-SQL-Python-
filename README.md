# 🛒 Global E-Commerce Analytics Dashboard (API + SQL + Python)

### 📊 **Overview**
This project builds a **real-time E-Commerce Data Analytics System** using **Python**, **FakeStore API**, and **MySQL**.  
The data pipeline fetches live product data, stores it in a SQL database, performs advanced analysis using Python and SQL queries, and visualizes insights through Matplotlib and Seaborn.

---

### ⚙️ **Key Features**
- 🔗 Integrated **FakeStore API** to fetch real-time product, category, and price data.  
- 🗄️ Used **MySQL** for data storage and advanced querying.  
- 🧮 Implemented **ETL (Extract, Transform, Load)** using Python and Pandas.  
- 💹 Conducted in-depth **data analysis** on pricing, ratings, and category-wise sales.  
- 📈 Visualized results with **Matplotlib** and **Seaborn** for clear business insights.  
- 🔁 Automated data fetching and updates for near real-time insights.  

---

### 🧠 **Tech Stack**
| Layer | Tools / Technologies |
|--------|----------------------|
| **Programming Language** | Python |
| **Database** | MySQL |
| **API Source** | FakeStore API |
| **Libraries** | Pandas, Requests, Matplotlib, Seaborn, MySQL Connector |
| **Data Format** | CSV / Excel |

---

### 📈 **Data Flow**
1. **Data Extraction:** Retrieve product data from the [FakeStore API](https://fakestoreapi.com/).  
2. **Data Storage:** Insert product details into a **MySQL** database.  
3. **Data Transformation:** Use Pandas to clean, process, and enrich data.  
4. **Data Analysis & Visualization:** Execute SQL and Python-based analysis with visual insights.

---

### 🧮 **Example SQL Queries**
```sql
-- Average Price per Category
SELECT category, ROUND(AVG(price),2) AS avg_price
FROM products
GROUP BY category;

-- Top 5 Highest Rated Products
SELECT title, rate, price 
FROM products 
ORDER BY rate DESC 
LIMIT 5;

-- Most Sold Categories
SELECT category, SUM(monthly_sales) AS total_sales
FROM products
GROUP BY category
ORDER BY total_sales DESC;

-- Category Contribution to Revenue
SELECT 
    category,
    ROUND(SUM(price * monthly_sales), 2) AS category_revenue,
    ROUND((SUM(price * monthly_sales) * 100 / (SELECT SUM(price * monthly_sales) FROM products)), 2) AS percent_contribution
FROM products
GROUP BY category;
