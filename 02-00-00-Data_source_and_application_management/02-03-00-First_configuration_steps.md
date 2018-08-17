First configuration steps
=========================

To install and configure OP5 Log Analytics on the CentOS Linux system you should:
- set the hostname:\
	`hostnamectl set-hostname op5-log-analytics`
- set the corect time zone:\
	`/bin/rm -rf /etc/localtime`\
	`ln -s /usr/share/zoneinfo/Europe/Warsaw /etc/localtime`
- set the firewall:
	`systemctl enable firewalld && systemctl start firewalld`\
	`firewall-cmd --zone=public --add-port=22/tcp --permanent`\
	`firewall-cmd --zone=public --add-port=5601/tcp --permanent`\
	`firewall-cmd --zone=public --add-port=9200/tcp --permanent`\
	`firewall-cmd --zone=public --add-port=9300/tcp --permanent`\
- enable additional yum repository:
	` yum install -y epel-release`
- update base system:
	` yum update -y`
- install the required packages from the yum repository:
	`yum -y install openssh openssh-server openssh-clients openssl-libs htop iotop vim dstat lsof tar wget nc psmisc ntpdate git python-pip python-devel telnet libffi-devel openssl-devel curl mc htop liberation-sans-fonts xorg-x11-xauth.x86_64 unzip bzip2 whois bind-utils fontconfig freetype freetype-devel fontconfig-devel libstdc++ urw-fonts mailx cyrus-sasl cyrus-sasl-gssapi cyrus-sasl-ntlm cyrus-sasl-plain libgsasl gcc npm`
