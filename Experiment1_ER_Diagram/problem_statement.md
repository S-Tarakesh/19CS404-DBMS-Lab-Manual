# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_fitness.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

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
<img width="4488" height="1908" alt="restaurant" src="https://github.com/user-attachments/assets/abb219a7-4a44-4726-8d11-a99fe456c2e4" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Customer | CustomerID||
|Waiter   |WaiterID|       |
|Chef     |ChefID  |       |
|Table    |TableID|       |
|FoodItem | FoodItemID|       |
|Order|OrderID||
|OrderItem|OrderItemID,OrderID,FoodItemID||
|Bill|BillID,OrderID||
|Supervisor|SupervisorID||
### Relationships and Constraints
| Relationship | Cardinality | Participation | Notes |
|-----|----|----|----|
|Customer–Table  |	M:1	|Customer: Total; Table: Partial     |	Each customer is assigned to one table; a table can accommodate multiple customers over time.|
|Waiter–Table    |	M:N*|Waiter: Partial; Table: Total       |A waiter serves multiple tables, and a table is served by one waiter at a time.|
|Waiter–Order    |  1:M	|Waiter: Partial; Order: Total       |A waiter creates multiple orders; each order is created by one waiter.|
|Order–Table     |	M:1	|Order: Total; Table: Partial	       |Each order is placed at one table; a table can have multiple orders over time.|
|Order–OrderItem |	1:M |	Order: Total; OrderItem: Total     |	Each order contains multiple order items; each item belongs to one order.|
|Bill–Order      |	1:1	|Bill: Total; Order: Partial	       |Each bill is generated for one order; an order may have one bill.|
|Chef–OrderItem  |	1:M	|Chef: Partial; OrderItem: Total     |	A chef prepares multiple order items; each item is prepared by one chef.|
|Supervisor–Order|  1:M*|	Supervisor: Partial; Order: Partial|	A supervisor oversees exceptional cases; an order may or may not require supervision.|

### Assumptions
- A customer is assigned to one table. A table can be occupied by multiple customers (over time).
- A waiter serves multiple tables. A table is served by one waiter at a time.
- A waiter creates multiple orders. An order is created by one waiter.
- An order is placed at a specific table. A table can have multiple orders over time.
- An order contains multiple order items.Each order item belongs to one order.
- A bill is generated for one order. An order can have one bill.
- A chef prepares multiple order items. An order item is prepared by one chef.
- A supervisor manages exceptional cases related to orders. An order can have oversight from a supervisor.
## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
