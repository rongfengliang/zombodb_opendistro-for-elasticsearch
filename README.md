# zombodb+opendistro-for-elasticsearch

## Some Notes

* default es user account

```code
admin amdin
```

* zombodb connect es config

```code
  CREATE EXTENSION zombodb;
  CREATE TABLE products (
    id SERIAL8 NOT NULL PRIMARY KEY,
    name text NOT NULL,
    keywords varchar(64)[],
    short_summary text,
    long_description zdb.fulltext, 
    price bigint,
    inventory_count integer,
    discontinued boolean default false,
    availability_date date
);

CREATE INDEX idxproducts 
                     ON products 
                  USING zombodb ((products.*))
                   WITH (url='http://admin:admin@elasticsearch:9200/');
SELECT * FROM products WHERE products ==> 'sports box';

```