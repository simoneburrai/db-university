1. Contare quanti iscritti ci sono stati ogni anno
```
SELECT 
    COUNT(*), YEAR(enrolment_date)
FROM
    univerity.students
GROUP BY YEAR(enrolment_date);
```
2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```
SELECT 
    COUNT(*), teachers.office_address
FROM
    teachers
GROUP BY teachers.office_address
```
3. Calcolare la media dei voti di ogni appello d'esame
```
SELECT 
    AVG(exam_student.vote) AS `vote_avg`, exam_student.exam_id
FROM
    exam_student
GROUP BY exam_student.exam_id

```
4. Contare quanti corsi di laurea ci sono per ogni dipartimento
```
SELECT 
    COUNT(department_id) AS `number_of_degrees_for_deparment`
FROM
    univerity.degrees
GROUP BY department_id
```