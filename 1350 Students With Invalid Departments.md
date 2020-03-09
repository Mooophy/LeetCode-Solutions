### 1350. Students With Invalid Departments
* `Sql`
* With `Join`:
```sql
select
    s.id as id,
    s.name as name
from
    Students as s left join Departments as d on s.department_id = d.id
where
    d.id is null
```
* With `Not In`
```sql
select
    s.id as id,
    s.name as name
from
    Students as s
where 
    s.department_id not in (select id from Departments)  
```
