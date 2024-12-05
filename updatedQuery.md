# Group by:

### Contare quanti iscritti ci sono stati ogni anno
SELECT YEAR(enrolment_date) AS year, COUNT(*) AS total_students
FROM `students`
GROUP BY YEAR(enrolment_date);


### Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT office_address, COUNT(*) AS tot_teachers
FROM teachers
GROUP BY office_address;


### Calcolare la media dei voti di ogni appello d'esame
SELECT exam_id, AVG(vote) AS avg_vote
FROM exam_student
GROUP BY exam_id;


### Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT department_id, COUNT(*) AS tot_programs
FROM degrees
GROUP BY department_id;




# Joins:

### Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT students.*
FROM students
JOIN degrees ON students.degree_id = degrees.id
WHERE degrees.name = 'Corso di Laurea in Economia';


### Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT degrees.*
FROM degrees
JOIN departments ON degrees.department_id = departments.id
WHERE degrees.level = 'magistrale' AND departments.name = 'Dipartimento di Neuroscienze';


### Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT courses.*
FROM courses
JOIN course_teacher ON courses.id = course_teacher.course_id


### Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
SELECT students.*, departments.name AS department_name, degrees.name AS degree_name
FROM students
JOIN degrees ON students.degree_id = degrees.id
JOIN departments ON degrees.department_id = departments.id
ORDER BY students.surname, students.name;


### Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
SELECT degrees.name AS degree_name, courses.name AS course_name, teachers.name, teachers.surname
FROM degrees
JOIN courses ON degrees.id = courses.degree_id
JOIN course_teacher ON courses.id = course_teacher.course_id
JOIN teachers ON course_teacher.teacher_id = teachers.id;


### Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
SELECT DISTINCT teachers.*
FROM teachers
JOIN course_teacher ON teachers.id = course_teacher.teacher_id
JOIN courses ON course_teacher.course_id = courses.id
JOIN degrees ON courses.degree_id = degrees.id
JOIN departments ON degrees.department_id = departments.id
WHERE departments.name = 'Dipartimento di Matematica';


### BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.