# More JOIN

![](https://i.imgur.com/qEL9Atu.png)

1. List the films where the yr is 1962 [Show id, title]

```sql
SELECT id, title
FROM movie
WHERE yr=1962
```

2. Give year of 'Citizen Kane'.

```sql
SELECT yr
FROM movie
WHERE title = 'Citizen Kane'
```

3. List all of the Star Trek movies, include the id, title and yr (all of these movies include the words Star Trek in the title). Order results by year.

```sql
SELECT id, title, yr
FROM movie
WHERE title LIKE '%star trek%'
ORDER BY yr
```

4. What id number does the actor 'Glenn Close' have?

```sql
SELECT id
FROM actor
WHERE name = 'Glenn Close'
```

5. What is the id of the film 'Casablanca'

```sql
SELECT id
FROM movie
WHERE title = 'Casablanca'
```

6. Obtain the cast list for 'Casablanca'.
    what is a cast list?
    Use movieid=11768, (or whatever value you got from the previous question)
    
```sql
SELECT name
FROM actor, casting
WHERE id=actorid AND movieid = 11768
```

7. Obtain the cast list for the film 'Alien'

```sql
SELECT name
FROM actor, casting
WHERE id=actorid AND movieid = (SELECT id FROM movie WHERE title = 'Alien')
```

8. List the films in which 'Harrison Ford' has appeared

```sql
SELECT title
FROM movie, casting
WHERE id=movieid AND actorid = (SELECT id FROM actor WHERE name = 'Harrison Ford')
```

9. List the films where 'Harrison Ford' has appeared - but not in the starring role. [Note: the ord field of casting gives the position of the actor. If ord=1 then this actor is in the starring role]

```sql
SELECT title
FROM movie, casting
WHERE id=movieid AND actorid = (SELECT id FROM actor WHERE name = 'Harrison Ford') AND ord<>1
```

10. List the films together with the leading star for all 1962 films.

```sql
SELECT title, name
FROM movie JOIN casting ON (id=movieid)
JOIN actor ON (actor.id = actorid)
WHERE ord=1 AND  yr = 1962
```

11. Which were the busiest years for 'John Travolta', show the year and the number of movies he made each year for any year in which he made more than 2 movies.

- busiest year
```sql
SELECT yr,COUNT(title) FROM
  movie JOIN casting ON movie.id=movieid
         JOIN actor   ON actorid=actor.id
WHERE name='John Travolta'
GROUP BY yr
HAVING COUNT(title)=(SELECT MAX(c) FROM
(SELECT yr,COUNT(title) AS c FROM
   movie JOIN casting ON movie.id=movieid
         JOIN actor   ON actorid=actor.id
 WHERE name='John Travolta'
 GROUP BY yr) AS t)
```

- made more than 2 movies
```sql
SELECT yr,COUNT(title) FROM
  movie JOIN casting ON movie.id=movieid
         JOIN actor   ON actorid=actor.id
where name='John Travolta'
GROUP BY yr
HAVING COUNT(title) > 2
```

12. List the film title and the leading actor for all of the films 'Julie Andrews' played in.

```sql
SELECT title, name FROM movie
JOIN casting x ON movie.id = movieid
JOIN actor ON actor.id =actorid
WHERE ord=1 AND movieid IN
(SELECT movieid FROM casting y
JOIN actor ON actor.id=actorid
WHERE name='Julie Andrews')
```

13. Obtain a list, in alphabetical order, of actors who've had at least 30 starring roles.

```sql
SELECT name
FROM actor
  JOIN casting ON (id = actorid AND (SELECT COUNT(ord) FROM casting WHERE actorid = actor.id AND ord=1)>=30)
GROUP BY name
```

14. List the films released in the year 1978 ordered by the number of actors in the cast, then by title.

```sql
SELECT title, COUNT(actorid) as cast
FROM movie JOIN casting on id=movieid
WHERE yr = 1978
GROUP BY title
ORDER BY cast DESC, title
```

15. List all the people who have worked with 'Art Garfunkel'.

```sql
SELECT DISTINCT name
FROM actor JOIN casting ON id=actorid
WHERE movieid IN (SELECT movieid FROM casting JOIN actor ON (actorid=id AND name='Art Garfunkel')) AND name != 'Art Garfunkel'
GROUP BY name
```

# Quiz

![](https://i.imgur.com/3QFXZbS.png)

![](https://i.imgur.com/2XDHJfe.png)

![](https://i.imgur.com/7YxNnBL.png)

![](https://i.imgur.com/dxdJiKl.png)

![](https://i.imgur.com/uuAzowF.png)

![](https://i.imgur.com/SJZZnf0.png)

![](https://i.imgur.com/Fx0dBJK.png)

![](https://i.imgur.com/K0m8q7m.png)

![](https://i.imgur.com/tXiApl4.png)

![](https://i.imgur.com/nGgkrGs.png)

![](https://i.imgur.com/DpqfKL3.png)

![](https://i.imgur.com/Bsx9C2c.png)

![](https://i.imgur.com/vMlsT0E.png)

![](https://i.imgur.com/8sEwCLz.png)

![](https://i.imgur.com/6w6e6HG.png)

