Where does the data come from?
==============================

OP5 Log Analytics is a solution enabling effective data processing
from the IT environment that exists in the organization.

The Elsasticsearch engine allows building a database in witch large
amounts of data are stored in ordered indexes. The Logstash module is
responsible for load data into Indexes, whose function is to collect
data on specific tcp/udp ports, filter them, normalize them and place
them in the appropriate index. Additional plugins, that we can use in
Logstash reinforce the work of the module, increase its efficiency,
enabling the module to quick interpret data and parse it.

Below is an example of several of the many available Logstash plugins:

**exec** -- receive output of the shell function as an event;

**imap** -- read email from IMAP servers;

**jdbc** -- create events based on JDC data;

**jms** -- create events from Jms broker;

Both Elasticsearch and Logstash are free Open-Source solutions.

More information about Elasticsearch module can be find at:\
https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started.html

Detailed information about Logstash engine:\
https://www.elastic.co/guide/en/logstash/current/introduction.html

List of available Logstash plugins:\
https://www.elastic.co/guide/en/logstash/current/input-plugins.html