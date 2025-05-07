1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
```
SELECT 
    students.*, degrees.name
FROM
    students
        JOIN
    degrees ON students.degree_id = degrees.id
WHERE
    degrees.name = 'Corso di Laurea in Economia'
```
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze
```
SELECT 
    degrees.id,
    degrees.department_id,
    degrees.name,
    degrees.level,
    departments.id,
    departments.name
FROM
    degrees
        JOIN
    departments ON departments.id = degrees.department_id
WHERE
    departments.name = 'Dipartimento di Neuroscienze'
        AND degrees.level = 'magistrale'

```

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
```
SELECT 
    teachers.id,
    teachers.name,
    teachers.surname,
    courses.name,
    courses.period,
    courses.year,
    courses.cfu
FROM
    univerity.teachers
        JOIN
    course_teacher ON course_teacher.teacher_id = teachers.id
        JOIN
    courses ON course_teacher.course_id = courses.id
WHERE
    teachers.id = 44
```
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome
```
SELECT 
    *
FROM
    univerity.students
        JOIN
    degrees ON students.degree_id = degrees.id
        JOIN
    departments ON degrees.department_id = departments.id
ORDER BY students.surname , students.name
```
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
```
SELECT 
    *
FROM
    univerity.degrees
        JOIN
    courses ON courses.degree_id = degrees.id
        JOIN
    course_teacher ON course_teacher.course_id = courses.id
        JOIN
    teachers ON teachers.id = course_teacher.teacher_id
ORDER BY degrees.name, teachers.surname, teachers.name
```
6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)
```
SELECT 
     teachers.name, teachers.surname
FROM
    teachers
        JOIN
    course_teacher ON teacher_id = teachers.id
        JOIN
    courses ON courses.id = course_teacher.course_id
        JOIN
    degrees ON courses.degree_id = degrees.id
        JOIN
    departments ON degrees.department_id = departments.id
WHERE
    departments.name = 'Dipartimento di Matematica'
GROUP BY teachers.name, teachers.surname
ORDER BY teachers.name
```
7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18.