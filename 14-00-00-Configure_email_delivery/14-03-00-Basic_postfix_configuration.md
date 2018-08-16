Basic postfix configuration
---------------------------

This configuration is done in the main.cfg file which we complete with
the entry:

-  section \# RECEIVING MAIL

inet\_interfaces = all

inet\_protocols = ipv4

-  section \# INTERNET OR INTRANET

relayhost = \[IP mail server\]:25 (port number)

Then, we complete the canonical file as described in p. 11.1

At the end we restart the postfix

/etc/init.d/postfix restart
