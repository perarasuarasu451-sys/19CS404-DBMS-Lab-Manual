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
![Image](https://github.com/user-attachments/assets/b0392874-cdca-4724-81bf-b6512bc0b335)

### Entities and Attributes

| Entity                  | Attributes (PK, FK)                                             | Notes                                       |
|-------------------------|-----------------------------------------------------------------|---------------------------------------------|
| Member                  |MemberID (PK), Name, Phone, MembershipType                       |Stores member personal and membership details| 
| Program	                | ProgramID (PK), Type, Duration	                                |Different fitness programs (Yoga, Zumba,etc.)|
| Trainers	              |TrainerID (PK), Name, Phone, Specialization, Experience	        |Trainers working in the gym                  | 
| PersonalTrainingSession	|SessionID (PK), MemberID (FK), TrainerID (FK), Date, Time	      |Personal training session booked by members  | 
| Attendance	            |ID (PK), MemberID (FK), ProgramID (FK), Date, Status	            |Tracks which member attended which program   |
| Payment	                |ID (PK), MemberID (FK), Amount, Date, Mode	                      |Payment records of members                   |

### Relationships and Constraints

| Relationship                   | Cardinality  | Participation       | Notes                              |
|--------------------------------|--------------|---------------------|------------------------------------|
| Member–Program                 |	M:N       	|Partial on both sides|Attendance links Members to Programs|
| Program–Trainers               |	M:N	        |Partial	            |Trainers may run multiple programs  |
| Member–PersonalTrainingSession |	1:M         |Total on PTS side    |Each session must belong to a member|
| Trainer–PersonalTrainingSession|  1:M	        |Total on PTS side	  |Each session requires one trainer   |
| Member–Attendance	             |  1:M	        |Total on Attendance	|Attendance entry refer to a member  | 
| Program–Attendance	           |  1:M	        |Total	              |Attendance linked to programs       |
| Member–Payment	               |  1:M	        |Total on Payment	    |Payment must be made by a member    |
     

### Assumptions
- A member can join multiple programs.
- Trainers can be assigned to multiple programs.
- Personal training sessions always involve one trainer and one member.

---
5. Export the completed Markdown (with diagrams) as **a single PDF**
