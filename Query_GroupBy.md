1. Contare quanti iscritti ci sono stati ogni anno

SELECT COUNT(*) AS N_studenti, enrolment_date FROM `students` GROUP By enrolment_date ASC

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT COUNT(*) AS N_Insegnanti, office_address FROM `teachers` GROUP BY office_address

3. Calcolare la media dei voti di ogni appello d'esame

SELECT AVG(vote) as Media_Voti, exam_id FROM `exam_student` GROUP By exam_id

4. Contare quanti corsi di laurea ci sono per ogni dipartimento


