# SQLZoo_Select-from-world
you can get the solutions of "https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial" in this folder

--- Qun 1- Read the notes about this table. Observe the result of running this SQL command to show the name, continent and population of all countries.

Ans - select name, continent, population from world;

  Qun 2 - How to use WHERE to filter records. Show the name for the countries that have a population of at least 200 million. 200 million is 200000000, there are eight zeros.

Ans - select name from world where population > 200000000;

Qun 3 - Give the name and the per capita GDP for those countries with a population of at least 200 million.

HELP:How to calculate per capita GDP
per capita GDP is the GDP divided by the population GDP/population

Ans - select name, GDP/population from world where population > 200000000;

Qun 4 - Show the name and population in millions for the countries of the continent 'South America'. Divide the population by 1000000 to get population in millions.

Ans - select name, population/1000000 from world where continent =  'South America';

Qun 5 - Show the name and population for France, Germany, Italy

Ans - select name, population from world where name IN ('France', 'Germany', 'Italy');

Qun 6 - Show the countries which have a name that includes the word 'United'

Ans - select name from world where name like 'United%'

Qun 7 - Two ways to be big: A country is big if it has an area of more than 3 million sq km or it has a population of more than 250 million.

Ans - Show the countries that are big by area or big by population. Show name, population and area.

Ans - select name, population, area from world where area > 3000000 or population > 250000000

Qun 8 - Exclusive OR (XOR). Show the countries that are big by area (more than 3 million) or big by population (more than 250 million) but not both. Show name, population and area.
Australia has a big area but a small population, it should be included.
Indonesia has a big population but a small area, it should be included.
China has a big population and big area, it should be excluded.
United Kingdom has a small population and a small area, it should be excluded.

Ans - SELECT name, population, area FROM world WHERE (population > 250000000 OR area > 3000000) AND NOT (population > 250000000 AND area > 3000000);

Qun 9 - Show the name and population in millions and the GDP in billions for the countries of the continent 'South America'. Use the ROUND function to show the values to two decimal places.
For Americas show population in millions and GDP in billions both to 2 decimal places.

Ans - SELECT name, ROUND((population/1000000), 2), ROUND((GDP/1000000000), 2) FROM world 
WHERE continent = 'South America'

Qun 10 - Show the name and per-capita GDP for those countries with a GDP of at least one trillion (1000000000000; that is 12 zeros). Round this value to the nearest 1000.
Show per-capita GDP for the trillion dollar countries to the nearest $1000.

Ans - SELECT name, ROUND((gdp/population), -3) FROM world WHERE gdp >= 1000000000000;

Qun 11 - Greece has capital Athens.
Each of the strings 'Greece', and 'Athens' has 6 characters.
Show the name and capital where the name and the capital have the same number of characters.
You can use the LENGTH function to find the number of characters in a string
For Microsoft SQL Server the function LENGTH is LEN

Ans - SELECT name, capital FROM world WHERE LENGTH(name) = LENGTH(capital)

Qun 12 - The capital of Sweden is Stockholm. Both words start with the letter 'S'.
Show the name and the capital where the first letters of each match. Don't include countries where the name and the capital are the same word.
You can use the function LEFT to isolate the first character.
You can use <> as the NOT EQUALS operator.

Ans - select name, capital from world where LEFT(name,1) = LEFT(capital,1) AND name <> capital;

Qun 13 - 
Equatorial Guinea and Dominican Republic have all of the vowels (a e i o u) in the name. They don't count because they have more than one word in the name. Find the country that has all the vowels and no spaces in its name. You can use the phrase name NOT LIKE '%a%' to exclude characters from your results.
The query shown misses countries like Bahamas and Belarus because they contain at least one 'a'

 Ans - SELECT name FROM world WHERE name LIKE '%a%' AND name LIKE '%e%' AND name LIKE '%i%' AND name LIKE '%o%' AND name LIKE '%U%' AND name NOT LIKE '% %';
