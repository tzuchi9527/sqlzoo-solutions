# SELECT basics

1. The example uses a WHERE clause to show the population of 'France'. Note that strings (pieces of text that are data) should be in 'single quotes';

```sql
SELECT population 
FROM world
WHERE name = 'Germany'
```
2. Checking a list The word IN allows us to check if an item is in a list. The example shows the name and population for the countries 'Brazil', 'Russia', 'India' and 'China'.

```sql
SELECT name, population
FROM world
WHERE name IN ('Norway', 'Sweden','Denmark')
```

3. Which countries are not too small and not too big? BETWEEN allows range checking (range specified is inclusive of boundary values). The example below shows countries with an area of 250,000-300,000 sq. km. Modify it to show the country and the area for countries with an area between 200,000 and 250,000.

```sql
SELECT name, area 
FROM world
WHERE area BETWEEN 200000 AND 250000
```

# quiz

![](https://i.imgur.com/PrnKCXn.png)

![](https://i.imgur.com/vuYqBiJ.png)

![](https://i.imgur.com/C5IMfrK.png)

![](https://i.imgur.com/1A0QliB.png)

![](https://i.imgur.com/E5BJDH2.png)

![](https://i.imgur.com/hNpCtO8.png)

![](https://i.imgur.com/kIjvWlk.png)

![](https://i.imgur.com/XhgYxvj.png)

![](https://i.imgur.com/doVMB5N.png)

![](https://i.imgur.com/WuphmPv.png)

![](https://i.imgur.com/HOYoiEA.png)

![](https://i.imgur.com/TdHOXnl.png)

![](https://i.imgur.com/eMpLabe.png)

![](https://i.imgur.com/IYJF6rv.png)

![](https://i.imgur.com/pYHg2cW.png)
