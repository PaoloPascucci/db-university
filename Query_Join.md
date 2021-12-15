1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT * FROM `students` INNER JOIN degrees ON students.degree_id = degrees.id WHERE degrees.name = 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea del Dipartimento di Neuroscienze

SELECT * FROM `degrees` INNER JOIN departments ON degrees.department_id = departments.id WHERE departments.name = 'Dipartimento di Neuroscienze';

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT * FROM `courses` INNER JOIN course_teacher ON courses.id = course_teacher.course_id WHERE course_teacher.teacher_id = 44;

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT students.name , students.surname , degrees.*, departments.name FROM `students` INNER JOIN degrees On students.degree_id = degrees.id INNER join departments ON degrees.department_id = departments.id ORDER BY students.name, students.surname;

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT * FROM `courses` INNER JOIN course_teacher On courses.id = course_teacher.course_id INNER JOIN teachers ON course_teacher.teacher_id = teachers.id;

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT DISTINCT teachers.* FROM `teachers` INNER JOIN course_teacher ON teachers.id = course_teacher.teacher_id INNER JOIN courses ON courses.id = course_teacher.course_id INNER JOIN degrees ON degrees.id = courses.degree_id INNER JOIN departments ON departments.id = degrees.department_id WHERE departments.name = 'Dipartimento di Matematica';

7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami

SELECT COUNT(exams.id) AS N_volte_esame, courses.name, students.name, students.surname
FROM `students` JOIN exam_student ON students.id = exam_student.student_id JOIN exams ON exam_student.exam_id = exams.id JOIN courses ON exams.course_id = courses.id GROUP BY exams.course_id, students.id ORDER by students.surname ASC,students.name ASC;

