### Date : 11/02/26
# REVERSE KT: FEATURE ANALYSIS AMRAP-ECOMMERCE

**Module:** Warehouse Optimization

## 1. What is Warehouse Optimization?

Warehouse optimization is the process of using data and logic to improve the efficiency of storage and stock movement within a physical facility. In this system, it involves modeling the warehouse hierarchy (zones, aisles, racks) and mapping products to specific locations to minimize picking time and maximize space usage.

The primary goal is to centralize warehouse activity and ensure that every stock movement is tracked and strategically placed using Al-assisted recommendations.

---

## 2. Inputs and Outputs

To function effectively, the module processes specific operational data to generate actionable warehouse insights.

### **Inputs**


- **Warehouse Hierarchy:** Definitions of physical storage structures (Warehouses, Blocks, Aisles).
- **Product Specifications:** SKU details, dimensions, and storage requirements (like temperature,fragility).
- **Manual Stock Adjustments:** Inventory changes made by warehouse staff.(Internal)
- **Movement Logs:** Timestamps and IDs for every time a product is moved between locations.


### **Outputs**


- **Product-Location Map:** A digital record of exactly where each SKU is stored.
- **Allocation Suggestions:** Al-generated recommendations for where new stock should be placed for maximum efficiency.
- **Movement History:** A comprehensive log showing the "trail" of stock movement.
- **Fulfillment Paths:** Logic-driven locations for where to pick items from to fulfill a specific order.
- **Inventory Health Indicators:** Summaries of stock levels and storage status.

---

## 3. Product Logging and Traceability

The system ensures that no item is "lost" within the warehouse through a structured logging process.


- **SKU-Level Tracking:** Every product is tracked at the individual SKU level with a unique identifier.
- **Structured Stock States:** Inventory is managed using consistent states (e.g., "In-Transit," "Allocated," "Available") to ensure data integrity during sales and manual moves.
- **Movement History Tracking:** The system maintains a permanent history of stock movement across storage locations.
- **Traceability:** By combining the movement logs with the normalized sales data, an admin can trace a product from its initial warehouse allocation to the specific sales channel event that triggered its removal.


---

## 4. Overutilization and Underutilization (To be Avoided)

A key feature for the Admin side is the Al-assisted identification of space efficiency.

- **Overutilization:** The system flags areas or bins that are exceeding capacity or experiencing high-density "traffic" that causes bottlenecks. Al can suggest **stock redistribution** to move items to less crowded areas.
- **Underutilization:** The system identifies "dead zones" where storage space is being wasted or where products have become **slow-moving inventory**.
- **From Operational Analytics:** Dashboards provide visibility into these indicators, allowing admins to see warehouse activity heatmaps and redistribute stock to maintain a balanced, efficient flow.



---
