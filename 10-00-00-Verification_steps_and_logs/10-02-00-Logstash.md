Verificatoin of Logstash service
=====================================
To verify of Logstash service you can use following command:
- control Logstash service via **systemd**:\
`# systemctl status logstash`\
output:\
`logstash.service - logstash`\
   `Loaded: loaded (/etc/systemd/system/logstash.service; enabled; vendor preset: disabled)`\
   `Active: active (running) since Wed 2017-07-12 10:30:55 CEST; 1 months 23 days ago`\
 `Main PID: 87818 (java)`\
   `CGroup: /system.slice/logstash.service`\
          `└─87818 /usr/bin/java -XX:+UseParNewGC -XX:+UseConcMarkSweepGC`
- control Logstash service via **port tcp**:\
`# curl -XGET '127.0.0.1:9600'`\
output:
`{`\
   `"host": "skywalker",`\
   `"version": "4.5.3",`\
   `"http_address": "127.0.0.1:9600"`\
`}`
- control Logstash service via **log file**:\
`# tail -f /var/log/logstash/logstash-plain.log`
