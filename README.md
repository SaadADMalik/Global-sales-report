# 🛒 GlobalMart Sales Analysis
## End-to-End Business Intelligence with SQL, Power BI & ETL

### 💡 Tech Stack
- Power BI
- PostgreSQL
- Git
- VS Code
- Python

---

## 📌 Project Overview
This project provides a comprehensive business intelligence solution for **GlobalMart**, a multinational retailer operating across multiple countries. The objective is to **streamline sales tracking, consolidate data from different sources, and generate insightful dashboards** using Power BI.

To achieve this, data from various sources (including **Azure Cloud databases and CSV files**) was cleaned, transformed, and centralized in **Power BI** for further analysis. The interactive report allows users to **drill down into KPIs** and track sales performance over time.

Additionally, **SQL queries** were developed to provide direct access to the database for deeper analysis, and a **Python-based database connector** was created to automate query execution.

🔹 *All data used in this project is fictional and was created solely for learning and demonstration purposes.*

---

## 🏬 Business Challenge
GlobalMart faced difficulties in:
- Tracking sales
- Managing customer data
- Visualizing business performance due to scattered data sources

### **The company required:**
✅ A **centralized data model** for structured reporting  
✅ **Interactive dashboards** to track sales trends and key performance indicators (**KPIs**)  
✅ **SQL-based queries** to allow easy data retrieval without relying on Power BI  

---

## 📊 Power BI Dashboard
The **Power BI report** provides interactive visual insights on key business metrics. Users can filter and explore:

📈 **Revenue trends over time**  
🏷️ **Product sales performance**  
📍 **Regional store insights**  
👥 **Customer segmentation & purchase behavior**  

### 🔹 Dashboard Preview
![image](https://github.com/user-attachments/assets/a06f8713-c288-496f-ba2e-7876b2b1d9d8)


---

## 🔹 Star Schema Data Model
To efficiently structure the dataset, a **star schema** was implemented in Power BI, ensuring **optimal performance and easy navigation**.

### **Star Schema Model**
![image](https://github.com/user-attachments/assets/c22bfea9-9a23-4408-b56e-e591048641a7)



---

## ⚙️ SQL Queries for Business Insights
SQL queries were created to fetch **real-time insights** from the centralized **Azure database**. Below is an example query that retrieves total revenue and order counts by store type:

```sql
-- Sales & Orders Summary by Store Type
CREATE VIEW "Store Sales Overview" AS
SELECT
    "Store Type",
    "Revenue",
    "Revenue" / SUM("Revenue") OVER () AS "Percentage of Total Revenue",
    "Total Orders"
FROM (
    SELECT
        ds.store_type AS "Store Type",
        SUM(o.product_quantity * dp.sale_price) AS "Revenue",
        COUNT(*) AS "Total Orders"
    FROM orders o
    JOIN dim_product dp ON dp.product_code = o.product_code
    JOIN dim_store ds ON ds.store_code = o.store_code
    JOIN dim_date dd ON dd.date = o.order_date
    GROUP BY "Store Type"
) AS store_data;
```

---

---

## 🚀 Getting Started
### **Prerequisites**
- Install **Power BI Desktop**
- Set up **PostgreSQL** database
- Install required **Python libraries** (`pandas`, `sqlalchemy`, `psycopg2`)

### **Steps to Run the Project**
1. **Clone the repository**
   ```sh
   git clone https://github.com/your-repo/GlobalMart_Sales_Analysis.git
   cd GlobalMart_Sales_Analysis
   ```
2. **Set up the database** using SQL scripts in `sql_queries/`
3. **Run Python ETL scripts** to load data into the database
4. **Open the Power BI report** in `reports/`
5. **Explore interactive insights**

---

## 🛠️ Future Enhancements
- Add **machine learning-based sales forecasting**
- Integrate **real-time streaming data**
- Implement **DAX measures** for advanced Power BI calculations

---

## 📜 License
This project is licensed under the **MIT License**.

📧 **Contact:** If you have any questions, feel free to reach out!

