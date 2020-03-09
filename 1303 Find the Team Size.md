### 1303. Find the Team Size
* `Sql`
* Group by, Subquery, 
```sql
select
    e.employee_id as employee_id,
    t.team_size as team_size 
from
    Employee as e 
    inner join(
    select
        team_id,
        count(team_id) as team_size
    from
        Employee 
    group by
        team_id
) as t 
    on e.team_id = t.team_id   
```
