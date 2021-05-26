# Game Play Analysis II

Table: `Activity`
```
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| player_id    | int     |
| device_id    | int     |
| event_date   | date    |
| games_played | int     |
+--------------+---------+
(player_id, event_date) is the primary key of this table.
This table shows the activity of players of some game.
Each row is a record of a player who logged in and played a number of games (possibly 0) before logging out on some day using some device.
``` 

Write a SQL query that reports the **device** that is **first logged** in for each player.

The query result format is in the following example:
```
Activity table:
+-----------+-----------+------------+--------------+
| player_id | device_id | event_date | games_played |
+-----------+-----------+------------+--------------+
| 1         | 2         | 2016-03-01 | 5            |
| 1         | 2         | 2016-05-02 | 6            |
| 2         | 3         | 2017-06-25 | 1            |
| 3         | 1         | 2016-03-02 | 0            |
| 3         | 4         | 2018-07-03 | 5            |
+-----------+-----------+------------+--------------+

Result table:
+-----------+-----------+
| player_id | device_id |
+-----------+-----------+
| 1         | 2         |
| 2         | 3         |
| 3         | 1         |
+-----------+-----------+
```

## My Solution 

1. Select and player and earliest login
2. Join with the original table to get `device_id`

```sql
SELECT B.player_id, A.device_id
FROM Activity A
INNER JOIN (
	SELECT player_id,MIN(event_date) AS min_event_date
	FROM Activity
	GROUP BY player_id) B
ON A.event_date = B.min_event_date AND A.player_id = B.player_id
```

## My Submission

