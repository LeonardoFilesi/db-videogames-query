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

===GROUP BY===
1)
SELECT COUNT(id)
FROM software_houses
GROUP BY country;
2)
SELECT COUNT(id)
3)
SELECT COUNT(videogame_id)
FROM pegi_label_videogame
GROUP BY pegi_label_id;
4)
SELECT DATEPART(year, release_date) AS year, COUNT(name) AS videogame
FROM videogames
GROUP BY DATEPART(year,release_date);
5)
SELECT COUNT(videogame_id)
FROM device_videogame
GROUP BY device_id;
FROM reviews
GROUP BY videogame_id;
3)
SELECT COUNT(videogame_id)
FROM pegi_label_videogame
GROUP BY pegi_label_id;
4)
SELECT DATEPART(year, release_date) AS year, COUNT(name) AS videogame
FROM videogames
GROUP BY DATEPART(year,release_date);
5)
SELECT COUNT(videogame_id)
FROM device_videogame
GROUP BY device_id;
6)
SELECT videogame_id
FROM reviews
GROUP BY videogame_id
ORDER BY COUNT(rating) DESC;

===JOIN===
1)
SELECT DISTINCT players.*
FROM players
RIGHT JOIN reviews 
ON players.id = reviews.player_id;
2)
SELECT DISTINCT videogame_id
FROM tournament_videogame
RIGHT JOIN tournaments
ON tournament_videogame.tournament_id = tournaments.id
WHERE year = 2016;
3)
SELECT categories.*
FROM categories
RIGHT JOIN category_videogame
ON category_videogame.category_id = categories.id;
(ALTERNATIVA)
SELECT v.id AS videogame_id, v.name AS videogame_name, v.release_date, c.id AS category_id, c.name AS category_name 
FROM videogames v
INNER JOIN category_videogame cv ON v.id = cv.videogame_id
INNER JOIN categories c ON cv.category_id = c.id
ORDER BY videogame_id
4)
SELECT DISTINCT software_houses.*
FROM software_houses
RIGHT JOIN videogames
ON videogames.software_house_id = software_houses.id
WHERE DATEPART(year, release_date) > 2020;
5)
SELECT awards.*
FROM awards
RIGHT JOIN award_videogame
ON award_videogame.award_id = awards.id
LEFT JOIN videogames
ON videogames.id = award_videogame.videogame_id;
6)
SELECT DISTINCT v.name AS videogame_name, c.name AS category_name, pl.name AS pegi_label
FROM videogames v
INNER JOIN category_videogame cv ON v.id = cv.videogame_id
INNER JOIN categories c ON cv.category_id = c.id
INNER JOIN pegi_label_videogame plv ON plv.videogame_id = v.id
INNER JOIN pegi_labels pl ON pl.id = plv.pegi_label_id
INNER JOIN reviews r ON r.videogame_id = v.id
WHERE r.rating >= 4;
