# SQL-queries

1.  Select countries where a total number of inhabitants (population) in all cities is greater than 400.  
```
select country.Name
FROM country
 INNER Join (SELECT CountryID ,sum(Population) as allPopulation from City GROUP by CountryID) s 
 WHERE country.CountryID = s.CountryID 
 AND s.allPopulation > 400 
```
2.Select names of the countries that have no buildings at all  
```
select c.Name 
from Country c 
where 0 = ( select COUNT(*) from City t 
           INNER JOIN Building B ON B.CityID = t.CityID 
           where t.CountryID = c.CountryID 
          )
```
