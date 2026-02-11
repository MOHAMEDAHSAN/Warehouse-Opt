### Date : 11/02/26
# REVERSE KT: FEATURE ANALYSIS AMRAP-ECOMMERCE

**Module 2:** Warehouse Optimization

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

## 5. AI-Driven Margin-Preserving Logic

The AI component within this module functions as a **Financial Guardrail**. Rather than focusing solely on physical proximity, the system prioritizes protecting business profitability by ensuring that warehousing and logistics expenditures do not exceed a product's established margin.

### **5.1 Cost-Aware Fulfillment**

Upon the ingestion of a sale from any channel, the AI calculates the **Total Cost to Serve**. This calculation factors in:

- **Est Holding Cost:** Calculated as
<img width="444" height="88" alt="image" src="https://github.com/user-attachments/assets/8213534d-78fc-42da-a98c-f396147337b0" />

- **Logistics/Transport Cost:** Distance-based shipping rates from the specific warehouse node to the customer destination.


### **5.2 Optimal Node Selection**

The system bypasses simple "closest-first" logic in favor of **Profitability-Optimized Routing**.

- **Example Scenario:**
<img width="750" height="450" alt="image" src="https://github.com/user-attachments/assets/30dcd1f4-9d36-4913-8f91-1138edd33e19" />


 If Warehouse B (proximate) costs 100/day in storage, and Warehouse C (distant) costs 50/day with 25 in transit costs, the AI selects **Warehouse C**. The total cost of 75 preserves a higher net margin compared to the more expensive, though closer, location.
 
### **5.3 Loss Prevention Alerts**

The AI performs a real-time margin check. Any order where the combined holding and shipping costs result in a negative margin (Net Loss) is flagged immediately in the **Operational Analytics** dashboard. This allows the administrator to intervene, halt the order, or manually adjust the fulfillment strategy.

---

## 6. Technical Feasibility & Architecture

The proposed solution utilizes a hybrid architecture, leveraging the **MERN Stack** for core operations and a **Python-based Microservice** for analytical logic.

### **6.1 Backend & AI Implementation**

- **MERN Core (Node.js/Express):** Manages the primary **CRUD** operations, including warehouse hierarchy definitions, manual stock adjustments, and the admin interface.
- **Python/FastAPI (Optimization Engine):** Acts as a dedicated microservice to handle complex margin-aware calculations. If we are gonna use models to predict warehouse selection for usage.
- **Workflow:** When an order is ingested via Node.js, the backend sends a request to the FastAPI service.
- **Optimization Logic:** The Python service executes a cost-comparison script: 
- **Result:** The engine returns the ID/Details of the **Optimal Warehouse** to the core system for automated fulfillment.




---
