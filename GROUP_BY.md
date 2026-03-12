1.  Contare quanti iscritti ci sono stati ogni anno

    ```mysql
        SELECT
        	YEAR(enrolment_date) enrolment_year,
            COUNT(YEAR(enrolment_date)) AS enrolment_count
        FROM db_university.students
        GROUP BY YEAR(enrolment_date)
    ```

    | enrolment_year | enrolment_count |
    | -------------- | --------------- |
    | 2019           | 1709            |
    | 2018           | 912             |
    | 2020           | 1645            |
    | 2021           | 734             |

---

2.  Contare gli insegnanti che hanno l'ufficio nello stesso edificio

    ```mysql
        SELECT
        	office_address,
            COUNT(office_address) AS same_address_count
        FROM db_university.teachers
        GROUP BY office_address
    ```

---

3.  Calcolare la media dei voti di ogni appello d'esame

    ```mysql
        SELECT exam_id,
        		AVG(vote) AS avarage_vote
        FROM exam_student
        GROUP BY exam_id
    ```

---

4.  Contare quanti corsi di laurea ci sono per ogni dipartimento

    ```mysql
        SELECT
        	department_id,
            COUNT(name)
        FROM db_university.degrees
        GROUP BY department_id
    ```
