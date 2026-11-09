Malachi Johnson

# Project 4 — Meeting 2

Date: October 26, 2026
Time: 3:00 PM–3:30 PM
Team: Group 4
Members: Malachi Johnson and Jalen Davis
Project: Final Grade Calculator
Sprint: 4

## Discussion

We reviewed our component assignments and the files needed for each component.

My Course Management Component will handle course creation and updates and course information validation. It will also organize assignments under their related courses.

The planned files include Course.java and CourseController.java and CourseService.java and CourseRepository.java. Assignment.java and AssignmentRepository.java will support access to related assignments.

Jalen's Grade Calculation Component will handle current grades and weighted grades and required final exam scores and estimated final grades.

We agreed to use one shared MySQL database. The browser will send requests to the backend. The backend will use repositories to read and save database records.

## Database Design

My Courses table will contain course_id and course_name and course_code and credit_hours. The course_id field will be an automatically generated primary key.

Jalen's Assignments table will contain assignment_id and course_id and assignment_name and category and weight and score and max_score.

One course can have many assignments. Each assignment belongs to one course. The course_id in Assignments will reference the primary key in Courses.

## Product Backlog

| PBI | Status | Sprint | Estimate | Assigned | Reviewer |
|---|---|---|---|---|---|
| Identify component subcomponents | Discussed | Sprint 4 | 2 days | Both members | Both members |
| Identify necessary application files | Initial list prepared | Sprint 4 | 2 days | Both members | Both members |
| Design Courses table | Structure drafted | Sprint 4 | 1 day | Malachi Johnson | Jalen Davis |
| Design Assignments table | Structure drafted | Sprint 4 | 1 day | Jalen Davis | Malachi Johnson |
| Define the relationship between tables | Discussed | Sprint 4 | 1 day | Both members | Both members |
| Review container configuration | Planned for next meeting | Sprint 4 | 1 day | Both members | Both members |

## Next Steps

I will finish documenting Course Management and the Courses table. Jalen will finish documenting Grade Calculation and the Assignments table. We will review the container design and check that our documents use the same technologies and table relationships.

The estimates above are planned work time rather than recorded hours.