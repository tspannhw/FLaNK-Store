# FLaNK-Store

Retail Grocery Store with MiNiFi, NiFi, Kafka, Flink, Kudu, Iceberg, Visualization

![FLANK](https://github.com/tspannhw/FLaNK-Store/blob/main/images/thefuturenificity4.jpg)


### We are ingesting data from Kroger

You will need to sign-up to get your credentials to get this cool data.

* https://developer.kroger.com/reference/#operation/productGet
* https://developer.kroger.com/documentation
* https://developer.kroger.com/documentation/public/getting-started/quick-start
* https://developer.kroger.com/documentation/api-products/public/products/overview

### Querying Kafka Topic for Items

![FLANK](https://github.com/tspannhw/FLaNK-Store/blob/main/images/ssbitems.jpg)

![FLANK](https://github.com/tspannhw/FLaNK-Store/blob/main/images/ssbitems2.jpg)

![SSB](https://github.com/tspannhw/FLaNK-Store/blob/main/images/smmitemvalue.jpg)


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
* https://github.com/tspannhw/FLaNK-AllTheStreams/tree/main/schemas
