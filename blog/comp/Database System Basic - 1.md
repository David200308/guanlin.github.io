<center>
  <h1>Database System Basic - 1 </h1>
  <h2>Intermediate SQL</h2>
</center>

---

## Example Database Table

### student (sid, name, login, gpa)

| Sid   | Name   | Login      | Age  | Gpa  |
| ----- | ------ | ---------- | ---- | ---- |
| 53666 | Kanye  | kanye@cs   | 44   | 4.0  |
| 53688 | Bieber | jbieber@cs | 27   | 3.9  |
| 53655 | Tupac  | shakur@cs  | 25   | 3.5  |

### enrolled (sid, cid, grade)

| Sid   | Cid    | Grade |
| ----- | ------ | ----- |
| 53666 | 15-445 | C     |
| 53688 | 15-721 | A     |
| 53688 | 15-826 | B     |
| 53655 | 15-445 | B     |
| 53666 | 15-721 | C     |

### course (cid, name)

| Cid    | Name                         |
| ------ | ---------------------------- |
| 15-445 | Database Systems             |
| 15-721 | Advanced Database Systems    |
| 15-826 | Data Mining                  |
| 15-823 | Advanced Topics in Databases |



(P.S. The SQL below all use example data table)

## Basic Syntax

### Basic

Ex: Which students age > 25?

```sql
SELECT name, gpa
	FROM student
	WHERE age > 25
```

### Joins

Ex: Which students got an A in 15-721?

```sql
SELECT s.name
	FROM enrolled AS e, student AS s
	WHERE e.grade = 'A' AND e.cid = '15 - 721' 
		AND e.sid = s.sid
```



## A. Aggregates

| Name       | Definition                      |
| ---------- | ------------------------------- |
| AVG(col)   | Return the average col value    |
| MIN(col)   | Return the minimum col value    |
| MAX(col)   | Return the maximum col value    |
| SUM(col)   | Return the sum of values in col |
| COUNT(col) | Return # of values for col      |

Ex: Get # of students with a "@cs" login?

``` sql
SELECT COUNT(login) AS cnt
	FROM student WHERE login LIKE '%@cs'
```

``` sql
SELECT COUNT(*) AS cnt
	FROM student WHERE login LIKE '%@cs'
```

``` sql
SELECT COUNT(1) AS cnt
	FROM student WHERE login LIKE '%@cs'
```



### Multiple Aggregates

```sql
SELECT AVG(gpa), COUNT(sid)
	FROM student WHERE login LIKE '%@cs'
```



### Distinct Aggregates

```sql
SELECT COUNT(DISTINCT login)
	FROM student WHERE login LIKE '%@cs'
```



### Example: 

Get the average GPA of students enrolled in each course?

```sql
SELECT AVG(s.gpa), e.cid
	FROM enrolled AS e, student AS s
	WHERE e.sid = s.sid
```



## B. Group By

Project tuples into subsets and calculate aggregates against each subset.

```sql
SELECT AVG(s.gpa), e.cid
	FROM enrolled AS e, student AS s
	WHERE e.sid = s.sid
	GROUP BY e.cid
```

#### Display:

<img src="/Users/davidjiang/Library/Application Support/typora-user-images/image-20220514185653747.png" alt="image-20220514185653747" style="zoom:70%;" />

Non-aggregated values in SELECT output clause must appear in GROUP BY clause. For example:

```sql
SELECT AVG(s.gpa), e.cid, s.name
	FROM enrolled AS e, student AS s
	WHERE e.sid = s.sid
	GROUP BY e.cid, s.name
```



## C. Having

Filters results based on aggregation computation. Like a WHERE clause for a GROUP BY.

```sql
SELECT AVG(s.gpa) AS avg_gpa, e.cid
	FROM enrolled AS e, student AS s
	WHERE e.sid = s.sid
	GROUP BY e.cid
	HAVING avg_gpa > 3.9;
```

#### Display:

<img src="/Users/davidjiang/Library/Application Support/typora-user-images/image-20220514190528979.png" alt="image-20220514190528979" style="zoom:70%;" />



## D. String Operations

|          | String Case | String Quotes   |
| -------- | ----------- | --------------- |
| SQL-92   | Sensitive   | Single Only     |
| Postgres | Insensitive | Single Only     |
| MySQL    | Sensitive   | Single / Double |
| SQLite   | Sensitive   | Single / Double |
| DB2      | Sensitive   | Single Only     |
| Oracle   | Sensitive   | Single Only     |

SQL-92:

```sql
WHERE UPPER(name) = UPPER('KaNyE')
```

MySQL:

```sql
WHERE name = "KaNyE"
```



### 1. LIKE Operators

**LIKE**: is used for string matching.

#### String-matching Operators

'%' --> Matches any substring (include empty strings)

'_' --> Match any one character

```sql
SELECT * FROM enrolled AS e
	WHERE e.cid LIKE '15-%'
```

```sql
SELECT * FROM student AS s
	WHERE s.login LIKE '%@c_'
```



