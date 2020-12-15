# Partitioning data
* by range
* by list
* by hash

## Partition data by range

Create main table to keep data from IoT devices
```
CREATE TABLE iot_data(
    location_id int not null,
    measure_date date not null,
    temp_celcius int
)
PARTITION BY RANGE (measure_date)
```

Create partition by date range
```
CREATE TABLE iot_data_week1_2020 PARTITION OF iot_data
FOR VALUES FROM ('2020-12-01') TO ('2020-12-08');

CREATE TABLE iot_data_week2_2020 PARTITION OF iot_data
FOR VALUES FROM ('2020-12-09') TO ('2020-12-16');
```

## Partition data by list

Create table products
```
CREATE TABLE products(
    product_id int not null,
    product_name text not null,
    product_detail text not null,
    product_category varchar not null
)
PARTITION BY LIST (product_category);
```

Create partition by list of catagory
```
CREATE TABLE product_category_01 PARTITION OF products
FOR VALUES IN ('A', 'B', 'C');

CREATE TABLE product_category_02 PARTITION OF products
FOR VALUES IN ('D', 'E', 'F');
```

## Partition data by hash

Create table customer activity
```
CREATE TABLE customer_activities(
    customer_id int not null,
    url text not null,
    counter int not null,
    click_sequence int not null
)
PARTITION BY HASH (customer_id);
```

Create partition by hash
```
CREATE TABLE customer_activities_01 PARTITION OF customer_activities
FOR VALUES WITH ( MODULUS 3, REMAINDER 0 );

CREATE TABLE customer_activities_02 PARTITION OF customer_activities
FOR VALUES WITH ( MODULUS 3, REMAINDER 1 );

CREATE TABLE customer_activities_03 PARTITION OF customer_activities
FOR VALUES WITH ( MODULUS 3, REMAINDER 2 );
```