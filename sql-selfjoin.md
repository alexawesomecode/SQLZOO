## 1

SELECT COUNT(stops.name)
FROM stops

## 2

SELECT id
FROM stops
WHERE name = 'Craiglockhart'

## 3

SELECT stops.id, stops.name
FROM stops
JOIN route ON (route.stop=stops.id)
WHERE route.company = 'LRT' AND route.num = 4

# 4

SELECT company, num, COUNT(*)
FROM route WHERE stop=149 OR stop=53
GROUP BY company, num
HAVING COUNT(route.num) > 1


## 5

SELECT a.company, a.num, a.stop, b.stop
FROM route a JOIN route b ON
  (a.company=b.company AND a.num=b.num)
WHERE a.stop=53  AND b.stop=149

## 6



