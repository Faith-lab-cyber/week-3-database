# week-3-database
SELECT COUNT(*) AS total_admissions FROM admissions;
SELECT AVG(DATEDIFF(discharge_date, admission_date)) AS avg_length_of_stay FROM admissions;
SELECT primary_diagnosis, COUNT(*) AS total_admissions FROM admissions GROUP BY primary_diagnosis;
SELECT service, AVG(DATEDIFF(discharge_date, admission_date)) AS avg_length_of_stay FROM admissions GROUP BY service
SELECT discharge_disposition, COUNT(*) AS total_discharges FROM discharges GROUP BY discharge_disposition;
SELECT service, COUNT(*) AS total_admissions FROM admissions GROUP BY service HAVING COUNT(*) > 5;
SELECT AVG(DATEDIFF(discharge_date, admission_date)) AS avg_length_of_stay FROM admissions WHERE primary_diagnosis = 'Stroke';
SELECT acuity, COUNT(*) AS total_visits FROM ed_visits GROUP BY acuity;
SELECT primary_diagnosis, service, COUNT(*) AS total_admissions FROM admissions GROUP BY primary_diagnosis, service;
SELECT MONTH(admission_date) AS admission_month, COUNT(*) AS total_admissions FROM admissions GROUP BY MONTH(admission_date);
SELECT primary_diagnosis, MAX(DATEDIFF(discharge_date, admission_date)) AS max_length_of_stay FROM admissions GROUP BY primary_diagnosis

SELECT service,
       SUM(DATEDIFF(discharge_date, admission_date)) AS total_length_of_stay,
       AVG(DATEDIFF(discharge_date, admission_date)) AS avg_length_of_stay
FROM admissions
GROUP BY service
ORDER BY avg_length_of_stay DESC;