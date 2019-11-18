
# 1 

SELECT population FROM world
  WHERE name = 'Germany'

# 2
SELECT population FROM world
  WHERE name = 'France'

## 3

SELECT name, population FROM world
  WHERE name IN ( 'Sweden','Norway','Denmark');

