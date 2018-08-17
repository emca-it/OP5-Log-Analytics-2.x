First configuration steps
=========================
To install and configure OP5 Log Analytics on the CentOS Linux system you should:

Optionally you can:
- configure integration with Active Directory and SSO servers. You can find necessary information in [12-00-00-Integration_with_AD](/./12-00-00-Integration_with_AD/12-00-00-Integration_with_AD.md) and [13-00-00-Windows-SSO](/./13-00-00-Windows-SSO/13-00-00-Windows-SSO.md);
- install and conigure monitoring with Marver:

	`cd /usr/share/elasticsearch`\
	`sudo bin/plugin install license`\
	`sudo bin/plugin install marvel-agent`\
	`systemctl restart elasticsearch`

- enable predictive funcionality in Intelligence module:

	`curl -XPOST 'http://localhost:9200/_aliases' -d '{`\
     		`"actions" : [`\
         	`{ "add" : { "index" : "intelligence", "alias" : "predictive" } },`\
        	 `{ "add" : { "index" : "op5-linux", "alias" : "predictive" } }`\
     		`]}'`
- enable dayily rotate alert and audit indexes:\

	`/bin/cp -rf /root/energy_logserver_stable/utils/index-rotation.sh /opt/alert/index-rotation.sh`\
	`crontab -e`\
	`@midnight /opt/alert/index-rotation.sh audit`\
	`@midnight /opt/alert/index-rotation.sh alert`
