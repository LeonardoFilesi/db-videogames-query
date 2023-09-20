# db-videogames-query
===SELECT===
1)
SELECT *
FROM software_houses
WHERE country LIKE 'United States';
2)
SELECT *
FROM players
WHERE city LIKE 'Rogahnland';
3)
SELECT *
FROM players
WHERE name LIKE '%a';
4)
SELECT *
FROM reviews
WHERE player_id = 800;
5)
SELECT *
FROM tournaments
WHERE year = 2015;
6)
SELECT *
FROM awards
WHERE description LIKE '%facere%';
7)
SELECT DISTINCT videogame_id
FROM category_videogame
WHERE category_id IN (2,6);
8)
SELECT *
FROM reviews
WHERE rating >= 2 AND rating <= 4;
9)
SELECT *
FROM videogames
WHERE DATEPART(year, release_date) = 2020;
10)
SELECT DISTINCT videogame_id
FROM reviews
WHERE rating = 5;
