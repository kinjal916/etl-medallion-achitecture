# Data Catalog for Gold Layer

## Overview
The Gold Layer is the business-level data representation, structured to support analytical and reporting use cases. It consists of **dimension tables** and **fact tables** for specific business metrics.
Add commentMore actions
---

### 1. **gold.dim_customers**
- **Purpose:** Stores customer details enriched with demographic and geographic data.
- **Columns:**

| Column Name      | Data Type     | Description                                                                                   |
|------------------|---------------|-----------------------------------------------------------------------------------------------|
| id     | int           | Surrogate key uniquely identifying each customer record in the dimension table.               |
| customer_id      | int           | Unique numerical identifier assigned to each customer.                                        |
| customer_key  | string  | Alphanumeric identifier representing the customer, used for tracking and referencing.         |
| firstname       | string  | The customer's first name, as recorded in the system.                                         |
| lastname        | string  | The customer's last name or family name.                                                     |
| country          | string  | The country of residence for the customer (e.g., 'Australia').                               |Add commentMore actions
| marital_status   | string  | The marital status of the customer (e.g., 'Married', 'Single').                              |
| gender           | string  | The gender of the customer (e.g., 'Male', 'Female', 'n/a').                                  |
| birth_date        | date          | The date of birth of the customer, formatted as YYYY-MM-DD (e.g., 1971-10-06).               |
| create_date      | date          | The date and time when the customer record was created in the system|

---

### 2. **gold.dim_products**
- **Purpose:** Provides information about the products and their attributes.
- **Columns:**

| Column Name         | Data Type     | Description                                                                                   |
|---------------------|---------------|-----------------------------------------------------------------------------------------------|
| id         | int           | Surrogate key uniquely identifying each product record in the product dimension table.         |
| product_id          | string           | A unique identifier assigned to the product for internal tracking and referencing.            |
| product_key      | string  | A structured alphanumeric code representing the product, often used for categorization or inventory. |
| product_name        | string  | Descriptive name of the product, including key details such as type, color, and size.         |
| category_id         | string  | A unique identifier for the product's category, linking to its high-level classification.     |
| category            | string  | The broader classification of the product (e.g., Bikes, Components) to group related items.  |
| subcategory         | string  | A more detailed classification of the product within the category, such as product type.      |
| maintenance| string  | Indicates whether the product requires maintenance (e.g., 'Yes', 'No').                       |
| product_cost                | double           | The cost or base price of the product, measured in monetary units.                            |
| product_line        | string  | The specific product line or series to which the product belongs (e.g., Road, Mountain).      |
| start_date          | date          | The date when the product became available for sale or use, stored in|

---

### 3. **gold.fact_sales**
- **Purpose:** Stores transactional sales data for analytical purposes.Add commentMore actions
- **Columns:**

| Column Name     | Data Type     | Description                                                                                   |
|-----------------|---------------|-----------------------------------------------------------------------------------------------|
| order_id    | string  | A unique alphanumeric identifier for each sales order (e.g., 'SO54496').                      |
| product_id     | INT           | Surrogate key linking the order to the product dimension table.                               |
| customer_id    | INT           | Surrogate key linking the order to the customer dimension table.                              |
| order_date      | DATE          | The date when the order was placed.                                                           |
| ship_date   | DATE          | The date when the order was shipped to the customer.                                          |
| due_date        | DATE          | The date when the order payment was due.                                                      |
| sales    | double           | The total monetary value of the sale for the line item, in whole currency units (e.g., 25).   |
| quantity        | double           | The number of units of the product ordered for the line item (e.g., 1).                       |
| price           | double           | The price per unit of the product for the line item, in whole currency units (e.g., 25).
