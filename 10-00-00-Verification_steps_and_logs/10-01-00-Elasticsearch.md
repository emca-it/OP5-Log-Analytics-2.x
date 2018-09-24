
Verification of Elasticsearch service
=====================================

To verify of Elasticsearch service you can use following command:

- Control of the Elastisearch system service via **systemd**:
`# sysetmctl status elasticsearch`
  output:

		`elasticsearch.service - Elasticsearch`
		`Loaded: loaded (/usr/lib/systemd/system/elasticsearch.service; enabled; vendor preset: disabled)`
		`Active: active (running) since Fri 2017-09-01 10:36:52 CEST; 3h 7min ago`
		 `Docs: http://www.elastic.co`
		`Main PID: 8362 (java)`
		`CGroup: /system.slice/elasticsearch.service`
		       `└─8362 /bin/java -Xms256m -Xmx1g -Djava.awt.headless=true`

- Control of Elasticsearch instance via **tcp port**:
  
`# curl -XGET '127.0.0.1:9200/'`

  output:

	`{`
	`  "name" : "Henry Peter Gyrich",`
	 ` "cluster_name" : "elasticsearch",`
	  `"version" : {`
	   ` "number" : "2.3.5",`
	    `"build_hash" : "90f439ff60a3c0f497f91663701e64ccd01edbb4",`
	    `"build_timestamp" : "2016-07-27T10:36:52Z",`
	    `"build_snapshot" : false,`
	    `"lucene_version" : "5.5.0"`
	  `},`
	  `"tagline" : "You Know, for Search"`
	`}`
 
- Control of Elasticsearch instance via **log file**:

	`# tail -f /var/log/elasticsearch/elasticsearch.log`

- other control commands via ***curl* application**:

		`curl -xGET "http://localhost:9200/_cat/health?v"`
		`curl -XGET "http://localhost:9200/_cat/nodes?v"`
		`curl -XGET "http://localhost:9200/_cat/indicates"`
