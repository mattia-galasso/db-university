1.  Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

    ```mysql
        SELECT
        	degrees.id degree_id,
            students.degree_id student_degree_id,
            degrees.name degree_name,
            students.name student_name,
            students.surname student_surname
        FROM db_university.degrees
        INNER JOIN db_university.students
        ON degrees.id = students.degree_id
        WHERE degrees.name LIKE "Corso di Laurea in Economia"
    ```

---

2.  Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
    Neuroscienze

    ```mysql
        SELECT
        	departments.id department_id,
            degrees.department_id degree_department_id,
            departments.name department_name,
            degrees.name degree_name,
            degrees.level degree_level
        FROM db_university.departments
        INNER JOIN db_university.degrees
        ON departments.id = degrees.department_id
        WHERE
        	departments.name LIKE "Dipartimento di Neuroscienze" AND
            degrees.level LIKE "magistrale"
    ```

---

3.  Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

    ```mysql
        SELECT
            teachers.id teacher_id,
            teachers.name teacher_name,
            teachers.surname teacher_surname,
            courses.name course_name,
            courses.description course_description
        FROM teachers

        INNER JOIN course_teacher
        ON teachers.id = course_teacher.teacher_id

        INNER JOIN courses
        ON course_teacher.course_id = courses.id

        WHERE teachers.id LIKE 44
    ```

---

4.  Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
    sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
    nome

    ```mysql
        SELECT
            students.name student_name,
            students.surname student_surname,
            degrees.name degree_name,
            degrees.level degree_level,
            departments.name department_name

        FROM db_university.students

        INNER JOIN degrees
        ON students.degree_id = degrees.id

        INNER JOIN departments
        ON degrees.department_id = departments.id

        ORDER BY students.surname, students.name ASC
    ```

---

5.  Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

    ```mysql
        SELECT
            degrees.name degree_name,
            courses.name course_name,
            teachers.name teacher_name,
            teachers.surname teacher_surname
        FROM db_university.degrees

        # COURSES JOIN
        INNER JOIN courses
        ON degrees.id = courses.degree_id

        # DA COURSES.ID -> COURSE_TEACHER(TABELLA PONTE) -> TEACHERS.ID
        INNER JOIN course_teacher
        ON courses.id = course_teacher.course_id

        INNER JOIN teachers
        ON course_teacher.teacher_id = teachers.id
    ```

---

6.  Selezionare tutti i docenti che insegnano nel Dipartimento di
    Matematica (54)

    ```mysql
        SELECT
            departments.name department_name,
            teachers.name teacher_name,
            teachers.surname teacher_surname

        FROM db_university.departments

        # departments -> degrees -> courses -> course_teacher -> teachers
        INNER JOIN degrees
        ON departments.id = degrees.department_id

        INNER JOIN courses
        ON degrees.id = courses.degree_id

        INNER JOIN course_teacher
        ON courses.id = course_id

        INNER JOIN teachers
        ON course_teacher.teacher_id = teachers.id

        WHERE departments.name LIKE "Dipartimento di Matematica"

        GROUP BY departments.name, teachers.name, teachers.surname
    ```

---

7.  BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
    per ogni esame, stampando anche il voto massimo. Successivamente,
    filtrare i tentativi con voto minimo 18.

```mysql

```
