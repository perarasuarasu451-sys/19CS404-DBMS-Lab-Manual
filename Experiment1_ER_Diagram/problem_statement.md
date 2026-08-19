# ER Diagram Workshop – Submission Template

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
![Image](https://github.com/user-attachments/assets/e042b8a0-0182-463e-84ed-4118d5c8f040)


### Entities and Attributes

| Entity    | Attributes (PK, FK)                                                                     | Notes                              |
|-----------|-----------------------------------------------------------------------------------------|------------------------------------|
|Customer	  |CustomerID (PK), Name, Email, Contact	                                                  |Customer details                    |      
|Dish	      |DishID (PK), DishName, Price, Category	                                                  |Menu items served                   |
|Waiter	    |WaiterID (PK), Name, Contact, Shift	                                                    |Staff who serve customers           |
|Reservation|ReservationID (PK), CustomerID (FK), TableID, Date, Time  	                              |Table reservations made by customers|
|Orders	    |OrderID (PK), CustomerID (FK), ReservationID (FK), DishID (FK), WaiterID (FK), OrderTime	|Order placed for dishes             | 
|Billing	  |BillID (PK), ReservationID (FK), TotalAmount, ServiceCharge	                            |Final bill for reservation          |               

### Relationships and Constraints

| Relationship        | Cardinality | Participation       | Notes                                      |
|---------------------|-------------|---------------------|--------------------------------------------|
|Customer–Reservation	| 1 : M	      |Total on Reservation	|A reservation must be linked to a customer  |
|Customer–Orders	    | 1 : M	      |Total on Orders	    |An order is always placed by a customer     |
|Reservation–Billing	| 1 : 1	      |Total on Billing	    |Every reservation has exactly one bill      |
|Reservation–Orders	  | 1 : M	      |Partial	            |Not all reservations may have orders        |
|Dish–Orders	        | 1 : M	      |Total on Orders	    |An order must refer to a dish               | 
|Waiter–Orders	      | 1 : M	      |Total	              |Each order is served by one waiter          |
|Customer–Billing	    | 1 : M       |Partial	            |Customer pays the bill for their reservation|         
### Assumptions
- A customer may or may not make a reservation before ordering.
- Each order contains one dish per entry (multiple dishes = multiple order entries).
- Billing is done per reservation, not per individual order.
- A waiter can serve multiple orders but an order is handled by exactly one waiter.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