### 2. || Operator (use in SQL-92)

```sql
SELECT name FROM student
	WHERE login = LOWER(name) || '@cs'
```

But in MySQL use CONCAT()

```sql
SELECT name FROM student
	WHERE login = CONCAT(LOWER(name), '@cs')
```



## E. Date / Time Operations

SQL-92 & MySQL:

```sql
SELECT NOW();
```

...



## F. Output Redirection

### 1. Store

Store query results in another table:

SQL-92:

```sql
SELECT DISTINCT cid INTO CourseIds
	FROM enrolled;
```

MySQL:

```sql
CREATE TABLE CourseIds (SELECT DISTINCT cid FROM enrolled);
```



### 2. Insert

Insert tuples from query into another table:

--> Inner SELECT must generate the same columns as the target table

SQL-92:

```sql
INSERT INTO CourseIds
(SELECT DISTINCT cid FROM enrolled);
```



## G. Output Control

### 1. ORDER BY <column*> [ASC | DESC]

--> Order the output tuples by the values in one or more of their columns.

```sql
SELECT sid, grade FROM enrolled
	WHERE cid = '15-721'
	ORDER BY grade
```



```sql
SELECT sid, grade FROM enrolled
	WHERE cid = '15-721'
	ORDER BY 1
```

```sql
SELECT sid FROM enrolled
	WHERE cid = '15-721'
	ORDER BY grade DESC, sid ASC
```

#3 Display ==> <img src="/Users/davidjiang/Library/Application Support/typora-user-images/image-20220514193957999.png" alt="image-20220514193957999" style="zoom:70%;" />

```sql
SELECT sid FROM enrolled
	WHERE cid = '15-721'
	ORDER BY grade DESC, 1 ASC
```



### 2. LIMIT <count> [offset]

--> Limit the # of tuples return in output

--> Can set an offset to return a "range"

```sql
SELECT sid, name FROM student
	WHERE login LIKE '%@cs'
	LIMIT 10
```

```sql
SELECT sid, name FROM student
	WHERE login LIKE '%@cs'
	LIMIT 20 OFFSET 10
```



## H. Nested Queries

Queries containing other queries.

Inner queries can appear anywhere in query.

```sql
SELECT name FROM student WHERE
	sid IN (SELECT sid FROM enrolled)
```

inside ( ): Inner Query

outside ( ): Outer Query



Ex. Get the names of students in '15-445'

```sql
SELECT name FROM student 
	WHERE sid IN(
		SELECT sid FROM enrolled
    WHERE cid = '15-445'
  )
```



| Nested Queries | Definition                                                   |
| -------------- | ------------------------------------------------------------ |
| ALL            | Must satisfy expression for all rows in the sub-query        |
| ANY            | Must satisfy expression for at least one row in the sub-query |
| IN             | Equivalent to ' = ANY( ) '                                   |
| EXISTS         | At least one row is returned                                 |



### NOT EXISTS

Ex. Find all courses that have no students enrolled in it.

```sql
SELECT * FROM student 
	WHERE NOT EXISTS(
		SELECT * FROM enrolled
    WHERE course.cid = enrolled.cid
  )
```

Display ==> <img src="/Users/davidjiang/Library/Application Support/typora-user-images/image-20220514195713633.png" alt="image-20220514195713633" style="zoom:70%;" />



## I. Window Functions

### 1. Special window functions:

--> ROW_NUMBER( ) -> # of the current row

--> RANK( ) -> Order position of the current row

```sql
SELECT *, ROW_NUMBER() OVER () AS row_num
	FROM enrolled
```



### 2. OVER Keyword

The **OVER** keyword specifies how to group togther tuples when computing the window function.

Use **PATITION BY** to specify group. (also can use **ORDER BY**)

```sql
SELECT cid, sid, 
	ROW_NUMBER() OVER (PARTITION BY cid)
	FROM enrolled
	ORDER BY cid
```



Ex. Find the student with the second highest grade for each course.

```sql
SELECT * FROM (
	SELECT *, RANK() OVER (PARTITION BY cid
						ORDER BY grade ASC) AS rank
	FROM enrolled) AS ranking
	WHERE ranking.rank = 2
```



## J. Common Table Expressions

Alternative to nested queries and views.

```sql
WITH cteName (col1, col2) AS (
	SELECT 1, 2
)
SELECT col1 + col2 FROM cteName
```



Ex. Find student record with the highest id that is enrolled in at least one course.

```sql
WITH cteSource (maxId) AS (
	SELECT MAX(sid) FROM enrolled
)
SELECT name FROM student, cteSourse
	WHERE student.sid = cteSource.maxId
```



## K. CTE - Recursion

Ex. Print the sequence of numbers from 1 to 10

```sql
WITH RECURSIVE cteSourse (counter) AS (
	(SELECT 1)
	UNION ALL
	(SELECT counter + 1 FROM cteSource
		WHERE counter < 10)
)
SELECT * FROM cteSource
```













