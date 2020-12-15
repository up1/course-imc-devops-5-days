# Explain and analyze with PostgreSQL

Start with basic query

```
EXPLAIN select * from staff;

EXPLAIN ANALYZE select * from staff;

EXPLAIN ANALYZE select lastname from staff
```

## Working with WHERE conditions

```
EXPLAIN select * from staff WHERE salary > 75000;

EXPLAIN ANALYZE select * from staff WHERE salary > 75000;
```

Improve execute time with indexes
```
CREATE INDEX idx_staff_salary ON staff(salary);

EXPLAIN ANALYZE select * from staff WHERE salary > 75000;
```
