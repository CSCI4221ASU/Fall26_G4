Malachi Johnson

# Project 4 — Meeting 3

Date: October 29, 2026
Time: 3:00 PM–3:30 PM
Team: Group 4
Members: Malachi Johnson and Jalen Davis
Project: Final Grade Calculator
Sprint: 4

## Discussion

We reviewed our architecture design and the responsibilities of each component. Our design uses a browser interface and a Spring Boot application and a shared MySQL database.

We reviewed the proposed Docker container. It will include the Java runtime and the built application and its required libraries and frontend files. MySQL will operate separately. Database credentials will be supplied through environment variables.

I reviewed my Course Management design. The component will validate course information and manage course records through the controller and service and repository files.

We checked the relationship between our database tables. Courses will use course_id as its primary key. Assignments will use course_id as a foreign key. This will allow multiple assignments to belong to one course.

We also reviewed the required submission files. Each member needs an architecture document and three separate meeting-minute files in the Project4 folder of their own repository.

## Product Backlog

| PBI | Status | Sprint | Estimate | Assigned | Reviewer |
|---|---|---|---|---|---|
| Review container description | Reviewed in meeting | Sprint 4 | 1 day | Both members | Both members |
| Review Course Management design | Reviewed in meeting | Sprint 4 | 1 day | Malachi Johnson | Jalen Davis |
| Review Grade Calculation design | Reviewed in meeting | Sprint 4 | 1 day | Jalen Davis | Malachi Johnson |
| Check database table relationship | Reviewed in meeting | Sprint 4 | 1 day | Both members | Both members |
| Finalize individual Markdown files | Remaining submission task | Sprint 4 | 1 day | Each member | Other member |
| Commit and push individual files | Remaining submission task | Sprint 4 | 1 day | Each member | Other member |

## Next Steps

Finish saving the individual architecture document and meeting notes. Commit and push the files to each member's own GitHub repository. Check that the files appear on GitHub before submitting the personal repository link to GeorgiaVIEW.

The design describes planned application files. It does not claim that the application has already been implemented or deployed.

The estimates above are planned work time rather than recorded hours.