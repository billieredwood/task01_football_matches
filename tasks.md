# Football Matches - Tasks

Each of the questions/tasks below can be answered using a `SELECT` query. When you find a solution copy it into the code block under the question before pushing your solution to GitHub.

1) Find all the matches from 2017.

```sql
<!-- Copy solution here -->
SELECT * FROM matches WHERE season = '2017';

```

2) Find all the matches featuring Barcelona.

```sql
<!-- Copy solution here -->
SELECT * FROM matches WHERE hometeam = 'Barcelona' OR awayteam = 'Barcelona';

```

3) What are the names of the Scottish divisions included?

```sql
<!-- Copy solution here -->
SELECT * FROM divisions WHERE country = 'Scotland';
SELECT DISTINCT name FROM divisions WHERE name LIKE '%Scottish%';
```

4) Find the value of the `code` for the `Bundesliga` division. Use that code to find out how many matches Freiburg have played in that division. HINT: You will need to query both tables
374


```sql
<!-- Copy solution here -->
SELECT * FROM divisions WHERE name = 'Bundesliga';           -- D1 is the value of the code.

SELECT * FROM matches WHERE division_code = 'D1' AND (hometeam = 'Freiburg' OR awayteam = 'Freiburg');

SELECT COUNT(*) FROM matches WHERE division_code = 'D1' AND (hometeam = 'Freiburg' OR awayteam = 'Freiburg');
```

5)  Find the teams which include the word "City" in their name. HINT: Not every team has been entered into the database with their full name, eg. `Norwich City` are listed as `Norwich`. If your query is correct it should return four teams.

```sql
<!-- Copy solution here -->
SELECT DISTINCT hometeam FROM matches WHERE hometeam LIKE '%City%';

```

6) How many different teams have played in matches recorded in a French division?

```sql
<!-- Copy solution here -->

SELECT * FROM divisions WHERE country LIKE '%France%';  --finds count of 4, code of f1 and f2

SELECT DISTINCT hometeam FROM matches WHERE division_code IN ('F1', 'F2');  --shows team names
or
SELECT COUNT(DISTINCT hometeam) FROM matches WHERE division_code IN ('F1', 'F2');       -- to count of 61 teams


```

7) Have Huddersfield played Swansea in any of the recorded matches?

```sql
<!-- Copy solution here -->

-- to confirm that they have played; showing a count of 12:
SELECT COUNT(*) FROM matches WHERE hometeam = 'Swansea' AND awayteam = 'Huddersfield' OR hometeam = 'Huddersfield' AND awayteam = 'Swansea';

-- to show the games that they have played together:
SELECT * FROM matches WHERE hometeam = 'Swansea' AND awayteam = 'Huddersfield' OR hometeam = 'Huddersfield' AND awayteam = 'Swansea';

```

8) How many draws were there in the `Eredivisie` between 2010 and 2015?

```sql
<!-- Copy solution here -->
SELECT COUNT(*) FROM matches WHERE division_code LIKE '%N1%' AND ftr = 'D' AND season > '2009' AND season < '2016';
--finds a total of 431 draws between 2010 to 2015.


-- finds the code data from division name:
SELECT * FROM divisions WHERE name LIKE '%Eredivisie%';

SELECT * FROM matches WHERE division_code LIKE '%N1%' AND ftr = 'D' AND season > '2009' AND season < '2016';
```

9) Select the matches played in the Premier League in order of total goals scored (`fthg` + `ftag`) from highest to lowest. When two matches have the same total the match with more home goals (`fthg`) should come first. 

```sql
<!-- Copy solution here -->


```

10) Find the name of the division in which the most goals were scored in a single season and the year in which it happened.

```sql
<!-- Copy solution here -->


```

### Useful Resources

- [Filtering results](https://www.w3schools.com/sql/sql_where.asp)
- [Ordering results](https://www.w3schools.com/sql/sql_orderby.asp)
- [Grouping results](https://www.w3schools.com/sql/sql_groupby.asp)