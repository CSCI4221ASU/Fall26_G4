Malachi Johnson

# Project 4 — Meeting 1

Date: October 21, 2026
Time: 3:00 PM–3:30 PM
Team: Group 4
Members: Malachi Johnson and Jalen Davis
Project: Final Grade Calculator
Sprint: 4

## Discussion

We discussed the architecture for our Final Grade Calculator. We reviewed layered architecture and client-server architecture and Model-View-Controller.

Our proposed application will use three layers. The presentation layer will provide the website. The application layer will manage courses and calculate grades. The data layer will store course and assignment records.

We selected Java and Spring Boot for the backend. The frontend will use HTML and CSS and JavaScript. MySQL will provide a shared database.

We discussed Docker and how it packages an application into a container. A Docker image provides the template for the container. The Docker daemon manages containers on the host computer. Our application container will connect to a separate MySQL service.

We identified four major components: User Interface and Course Management and Grade Calculation and Database.

## Responsibilities

I will document the Course Management Component and Courses table. Jalen will document the Grade Calculation Component and Assignments table. We will both help with the overall architecture and container design.

## Product Backlog

| PBI | Status | Sprint | Estimate | Assigned | Reviewer |
|---|---|---|---|---|---|
| Review architecture patterns | Discussed | Sprint 4 | 2 days | Both members | Both members |
| Describe cloud architecture | Proposed | Sprint 4 | 1 day | Jalen Davis | Malachi Johnson |
| Describe the Docker container | Proposed | Sprint 4 | 2 days | Jalen Davis | Malachi Johnson |
| Identify major components | Initial components identified | Sprint 4 | 2 days | Both members | Both members |
| Design Courses table | Assigned | Sprint 4 | 1 day | Malachi Johnson | Jalen Davis |
| Design Assignments table | Assigned | Sprint 4 | 1 day | Jalen Davis | Malachi Johnson |

## Next Steps

Each member will identify the files and subcomponents needed for their assigned component. We will review database usage and table structures at the next meeting.

The estimates above are planned work time rather than recorded hours.