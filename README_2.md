1.  Selezionare tutti gli studenti nati nel 1990 (160)

    ```mysql
        SELECT *
        FROM students
        WHERE YEAR(students.date_of_birth) LIKE 1990
    ```

---

2.  Selezionare tutti i corsi che valgono più di 10 crediti (479)

    ```mysql
        SELECT *
        FROM courses
        WHERE courses.cfu > 10
    ```

---

3.  Selezionare tutti gli studenti che hanno più di 30 anni

    ```mysql
        SELECT *
        FROM students
        WHERE TIMESTAMPDIFF(YEAR, students.date_of_birth, CURDATE()) > 30
    ```

---

4.  Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

    ```mysql
        SELECT *
        FROM courses
        WHERE
            courses.period LIKE "I semestre" AND courses.year LIKE 1
    ```

---

5.  Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

    ```mysql
        SELECT *
        FROM exams
        WHERE
        	YEAR(exams.date) = 2020 AND
            MONTH(exams.date) = 06 AND
            DAY(exams.date) = 20 AND
            HOUR(exams.hour) >= 14
    ```

---

6.  Selezionare tutti i corsi di laurea magistrale (38)

    ```mysql
        SELECT *
        FROM degrees
        WHERE degrees.name LIKE "%laurea magistrale%"
    ```

---

7.  Da quanti dipartimenti è composta l'università? (12)

    ```mysql
        SELECT count(*)
        FROM departments
    ```

---

8.  Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

    ```mysql
        SELECT count(*)
        FROM teachers
        WHERE teachers.phone IS NOT NULL
    ```
