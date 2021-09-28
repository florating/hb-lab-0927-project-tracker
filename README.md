# Lab Instructions

### Resources
* 0927 Lab Instructions: [here](https://fellowship.hackbrightacademy.com/materials/serft8/exercises/project-tracker/)
* 0927 Lab - Further Study: [here](https://fellowship.hackbrightacademy.com/materials/serft8/exercises/project-tracker/further-study/)
* 0927 Lecture: [SQL I](https://fellowship.hackbrightacademy.com/materials/t3/lectures/sql-1/)
* 0927 Lecture: [SQL II](https://fellowship.hackbrightacademy.com/materials/t3/lectures/sql-2/)
* PostgreSQL Documentation: [info for ALTER TABLE](https://www.postgresql.org/docs/9.1/sql-altertable.html)
* ANKI flashcards: [subreddit](https://www.reddit.com/r/Anki/), [official website](https://apps.ankiweb.net)


### General Lab Tasks

* Query 1: SELECT fname, lname FROM students WHERE github = 'jhacks';

* Query 2: SELECT project_title, grade FROM grades WHERE student_github = 'jhacks';

* Query 3: SELECT title, max_grade FROM projects;

```sql
SELECT * FROM students JOIN grades ON (students.github = grades.student_github);
```

// table1.col1 = table2.col2

```sql
SELECT students.fname,
       students.lname,
       grades.project_title,
       grades.grade
FROM students
  JOIN grades ON (students.github = grades.student_github);
```

```sql
SELECT * FROM students
  JOIN grades ON (students.github = grades.student_github)
  JOIN projects ON (grades.project_title = projects.title)
    WHERE github = 'jhacks';
```

```sql
SELECT fname, lname, project_title, grade, max_grade
FROM students
  JOIN grades ON (students.github = grades.student_github)
  JOIN projects ON (grades.project_title = projects.title)
    WHERE github = 'jhacks';
```

### Further Study
#### Creating Views
```sql
CREATE VIEW report_card_view AS
SELECT students.fname,
       students.lname,
       projects.title,
       projects.max_grade,
       grades.grade
FROM students
  JOIN grades ON (students.github = grades.student_github)
  JOIN projects ON (projects.title = grades.project_title);
```


What we did:
```sql
CREATE VIEW report_card_view AS
SELECT s.fname, s.lname, p.title, p.max_grade, g.grade
FROM students AS s
  JOIN grades AS g ON (s.github = g.student_github)
  JOIN projects AS p ON (p.title = g.project_title);
```


To display the view as a regular table:
```sql
SELECT * FROM report_card_view;
```


#### Setting Other Primary Keys
To alter tables in PostgreSQL you can use the `ALTER TABLE` command.

*Note: not all databases support the ALTER TABLE command.*
