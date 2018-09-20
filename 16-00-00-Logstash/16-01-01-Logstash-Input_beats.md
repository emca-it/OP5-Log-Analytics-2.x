Logstash - Input "beats"
======================

This plugin wait for reciving data from remote beats services. It use tcp
/5044 port for communicaton:

                input {
                        beats {
                                port => 5044
                        }
                }
