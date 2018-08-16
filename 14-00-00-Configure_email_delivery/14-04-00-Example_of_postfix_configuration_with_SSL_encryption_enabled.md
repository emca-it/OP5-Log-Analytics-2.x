Example of postfix configuration with SSL encryption enabled
------------------------------------------------------------

This configuration is done on 4 postfix files:

1\.  The main.cf file should contain the following entries in addition to
  standard (unchecked entries):
  
  mydestination = \$myhostname, localhost.\$mydomain, localhost
  
  myhostname = example.com
  
  relayhost = \[smtp.example.com\]:587
  
  smtp\_sasl\_auth\_enable = yes
  
  smtp\_sasl\_password\_maps = hash:/etc/postfix/sasl\_passwd
  
  smtp\_sasl\_security\_options = noanonymous
  
  smtp\_tls\_CAfile = /root/certs/cacert.cer
  
  smtp\_use\_tls = yes
  
  smtp\_sasl\_mechanism\_filter = plain, login
  
  smtp\_sasl\_tls\_security\_options = noanonymous
  
  canonical\_maps = hash:/etc/postfix/canonical
  
  smtp\_generic\_maps = hash:/etc/postfix/generic
  
  smtpd\_recipient\_restrictions = permit\_sasl\_authenticated
 
3\. We define the data for authorized in the file 
  /etc/postfix/sasl\_passwd

  \[smtp.example.com\]:587
  [[USER\@example.com:PASS]{.underline}](mailto:USER@example.com:PASS)

4\. We give appropriate permissions

  chmod 400 /etc/postfix/sasl\_passwd

5\. We map 
  
  postmap /etc/postfix/sasl\_passwd

6\. We generate a cacert file

  cat /etc/ssl/certs/Example\_Server\_CA.pem \| tee -a
  /etc/postfix/cacert.pem

7\. Finally, we restart postfix

  /etc/init.d/postfix restart
