# **CHANGELOG** #

# 2.1.17 #
## Added ##
- +Export Dashboard to PDF
## Changed ##
- bugfix dashboard generation using phantomjs
# 2.1.24 #
## Added ##
- +Report generation time added to the PDF
## Changed ##
- bugfix export Dashboard relative paths
- bugfix bigger dashboards
- bugfix relative path bug fix	
- bugfix Export to CSV
# 2.1.26 #
## Added ##
- +Kibana Reporting plugin
## Changed ##
- bugfix for report generation date on PDF
- bugfix elastalert auth jar 
- bugfix reports validation
# 2.1.27 #
## Added ##
- +Password Change function 
- +Deleting old CSV/PDF function

# 2.1.28 #
## Added ##
- +CSV Reports moved to reports tab
## Changed ##
- bugfix ES Auth Plugin Jar
- bugfix Kibana
- bugfix for scheduler index

# 2.1.29 #
## Added ##
- +Basic Auth function

# 2.1.30 #
## Changed ##
- bugfix From and To date on CSV CSV Task Export

# 2.1.31 #
## Changed ##
- bugfix auth-local-cookie.js change url to css file to relative
- bugfix fter submit command on 'export dashboard' page, Dashboard field shines in red
- bugfix server should not allow GET (even if user manually change request) server side verification
- bugfix In Export Task Managment tab use Search query "*" i Time Criteria Field Name as  "@timestamp" by default

# 2.1.32 #
## Added ##
- +Introduction of CSRF Tokens for each action. The CSRF Token can be generated once at login and appended to all GET / POST actions.

# 2.1.33 #
## Added ##
- +Changing your password require you to enter your current password.
- +Password change form require you to enter a new password twice.
- +Cookies new flags: expires, secure, domain.
## Changed ##
- bugfix Password Change function

# 2.1.34 #
## Added ##
- + Auto create user elastalert by kibana with random password (like logserver user)
- + Change Admin tab to Config
- + Deleting a user or role should require confirmation that the user is sure about this action.
## Changed ##
- bugfix: Marvel plugin problem with auth plugin enabled.
- bugfix: Public directory https://127.0.0.0.1:5601/bundles/ 

# 2.1.35 #
## Added ##
- + In audit.log should not appear _bulk (default off)
- + In audit.log should not appear password update/create request.
- + In audit.log query output on/off (default on)
- + Userlist and Rolelist alphabeticaly
- + Add username in Password change page info about role on change page
 
# 2.1.37 #
## Added ##
- + Non logged user which clicks on the link to the dashboard is redirected to the login page, and after successfully logging user is redirected to Discovery section rnot to the dashboard from the link

# 2.2.1 #
## Added ##

- + Introduction to Licensing module
# 2.2.2 #
## Added ##

- + Licensing module 

# 2.2.3 #
## Added ##

- + Code Documentation
## Changed ##

- bugfix: in User/Role Update

# 2.3.0 #
## Added ##
- + Object Management Elastafilter (kibana)
- + Active Directory AD Integration (elasticsearch-auth)
## Changed ##
- bugfix: in Alerts module (kibana)

# 2.3.3 #
## Added ##
- + AD config moved to elasticsearch.yml (elasticsearch-auth)
## Changed ##

- bugfix: Dashboards elastafilter (kibana)

# 2.3.4 #
## Added ##
- + In Config-> settings: Miliseconds to seconds change
- + Ldap/AD auth as optional
## Changed ##
- bugfix Userlist problem no roles selected after Update action
- bugfix elasticsearch logging 

# 2.3.5 #
## Added ##
- + Timepicker on task export changed from 2015-05-19 to 2018-01-01*
- + Object permission selector set/unset all
- + Java jdk1.8.0_161 added to git
- + Phantomjs added as kibana dependency
- + Marvel added to git
## Changed ##
- bugfix: If admin create role with /* pattern causes elasticsearch and kibana (no connection to elasticsearch) crash in loop....
- bugfix: Default config settings with elastafilter problem with timeout 0/token expire etc
- bugfix: In Alert -> Flatline bad example
- bugfix: In Alert -> Alert writeback index based on the configuration file.

# 2.3.6 #
## Added ##
- + LDAP/AD SSL Support
- + Title and Logos change to Logserver
## Changed ##
- bugfix: no Rules directory for alert
- bugfix: Example LDAP settings change

# 2.3.7 #
## Added ##
- + Logserver/Energy tab changed to Search tab in Kibana
- + Show license details in Kibana
- + Added default system settings for services [sysctl,limits.d]
- + Java dir changed => jdk-1.8.0_161.tar.bz2
- + New default users: logserver, alert, scheduler, intelligence 
## Changed ##
- bugfix: Exception in thread "Timer-1"
- bugfix: Default elastalert password changed

# 2.3.8 #
## Added ##
- + Intelligence plugin
- + Schedule plugin
- + Added kibana/elasticsearch PayLoad settings to config files.
## Changed ##
- bugfix: All shards failed in Discovery Tab => (elastafilter limits)
- bugfix: LDAP settings format

# 2.3.9 #
## Added ##
- + Intelligence plugin upgrade
- + Schedule plugin upgrade
- + Alerts upgrade
- + Java upgrade to 1.8_171
- + Added index-rotation.sh script for audit & alert index
## Changed ##
- bugfix: All shards failed in Discovery Tab => (elastafilter limits)
- bugfix: Max clause limit => 10240

# 2.4.0 #
## Added ##
- + Preview & Status in Intelligence section
- + Role-Mapping for AD
- + Default Users Role
- + Added scripts\ldap-alias-create.sh for AD User Alias
- + Example Alert Dashboard
## Changed ##
- bugfix: Intelligence Trend

# 2.4.1 #
## Changed ##
- bugfixes: Intelligence Scheduler Login Filter
- bugfixes: elasticsearch-auth plugin

# 2.4.2 #
## Added ##
- + Timelion
- + More detailed logs Kibana
- + More detailed logs Intelligence
- + PDF/CSV reports for AD users
- + Alerts preview for Users
- + New Alert SAVE button
## Changed ##
- bugfix: audit index: @timestamp
- bugfix: Intelligence Trend Threshold fix
- bugfix: Intelligence (SPARK_LOCAL_IP)
- bugfix: Mangement typo in Reports
- bugfix: Objects import
- bugfix: Recovery Alert Dashboard fix
- bugfix: Password update/change disabled for AD users

# 2.4.3 #
## Added ##
- + Kibana role for GUI users
- + Alert role for Alert Module users
- + Intelligence role for A/I Module users
- + Intelligence temporary directory
- + Intelligence Preview update

# 2.4.4 #
## Added ##
- + SSO single sign on implementation
- + Improved installation process
- + OpenJDK Support
- + Removed all unnecessary dependencies
- + Removed python libraries (pip)
- + Logstash configuration examples
- + OVF changed to OVA
## Changed ##
- bugfix: Conflict during system upgrade (yum update)
- bugfix: journald.conf conflict
- bugfix: Defaultrole AD users
- bugfix: start_date Intelligence module

# 2.4.5 #
## Added ##
- + New Login Page with SSO support
- + Alert module update
## Changed ##
- bugfix: metric_aggregation, new term, percentage_match

