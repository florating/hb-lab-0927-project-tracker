# Lab Instructions

### Resources
* 0927 Lab Instructions: [here](https://fellowship.hackbrightacademy.com/materials/serft8/exercises/project-tracker/)
* 0927 Lab - Further Study: [here](https://fellowship.hackbrightacademy.com/materials/serft8/exercises/project-tracker/further-study/)
* 0927 Lecture: [SQL I](https://fellowship.hackbrightacademy.com/materials/t3/lectures/sql-1/)
* 0927 Lecture: [SQL II](https://fellowship.hackbrightacademy.com/materials/t3/lectures/sql-2/)


### Next Steps

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