### 1068. Product Sales Analysis I
* Sql
```sql
select
    p.product_name as product_name,
    s.year as year,
    s.price as price
from
    Sales as s inner join Product as p on s.product_id = p.product_id
```
