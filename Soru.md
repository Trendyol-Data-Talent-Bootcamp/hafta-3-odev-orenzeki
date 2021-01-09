```sql
SELECT name, 
       new_car.id AS car_id, 
       new_car.model AS car_model, 
       new_manufacture.year AS manufacture_year,
       ARRAY(SELECT AS STRUCT new_purchase.id, 
                              TIMESTAMP_ADD(new_purchase.date, INTERVAL 3 HOUR) AS date
             FROM UNNEST(purchase) AS new_purchase) AS purchase
FROM `dsmbootcamp.sample.semi_structured_hw`
JOIN UNNEST(car) AS new_car
JOIN UNNEST(manufacture) AS new_manufacture ON new_car.id = new_manufacture.id ;
```
