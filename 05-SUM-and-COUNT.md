# SUM and COUNT

1. Show the total population of the world.

```sql
SELECT SUM(population)
FROM world
```

2. List all the continents - just once each.

```sql
SELECT DISTINCT(continent)
FROM world
```

3. Give the total GDP of Africa

```sql
SELECT SUM(gdp)
FROM world
WHERE continent = 'Africa'
```

4. How many countries have an area of at least 1000000

```sql
SELECT COUNT(name)
FROM world
WHERE area >= 1000000
```


5. What is the total population of ('Estonia', 'Latvia', 'Lithuania')


```sql
SELECT SUM(population)
FROM world
WHERE name IN ('Estonia', 'Latvia', 'Lithuania')
```

- Reference: https://sqlzoo.net/wiki/Using_GROUP_BY_and_HAVING.

6. For each continent show the continent and number of countries.

```sql
SELECT continent, COUNT(name)
FROM world
GROUP BY continent
```

7. For each continent show the continent and number of countries with populations of at least 10 million.

```sql
SELECT continent, COUNT(name)
FROM world
WHERE population >= 10000000
GROUP BY continent
```

8. List the continents that have a total population of at least 100 million.

```sql
SELECT continent
FROM world
GROUP BY continent
HAVING SUM(population) > 100000000
```

# Quiz

![](https://i.imgur.com/vhq282X.png)

![](https://i.imgur.com/Nf3wF2g.png)

![](https://i.imgur.com/TL0IP9g.png)

![](https://i.imgur.com/VcxfGJd.png)

![](https://i.imgur.com/seqPh0n.png)

![](https://i.imgur.com/m4KAMhi.png)

![](https://i.imgur.com/9zzGCfh.png)

![](https://i.imgur.com/xPMnOgU.png)

![](https://i.imgur.com/1bSAFN9.png)

![](https://i.imgur.com/KwRe9VC.png)

![](https://i.imgur.com/vtRHCj0.png)

![](https://i.imgur.com/N20u33q.png)

![](https://i.imgur.com/7jqC9Ac.png)

![](https://i.imgur.com/SnT9NAQ.png)

![](https://i.imgur.com/Q1JR7Ki.png)

![](https://i.imgur.com/2AGMN4I.png)
