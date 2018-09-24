Verificatoin of OP5 Log Analytics GUI service
=====================================

To verify of OP5 Log Analytics GUI service you can use following command:

- control the OP5 Log Analytics GUI service via **systemd**:

		`# systemctl status kibana`

output:

	`kibana.service - no description given`
	   `Loaded: loaded (/usr/lib/systemd/system/kibana.service; enabled; vendor preset: disabled)`
	   `Active: active (running) since Fri 2017-09-01 10:39:46 CEST; 2 days ago`
	   `Main PID: 8527 (node)`
	   `CGroup: /system.slice/kibana.service`
	           `└─8527 /opt/kibana/bin/../node/bin/node /opt/kibana/bin/../src/cl`

- control the OP5 Log Analytics GUI via **port tcp**:

		`# curl -XGET '127.0.0.1:5601/'`

output:

	  `<script>var hashRoute = '/app/kibana';`
	  `var defaultRoute = '/app/kibana';`
	  `var hash = window.location.hash;`
	  `if (hash.length) {`
	  `  window.location = hashRoute + hash;`
	  `} else {`
	  `  window.location = defaultRoute;`
	  `}</script>`

- Control the OP5 Log Analytics GUI via **log file**:

		`# tail -f /var/log/messages`
