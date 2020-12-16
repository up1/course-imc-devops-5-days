# Working with Indexes
* B-tree
* Bitmap
* Hash
* Specifics
  * GIN (Generalized INverted indexes)
  * BRIN (Block Range INdexes)
  * GiST (Generalized Search Tree)
  * SP-GiST (Space-Partitioned GiST)

## B-tree indexes
```
select * from staff WHERE email = 'jmurray3@gov.uk'

EXPLAIN ANALYZE select * from staff WHERE email = 'jmurray3@gov.uk'

CREATE INDEX idx_staff_email ON staff(email)

EXPLAIN ANALYZE select * from staff WHERE email = 'jmurray3@gov.uk'
```

## Bitmap indexes
```
select distinct job_title from staff 
select * from staff where job_title = 'Operator'

EXPLAIN ANALYZE select * from staff where job_title = 'Operator'

CREATE INDEX idx_staff_job_title ON staff(job_title)

EXPLAIN ANALYZE select * from staff where job_title = 'Operator'
```

## Hash indexes
```
CREATE INDEX idx_staff_email ON staff USING HASH (email)

EXPLAIN ANALYZE select * from staff WHERE email = 'jmurray3@gov.uk'
```
