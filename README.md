--SQL Query
--Query to get user-level dataset:
SELECT u.id AS "User ID",
      u.country AS "Country",
      u.gender AS "Gender", 
      g.device AS "Device Type", 
      g.group AS "Test Group",
      CASE
      WHEN SUM (a.spent) > 0 THEN 1
      ELSE 0 END AS "Converted",
      COALESCE (SUM (a. spent), 0) AS "Total Spent"
FROM users u 
LEFT JOIN
      activity a ON u.id = a.uid 
LEFT JOIN
      groups g ON u.id = g.uid 
GROUP BY u.id,
      u.country, 
      u.gender, 
      g.device, 
      g.group;

--Query for Novelty Effect:

SELECT a.dt AS date,
    (SUM(CASE WHEN g.group = 'B' THEN a.spent ELSE 0 END) / COUNT(DISTINCT CASE WHEN g.group = 'B' THEN u.id END)) AS treatment_conversion_rate, 
    (SUM(CASE WHEN g.group = 'A' THEN a.spent ELSE 0 END) / COUNT(DISTINCT CASE WHEN g.group = 'A' THEN u.id END)) AS control_conversion_rate,
    (SUM(CASE WHEN g.group = 'B' THEN a.spent ELSE 0 END) / COUNT(DISTINCT CASE WHEN g.group = 'B' THEN u.id END))
    - (SUM(CASE WHEN g.group = 'A' THEN a.spent ELSE 0 END) / COUNT(DISTINCT CASE
WHEN g.group = 'A' THEN u.id END)) AS conversion_rate_difference 
FROM users AS u
JOIN activity AS a
    ON u.id = a.uid 
JOIN groups AS g
    ON u.id = g.uid GROUP BY a.dt
ORDER BY conversion_rate_difference;

 
