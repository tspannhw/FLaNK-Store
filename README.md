# FLaNK-Store
Retail Grocery Store with MiNiFi, NiFi, Kafka, Flink, Kudu, Iceberg, Visualization



### NiFi Calcite SQL

````

SELECT brandname,category,countryorigin,'${date}' as itemdate,displayimage,
       images,item,itemId,itemdescription,itemheatsen,itemsize,longdescrption,
       msrp,originstore,cast(COALESCE(price, 0.00) as float) as price,
       productid,tmpind,tpr,ts,upc,uuid,updatedate
FROM FLOWFILE

````

### FLink SQL

````
select brandname, item, itemdescription, itemsize, price, category, updatedate, longdescrption, displayimage
from `sr1`.`default_database`.`item`

````

### References

* https://developer.kroger.com/documentation/api-products/public/products/tutorial
* https://github.com/tspannhw/retail-dynamic-shelf-pricing
