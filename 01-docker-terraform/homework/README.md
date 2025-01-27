# Module 1 Homework: Docker & SQL

This repository contains solutions for the homework questions related to Docker, SQL, and Terraform. Below are the answers and explanations for each question.

---

## **Question 1: Version of `pip` in `python:3.12.8` Image**
**Answer:** `24.3.1`  
**Explanation:**  
Run the following command to start the Docker container and check the `pip` version:
```bash
docker run -it --entrypoint bash python:3.12.8
pip --version


Question 2: Hostname and Port for pgadmin to Connect to Postgres

Answer: db:5432
Explanation:
In the Docker network, services communicate using their service names as hostnames. Since the Postgres service is named db and the internal port is 5432, pgadmin uses db:5432.

Question 3: Trip Segmentation Count (Oct 1–31, 2019)

Answer: 104,793; 202,661; 109,603; 27,678; 35,189

SQL Query:

SELECT
    COUNT(CASE WHEN trip_distance <= 1 THEN 1 END) AS "up_to_1",
    COUNT(CASE WHEN trip_distance > 1 AND trip_distance <= 3 THEN 1 END) AS "1_to_3",
    COUNT(CASE WHEN trip_distance > 3 AND trip_distance <=7 THEN 1 END) AS "3_to_7",
    COUNT(CASE WHEN trip_distance >7 AND trip_distance <=10 THEN 1 END) AS "7_to_10",
    COUNT(CASE WHEN trip_distance >10 THEN 1 END) AS "over_10"
FROM green_taxi_trips
WHERE lpep_pickup_datetime >= '2019-10-01' 
  AND lpep_pickup_datetime < '2019-11-01';

 Question 4: Longest Trip Distance per Day

Answer: 2019-10-31
SQL Query:


SELECT DATE(lpep_pickup_datetime) AS pickup_day, MAX(trip_distance) AS max_distance
FROM green_taxi_trips
GROUP BY pickup_day
ORDER BY max_distance DESC
LIMIT 1;


Question 5: Top Pickup Zones (2019-10-18)

Answer: East Harlem North, Morningside Heights
SQL Query:


SELECT z."Zone", SUM(t.total_amount) AS total
FROM green_taxi_trips t
JOIN taxi_zone z ON t."PULocationID" = z."LocationID"
WHERE DATE(lpep_pickup_datetime) = '2019-10-18'
GROUP BY z."Zone"
HAVING SUM(t.total_amount) > 13000
ORDER BY total DESC;


Question 6: Largest Tip from East Harlem North (Oct 2019)

Answer: JFK Airport
SQL Query:


SELECT dz."Zone", MAX(t.tip_amount) AS max_tip
FROM green_taxi_trips t
JOIN taxi_zone pz ON t."PULocationID" = pz."LocationID"
JOIN taxi_zone dz ON t."DOLocationID" = dz."LocationID"
WHERE pz."Zone" = 'East Harlem North' 
  AND DATE(lpep_pickup_datetime) BETWEEN '2019-10-01' AND '2019-10-31'
GROUP BY dz."Zone"
ORDER BY max_tip DESC
LIMIT 1;


Question 7: Terraform Workflow

Answer:

Setup: terraform init
Apply Changes: terraform apply -auto-approve
Destroy Resources: terraform destroy