# Cafe-Sales-Data-Cleaning
Cafe Sales - Dirty Data for Cleaning Training

## about dataset
The Dirty Cafe Sales dataset contains 10,000 rows of synthetic data representing sales transactions in a cafe. This dataset is intentionally "dirty," with missing values, inconsistent data, and errors introduced to provide a realistic scenario for data cleaning and exploratory data analysis (EDA). It can be used to practice cleaning techniques, data wrangling, and feature engineering.
  
  **File Information**
* **File Name:** dirty_cafe_sales.csv
* **Number of Rows:** 10,000
*  **Number of Columns:** 8

**Columns Description**
Column Name | Description
----------|------------|
Transaction ID  |     A unique identifier for each transaction. Always present and unique.
Item            |     The name of the item purchased. May contain missing or invalid values (e.g., "ERROR").
Quantity        |     The quantity of the item purchased. May contain missing or invalid values.
Price Per Unit  |     The price of a single unit of the item. May contain missing or invalid values.
Total Spent     |    The total amount spent on the transaction. Calculated as Quantity * Price Per Unit.
Payment Method  |    The method of payment used. May contain missing or invalid values (e.g., None, "UNKNOWN").
Location        |     The location where the transaction occurred. May contain missing or invalid values.
Transaction Date  |    The date of the transaction. May contain missing or incorrect values.  

**Menu Item**
Item | Price ($)|
-----|------|
coffee    |   2     
Tea       |  1.5   
snadwich  |  4     
salad     |  5     
Cake      |  3     
Cookie    |  1     
Smoothie  |  4     
Juice     |  3   

##  Data cleaning
 **data in before cleaning**

No|Column|Non-Null Count| Dtype 
---|-------|--------------| ----- 
 0  | Transaction ID   | 10000 non-null | object
 1  | Item             | 9667 non-null  | object
 2  | Quantity         | 9862 non-null  | object
 3  | Price Per Unit   | 9821 non-null  | object
 4  | Total Spent      | 9827 non-null  | object
 5  | Payment Method   | 7421 non-null  | object
 6  | Location         | 6735 non-null  | object
 7  | Transaction Date | 9841 non-null  | object


**data after cleaning**
No|Column|Non-Null Count| Dtype 
---|-------|--------------| ----- 
0  | Transaction ID    | 9727 non-null  | object        
 1  | Item             | 9727 non-null  | object        
 2  | Quantity         | 9727 non-null  | float64       
 3  | Price Per Unit   | 9727 non-null  | float64       
 4 | Total Spent       | 9727 non-null  | float64       
 5 |  Payment Method   | 9727 non-null  | object        
 6  | Location         | 9727 non-null  | object        
 7  | Transaction Date | 9727 non-null  | datetime64[ns]

**Handle data**
1. Change all invalid data **(e.g. ERROR, UNKNOWN)** to NaN for easy data cleaning.
2. Change the data type of each field to be appropriate
3. Find the Missing Value of the **Price Per Unit** field **(1)** by comparing the value of the Item from the Menu Item table **(2)** by comparing the value of the **Total Spent / Quantity** field
4. Find the Missing Value of the **Total Spent** field by comparing the value of the **Quantity * Price Per Unit** field
5. Find the Missing Value of the **Quantity** field by comparing the value of the **Total Spent / Price Per Unit** field
6. Find the Missing Value of the **Item** field by comparing the value of the Item from the Menu Item table
7. Find the Missing Value of the **Payment Method, Location, Transaction Date** fields by using the previous value **(ffilll)** to fill in

   **Data that cannot be found is**
    * record with fields Item, Quantity, Price Per Unit, Total Spent with at least 3 fields as NaN
   * record with fields Quantity, Total Spent as NaN
   * recoerd with fields Item as NaN and field Price Per Unit = 3.0
     
There is data 273 records out of 10,000 total records could not be handled and were removed from the dataset.

**การจัดการข้อมูล**
1. เปลี่ยนข้อมูลที่ไม่ถูกต้อง (เช่น ERROR, UNKNOWN ) ให้เป็น NaN ทั้งหมด เพื่อให้ง่ายต่อการทำความสะอาดข้อมูล
2. เปลี่ยนชนิดข้อมูลของแต่ละ Field ให้เหมาะสม
3. หาค่า Missing Value ของฟิลด์ Price Per Unit  (1) ได้จากการเทียบ ค่าของ Item จากตาราง Menu Item (2) ได้จากการเปรียบค่าของฟิลด์ Total Spent / Quantity
4. หาค่า Missing Value ของฟิลด์ Total Spent  ได้จากการเปรีบเทียบค่าของฟิลด์ Quantity * Price Per Unit
5. หาค่า Missing Value  ของฟิลด์ Quantity ได้จากการเปรีบเทียบค่าของฟิลด์ Total Spent / Price Per Unit
6. หาค่า Missing Value ของฟิลด์ Item ได้จากเปรียบเทียบค่าของ Item จากตาราง Menu Item
7. หาค่า Missing Value ของฟิลด์ Payment Method, Location, Transaction Date ได้โดยการใช้ค่าก่อนหน้า (ffilll) มาเติม

  **ข้อมูลที่ไม่สามารถหาได้คือ**
  
  *  record ที่มีฟิลด์ Item , Quantity , Price Per Unit, Total Spent ที่มีอย่างน้อย 3 ฟิลด์ขึ้นไป เป็น NaN
  *  record ที่มีฟิลด์ Quantity , Total Spent  เป็น NaN
  *  recoerd ที่มีฟิลด์ Item เป็น NaN และฟิดล์ Price Per Unit  = 3.0

มีข้อมูล 273 record จากทั้งหมด 10,000 record ที่ไม่สามมารถจัดการได้ จึงนำออกจากชุดข้อมูล
