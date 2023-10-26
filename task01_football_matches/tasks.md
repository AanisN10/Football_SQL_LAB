# Football Matches - Tasks

Each of the questions/tasks below can be answered using a `SELECT` query. When you find a solution copy it into the code block under the question before pushing your solution to GitHub.

1) Find all the matches from 2017.

```sql
<!-- SELECT * FROM Matches where season =2017 -->


```

2) Find all the matches featuring Barcelona.

```sql
<!-- SELECT * FROM Matches where hometeam= 'Barcelona' OR awayteam='Barcelona'; -->


```

3) What are the names of the Scottish divisions included?

```sql
<!-- SELECT name FROM Divisions Where country = 'Scotland'; -->


```

4) Find the value of the `code` for the `Bundesliga` division. Use that code to find out how many matches Freiburg have played in that division. HINT: You will need to query both tables

```sql
<!-- SELECT code FROM Divisions WHERE name = 'Bundesliga';
<!-- SELECT COUNT(*) FROM Matches where division_code = 'D1' AND(hometeam='Freiburg' OR awayteam ='Freiburg');-->


```

5)  Find the teams which include the word "City" in their name. HINT: Not every team has been entered into the database with their full name, eg. `Norwich City` are listed as `Norwich`. If your query is correct it should return four teams.

```sql
<!-- SElECT DISTINCT hometeam FROM Matches WHERE hometeam LIKE ('%City%'); -->


```

6) How many different teams have played in matches recorded in a French division?

```sql
<!-- SELECT code FROM Divisions WHERE COUNTRY = 'France' ; 
<!-- SELECT COUNT(DISTINCT hometeam) FROM Matches WHERE division_code = 'F1' OR division_code= 'F2' -->


```

7) Have Huddersfield played Swansea in any of the recorded matches?

```sql
<!-- SELECT distinct hometeam, awayteam, season FROM Matches Where (hometeam = 'Huddersfield' And awayteam = 'Swansea') OR (hometeam= 'Swansea' And awayteam = 'Huddersfield'); -->


```

8) How many draws were there in the `Eredivisie` between 2010 and 2015?

```sql
<!-- SELECT * FROM Divisions WHERE name = 'Eredivisie'; 
<!-- SELECT COUNT(*) FROM Matches Where division_code ='N1' AND (season BETWEEN 2010 AND 2015 ) AND ftr ='D'; -->


```

9) Select the matches played in the Premier League in order of total goals scored (`fthg` + `ftag`) from highest to lowest. When two matches have the same total the match with more home goals (`fthg`) should come first. 

```sql
<!-- SELECT * FROM Divisions WHERE country = 'England';
<!-- SELECT * FROM Matches WHERE division_code= 'E0';
<!-- SELECT *, (fthg+ ftag) AS TG FROM Matches WHERE division_code = 'E0'  ORDER BY TG DESC, fthg DESC;   -->


```

10) Find the name of the division in which the most goals were scored in a single season and the year in which it happened.

```sql
<!--  SELECT division_code, season, SUM(fthg + ftag) AS STG FROM Matches GROUP BY division_code , season ORDER BY STG DESC LIMIT 1;
<!--SELECT name FROM Divisions WHERE code = 'EC';
 -->


```

### Useful Resources

- [Filtering results](https://www.w3schools.com/sql/sql_where.asp)
- [Ordering results](https://www.w3schools.com/sql/sql_orderby.asp)
- [Grouping results](https://www.w3schools.com/sql/sql_groupby.asp)