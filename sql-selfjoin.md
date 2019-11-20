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



SELECT a.company, a.num, stopa.name, stopb.name
FROM route a JOIN route b ON
  (a.company=b.company AND a.num=b.num)
  JOIN stops stopa ON (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
WHERE stopa.name='Craiglockhart' AND stopb.name = 'London Road'


## 7 

SELECT DISTINCT a.company, a.num
FROM route a JOIN route b ON
  (a.company=b.company AND a.num=b.num)
  JOIN stops stopa ON (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
WHERE stopa.name='Haymarket' AND stopb.name = 'Leith'

## 8 

SELECT DISTINCT a.company, a.num
FROM route a JOIN route b ON
  (a.company=b.company AND a.num=b.num)
  JOIN stops stopa ON (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
WHERE stopa.name='Craiglockhart' AND stopb.name = 'Tollcross'

## 9

SELECT DISTINCT stopb.name, a.company, a.num
FROM route a JOIN route b ON
  (a.company=b.company AND a.num=b.num)
  JOIN stops stopa ON (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
WHERE stopa.name = 'Craiglockhart'

## 10

SELECT DISTINCT a.num, a.company, stopb.name ,  x.num,  x.company
FROM route a JOIN route b
ON (a.company = b.company AND a.num = b.num)
JOIN ( route x JOIN route z ON (x.company = z.company AND x.num= z.num))
JOIN stops stopa ON (a.stop = stopa.id)
JOIN stops stopb ON (b.stop = stopb.id)
JOIN stops stopx ON (x.stop = stopx.id)
JOIN stops stopz ON (z.stop = stopz.id)
JOIN stops ON(stops.id = x.stop)
WHERE  stopa.name = 'Craiglockhart' AND stopz.name = 'Lochend' AND  stopb.name = stopx.name

