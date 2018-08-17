First configuration steps
=========================

To install and configure OP5 Log Analytics on the CentOS Linux system you should:
- set the hostname:\
	`hostnamectl set-hostname op5-log-analytics`
- set the corect time zone:\
	`/bin/rm -rf /etc/localtime`
	`ln -s /usr/share/zoneinfo/Europe/Warsaw /etc/localtime`
