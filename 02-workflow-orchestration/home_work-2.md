# Homework - 2 

## Question 1. 
- [ x ] 128.3 MB
- [ ] 134.5 MB
- [ ] 364.7 MB
- [ ] 692.6 MB

## Question 2. Rendered value 
- [ ] `{{inputs.taxi}}_tripdata_{{inputs.year}}-{{inputs.month}}.csv`
- [ x ] `green_tripdata_2020-04.csv`
- [ ] `green_tripdata_04_2020.csv`
- [ ] `green_tripdata_2020.csv`

## Question 3. Number of rows (yellow, 2020) 
- [ ] 13,537,299
- [ x ] 24,648,499
- [ ] 18,324,219
- [ ] 29,430,127
- 
-- SELECT COUNT(*)
FROM `kestra-sandbox-449309.zoomcamp.yellow_tripdata`
WHERE filename LIKE 'yellow_tripdata_2020%'

## Question 4. Number of rows (green, 2020) 
- [ ] 5,327,301
- [ ] 936,199
- [x ] 1,734,051
- [ ] 1,342,034


-- SELECT COUNT(*)
FROM `kestra-sandbox-449309.zoomcamp.green_tripdata`
WHERE filename LIKE 'green_tripdata_2020%'

## Question 5. Number of rows (yellow, March 2021) 
- [ ] 1,428,092
- [ ] 706,911
- [ x] 1,925,152
- [ ] 2,561,031

## Question 6. Timezone for trigger 
- [ ] Add a timezone property set to EST in the Schedule trigger configuration
- [ x ] Add a timezone property set to America/New_York in the Schedule trigger configuration
- [ ] Add a timezone property set to UTC-5 in the Schedule trigger configuration
- [ ] Add a location property set to New_York in the Schedule trigger configuration
