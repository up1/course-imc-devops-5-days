# Tuning Joins
* Inner join
* Left outer join
* Right outer join
* Full outer join

## Nested loops
```
SELECT 
    s.id, s.last_name, s.job_title, cr.country
FROM
    staff s
INNER JOIN
    company_regions cr
ON
    s.region_id = cr.region_id
```

Explain and analyze
```
EXPLAIN ANALYZE SELECT 
    s.id, s.last_name, s.job_title, cr.country
FROM
    staff s
INNER JOIN
    company_regions cr
ON
    s.region_id = cr.region_id
```

Enable nestloop
```
set enable_nestloop=true;
set enable_hashjoin=false;
set enable_mergejoin=false;

EXPLAIN ANALYZE SELECT 
    s.id, s.last_name, s.job_title, cr.country
FROM
    staff s
INNER JOIN
    company_regions cr
ON
    s.region_id = cr.region_id
```

Create indexs
```
CREATE INDEX idx_staff_region_id ON staff(region_id)
```

## Hash joins
```
set enable_nestloop=false;
set enable_hashjoin=true;
set enable_mergejoin=false;

EXPLAIN ANALYZE SELECT 
    s.id, s.last_name, s.job_title, cr.country
FROM
    staff s
INNER JOIN
    company_regions cr
ON
    s.region_id = cr.region_id
```

## Merge joins
```
set enable_nestloop=false;
set enable_hashjoin=false;
set enable_mergejoin=true;

EXPLAIN ANALYZE SELECT 
    s.id, s.last_name, s.job_title, cr.country
FROM
    staff s
INNER JOIN
    company_regions cr
ON
    s.region_id = cr.region_id
```


