## 1

SELECT id, title
 FROM movie
 WHERE yr=1962

## 2

SELECT yr
FROM movie
WHERE title = 'Citizen Kane' 

## 3

SELECT id, title, yr
FROM movie
WHERE title LIKE '%Star%Trek%'
ORDER BY yr

## 4

SELECT id
FROM actor
WHERE name = 'Glenn Close'

## 5

SELECT id
FROM movie
WHERE title = 'Casablanca'

## 6 

SELECT name
FROM actor JOIN casting ON (id=actorid)
WHERE movieid=11768

## 7 

SELECT name
FROM actor JOIN casting ON (id=actorid)
JOIN movie ON (movie.id = casting.movieid)
WHERE movie.title = 'Alien'


## 8 

SELECT title
FROM movie JOIN casting ON (id = movieid)
JOIN actor ON (actor.id = casting.actorid)
WHERE actor.name = 'Harrison Ford'

## 9 

SELECT title
FROM movie JOIN casting ON (id = movieid)
JOIN actor ON (actor.id = casting.actorid)
WHERE actor.name = 'Harrison Ford' AND casting.ord <> 1

## 10

SELECT DISTINCT title, name
FROM movie JOIN casting ON (id = movieid)
JOIN actor ON (actor.id = casting.actorid)
WHERE yr = 1962 AND casting.ord = 1

## 11

SELECT yr,COUNT(title) FROM
  movie JOIN casting ON movie.id=movieid
        JOIN actor   ON actorid=actor.id
WHERE name='Rock Hudson'
GROUP BY yr
HAVING COUNT(title) > 2

## 12


SELECT title, name
FROM movie
JOIN casting ON (casting.movieid = movie.id)
JOIN actor ON (casting.actorid = actor.id)
WHERE casting.ord = 1 AND movieid IN
   (SELECT movieid FROM casting, actor
     WHERE actorid=actor.id
     AND name='Julie Andrews')


## 13

SELECT name
FROM actor
JOIN casting ON (casting.actorid=actor.id)
WHERE casting.ord=1 
GROUP BY name
HAVING COUNT(casting.actorid)>=30


## 14

SELECT title, COUNT(actorid)
FROM movie
JOIN casting ON (movie.id=casting.movieid)
WHERE yr=1978 
GROUP BY title
ORDER BY COUNT(actorid) DESC, title


## 14

SELECT name
FROM actor
JOIN casting ON (id=casting.actorid and name!='Art Garfunkel')
WHERE casting.movieid IN (SELECT movieid FROM casting
      WHERE actorid = (SELECT id FROM actor WHERE name='Art Garfunkel'))    

