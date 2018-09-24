Logstash
========

The OP5 Log Analytics use Logstash service to dynamically unify data
from disparate sources and normalize the data into destynation of your
choise. A Logstash pipeline has two required elements, *input* and *output*,
and one optional elemnet *filter*. The input plugins consume data from a source, the filter plugins modify teh data as you specify, and the output plugins writethe data to a destynation.
The default location of the Logstash plugin files is: */etc/logstash/conf.d/*. This location contain following OP5 Log Analytics default plugins:

- `01-input-beats.conf`
- `01-input-syslog.conf`
- `020-filter-beats-syslog.conf`
- `020-filter-network.conf`
- `099-filter-geoip.conf`
- `100-output-elasticsearch.conf`
- `naemon_beat.example`
- `perflogs.example`
