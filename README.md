# FLaNK-Store

Retail Grocery Store with MiNiFi, NiFi, Kafka, Flink, Kudu, Iceberg, Visualization

![FLANK](https://github.com/tspannhw/FLaNK-Store/blob/main/images/thefuturenificity4.jpg)

In today's example, I need to ingest grocery items for some analytics, so let's read these via a secured REST API.    To follow along, you will
need to sign up for your own free key to see this interesting data.   Who doesn't want to ingest bananas with NiFi.


### We are ingesting data from Kroger

You will need to sign-up to get your credentials to get this cool data.

* https://developer.kroger.com/reference/#operation/productGet
* https://developer.kroger.com/documentation
* https://developer.kroger.com/documentation/public/getting-started/quick-start
* https://developer.kroger.com/documentation/api-products/public/products/overview


![shoppingunsplash](https://github.com/tspannhw/FLaNK-Store/blob/main/images/kenny-eliason-SvhXD3kPSTY-unsplash.jpg)

### Apache NiFi Flow

![nifi](https://github.com/tspannhw/FLaNK-Store/blob/main/images/nifioverview.jpg)

![nifi](https://github.com/tspannhw/FLaNK-Store/blob/main/images/livestoredata.jpg)

We have a few interesting flows for working with Retail data.   The First 

![nifi](https://github.com/tspannhw/FLaNK-Store/blob/main/images/nififlow1.jpg)

![nifi](https://github.com/tspannhw/FLaNK-Store/blob/main/images/nififlow1b.jpg)

![nifi](https://github.com/tspannhw/FLaNK-Store/blob/main/images/nififlow2.jpg)

![nifi](https://github.com/tspannhw/FLaNK-Store/blob/main/images/nifitokafka.jpg)


### Kafka Topics Shown in Streams Messaging Manager

![sMM](https://github.com/tspannhw/FLaNK-Store/blob/main/images/smmitems.jpg)

![kafka](https://github.com/tspannhw/FLaNK-Store/blob/main/images/kafkaitemdetail.jpg)

![smm](https://github.com/tspannhw/FLaNK-Store/blob/main/images/itemanditemimagesmm.jpg)


### Apache Kafka Item Image

![kafka](https://github.com/tspannhw/FLaNK-Store/blob/main/images/itemimagesmm.jpg)



### Querying Kafka Topic for Items

![FLANK](https://github.com/tspannhw/FLaNK-Store/blob/main/images/ssbitems.jpg)

![FLANK](https://github.com/tspannhw/FLaNK-Store/blob/main/images/ssbitems2.jpg)

![SSB](https://github.com/tspannhw/FLaNK-Store/blob/main/images/smmitemvalue.jpg)


![flink](https://github.com/tspannhw/FLaNK-Store/blob/main/images/flinkjob.jpg)




### NiFi Calcite SQL - To Transform and Enrich Item Price Stream

````

SELECT brandname,category,countryorigin,'${date}' as itemdate,displayimage,
       images,item,itemId,itemdescription,itemheatsen,itemsize,longdescrption,
       msrp,originstore,cast(COALESCE(price, 0.00) as float) as price,
       productid,tmpind,tpr,ts,upc,uuid,updatedate
FROM FLOWFILE

````

### Flink SQL to Browse Data

An example of querying Apache Kafka topics with Apache Flink SQL via Schema Registry catalog.

````
select brandname, item, itemdescription, itemsize, 
       price, category, 
       updatedate, longdescrption, displayimage
from `sr1`.`default_database`.`item`

````

![grocery](https://github.com/tspannhw/FLaNK-Store/blob/main/images/franki-chamaki-ivfp_yxZuYQ-unsplash.jpg)


### References

* https://developer.kroger.com/documentation/api-products/public/products/tutorial
* https://github.com/tspannhw/retail-dynamic-shelf-pricing
* https://github.com/tspannhw/FLaNK-AllTheStreams/tree/main/schemas
* https://developer.kroger.com/documentation/partner/getting-started/apis
* https://documenter.getpostman.com/view/4833726/TVReeWJm
* https://github.com/tspannhw/FLaNK-AllTheStreams
