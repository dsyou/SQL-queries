# SQL-queries

1.  Select countries where a total number of inhabitants (population) in all cities is greater than 400.  

select country.Name
FROM country
 INNER Join (SELECT CountryID ,sum(Population) as allPopulation from City GROUP by CountryID) s 
 WHERE country.CountryID = s.CountryID 
 AND s.allPopulation > 400 
