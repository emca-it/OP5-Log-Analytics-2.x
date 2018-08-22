Mapping, Fielddata and Templates
===============================

Mapping is a collection of fields along with a specific data type
Fielddata is the field in which the data is stored (requires a specific type - string, float)
Template is a template based on which fielddata will be created in a given index.

- Information on all set mappings:\
*`# curl -XGET '127.0.0.1:9200/_mapping?pretty=true'`*

- Information about all mappings set in the index:\
*`# curl -XGET '127.0.0.1:9200/twitter/_mapping/*?pretty=true'`*

- Information about the type of a specific field:\
*`# curl -XGET '127.0.0.1:9200/twitter/_mapping/field/message*?pretty=true'`*

- Information on all set templates:\
*`# curl  -XGET '127.0.0.1:9200/_template/*?pretty=true'`*

- Create - Mapping / Fielddata - It creates index twitter-float and the tweet message field sets to float:\
*`# curl -XPUT '127.0.0.1:9200/twitter-float?pretty=true' -d '{`*\
  *`"mappings": {`*\
    *`"tweet": {`*\
      *`"properties": {`*\
        *`"message": {`*\
          *`"type": "float"`*\
        *`}`*\
      *`}`*\
    *`}`*\
  *`}`*\
*`}'`*

*`# curl -XGET '127.0.0.1:9200/twitter-float/_mapping/field/message?pretty=true'`*

- Create Template:\
*`# curl -XPUT '127.0.0.1:9200/_template/template_1' -d'{`*\
    *`"template" : "twitter4",`*\
    *`"order" : 0,`*\
    *`"settings" : {`*\
        *`"number_of_shards" : 2`*\
    *`}`*\
*`}'`*

*`# curl -XPOST '127.0.0.1:9200/twitter4/tweet?pretty=true' -d'{`*\
*`"user" : "lab1",`*\
*`"post_date" : "2017-08-25T10:10:00",`*\
*`"message" : "testuje automatyczne generowanie ID"`*\
*`}'`*

*`# curl -XGET '127.0.0.1:9200/twitter4/_settings?pretty=true'`*

– Create Template2 - Sets the mapping template for all new indexes specifying that the tweet data, in the 
field called message, should be of the "string" type:\

*`# curl -XPUT '127.0.0.1:9200/_template/template_2' -d'{`*\
  *`"template" : "*",`*\
  *`"mappings": {`*\
    *`"tweet": {`*\
      *`"properties": {`*\
        *`"message": {`*\
          *`"type": "string"`*\
        *`}`*\
      *`}`*\
    *`}`*\
  *`}`*\
*`}'`*


- Delete Mapping - Deleting a specific index mapping (no possibility to delete - you need to index):\
*`# curl -XDELETE '127.0.0.1:9200/twitter2'`*

- Delete Template:\
*`# curl  -XDELETE '127.0.0.1:9200/_template/template_1?pretty=true'`*
