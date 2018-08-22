Configuration OP5 Log Analytics and Windows SSO
==============================================

The configuration for AD has to be done in *`properties.yml`* file which can be found 
in *`src/main/resources`* directory in elasticsearch-auth plugin source code.

The various settings that needs to be done in this file are specified as below:




|**Direcitve**                                                    |**Description**                                    
|-----------------------------------------------------------------|---------------------------------------------------|
|ldap:								  |						      |
|name: "dev.example.com"                                          |# domain which is configured                       |
|host: "host1,host2"                                              |# list of servers for this domain                  |
|port: 389                                                        |# port for all the servers.                        |
|bind_dn: "Administrator@dev.example.com"                         |# admin username                                   | 
|bind_password: "Buspa#mexaj1"                                    |# admin password                                   |
|search_user_base_DN: "OU=lab,DC=dev,DC=it,DC=example,DC=com"     |# search user base root DN                         |
|user_id_attribute: "uid"                                         |# search user id attribute                         |
|search_groups_base_DN: "OU=lab,DC=dev,DC=it,DC=example,DC=com"   |# search group base DN. This is the root under which groups will be looked for.|
|unique_member_attribute: "uniqueMember"                          |# optional, default "uniqueMember"                 |
|connection_pool_size: 10                                         |# optional, default 30                             |
|connection_timeout_in_sec: 10                                    |# optional, default 1                              |
|request_timeout_in_sec: 10                                       |# optional, default 1                              |
|cache_ttl_in_sec: 60                                             |# optional, default 0 - cache disabled             |

If we want to configure multiple domain then same settings as mentioned above 
should be added in this file. The sample file in source dir have 2 domain configured 
so likewise we can add multiple domains.

Place this *`properties.yml`* file under config directory of elasticsearch installation.
After finish restart the Elasticsearch:\
*`systemctl restart elsticsearch`*


Configuring the SSL support for AD authentication in elasticsearch plugin. (Since version 2.3.6)
-------------------------------
1. Open the certificate manager where the AD server is installed:

![](/./media/media/image100.png)

2. Select the certificate and open it:

![](/./media/media/image101.png)

3. Select copy to file option in Details tab:

![](/./media/media/image102.png)

4.	Click on next:

![](/./media/media/image103.png)

5.	Keep the setting as shown below and proceed next:

![](/./media/media/image104.png)

6.	Keep the setting as shown below and proceed next:

![](/./media/media/image105.png)

7.	Give the name to certificate:

![](/./media/media/image106.png)

After the certificate is exported , this certificate should be imported in the trustsore 
that will be used by Elasticsearch plugin.

To import the certificate in the truststore there is utility called “keytool.exe” 
in JDK installation bin folder.

Use the command below to import it:\
*`keytool -import -alias adding_certificate_keystore  -file certificate.cer -keystore certificatestore`*

Values in RED should be changed as appropriate.

While doing this it will ask for setting a password for the trust store. 
Remember this password as this needs to be set in Elasticsearch plugin configuration.

Following settings should be set in Elasticsearch configuration for SSL:\
*`ssl.keystore.file: “<path to the trust store in above step>”`*\
*`ssl.keystore.password: "<password of the trust store in above step>"`*

	ldaps:
	    - name: "dev.example.pl"
	      host: "IP_address"
	      port: 389                                                 # optional, default 389
	      ssl_enabled: true                                         # set this property for enabling ssl for this domain
	      ssl_trust_all_certs: false                                 # set this property for truststore. If set to true then it will accept all the certificates else it will accept certificates only from the truststore.

Configuring Single Sign On (SSO) support (Since version 2.3.19)
---------------------------------------------------------------

**The very basic thing required for SSO is that the system should be accessible via domain url and not IP address or localhost. (SSO does not work for IP address/localhost)\
Like :\
http://dev.example.com:5601/login \
Not like :\
http://localhost:5601/login \
or\
http://IP_address:5601/login \**

SSO feature can be enabled/disabled using the following setting in *`kibana.yml`* file:\
*`kibana.sso_enabled: true`*

1.	Create an Account for Elasticsearch auth plugin:
In this step, a Kerberos Principal representing Elasticsearch auth plugin is created on the Active Directory.  The principal name would be something like name@REALM.NAME, while the REALM.NAME is the administrative name of the realm. In our case, the principal name will be esauth@DEV.EXAMPLE.COM. The account type should be "User", not a "Computer" in the AD.

Create User in AD, enter the details as shown below:

![](/./media/media/image106.png)

Make sure about the password options and encryption options as shown in the image.
Also note down the password that is set for this user and select password never expires option.

2.	Define Service Principal Name (SPN) and Create a Keytab file for it.
Use the following command to create the keytab file and SPN:\
    *C:> ktpass -out c:\Users\Administrator\\**esauth.keytab** -princ HTTP/**dev.example.com@DEV.EXAMPLE.COM** -mapUser **esauth** -mapOp set -pass **Sprint$123** -crypto ALL -pType KRB5_NT_PRINCIPAL

Values highlighted in bold can be changed. Domain specified should be for which SSO has to work.

3.	Create a file named *krb5Login.conf* with the following contents:

	      com.sun.security.jgss.initiate{
*com.sun.security.auth.module.Krb5LoginModule required principal="**esauth@DEV.EXAMPLE.COM**" useKeyTab=true keyTab=**C:\\Users\\Administrator\\Desktop\\esauth.keytab** storeKey=true debug=true;*
      };
    com.sun.security.jgss.krb5.accept {
com.sun.security.auth.module.Krb5LoginModule required principal="**esauth@DEV.EXAMPLE.COM**" useKeyTab=true keyTab=**C:\\Users\\Administrator\\Desktop\\esauth.keytab** storeKey=true debug=true;
                };
Content in bold should be changed as per the values created in the step 2. Make sure the domain should be in UPPERCASE as shown above.

4. Set the following JVM arguments:
-Dsun.security.krb5.debug=true -Djava.security.krb5.realm=**DEV.EXAMPLE.COM** -Djava.security.krb5.kdc=**IP_Address** -Djava.security.auth.login.config=**C:\\Users\\Administrator\\Desktop\\krb5Login.conf** -Djavax.security.auth.useSubjectCredsOnly=false

Change the appropriate value in the bold. This JVM arguments has to be set for Elasticsearch server. This also depends whether it is windows or unix system. This has to set before Elasticsearch server starts.

5. Add the following permission in java.policy file of the JDK/JRE installation:\
*`grant {`*\
  *`permission java.security.AllPermission;`*\
*`};`*

6. Add the following additional (highlighted in bold) settings for ldap in elasticsearch.yml or properties.yml file wherever the ldap settings are configured:

		**sso.domain: "dev.example.com"**
		ldaps:
		- name: "dev.example.com"
		host: "85.14.118.173"
		port: 389                                                 # optional, default 389
		ssl_enabled: false                                        # optional, default true
		ssl_trust_all_certs: false                                 # optional, default false
		bind_dn: "Administrator@dev.example.com"                     # optional, skip for anonymous bind
		bind_password: "Haslo@4321"                                 # optional, skip for anonymous bind
		search_user_base_DN: "OU=lab,DC=dev,DC=it,DC=example,DC=pl"
		user_id_attribute: "uid"                                  # optional, default "uid"
		search_groups_base_DN: "OU=lab,DC=dev,DC=it,DC=example,DC=pl"
		unique_member_attribute: "uniqueMember"                   # optional, default "uniqueMember"
		service_principal_name: "esauth@DEV.EXAMPLE.COM"
		service_principal_name_password : "Sprint$123"

Settings in bold are additional settings for SSO
Note: At this moment, SSO works for only single domain. So you have to mention for what domain SSO should work in the above property ‘sso.domain’

7. Client (Browser) Configuration for IE.
Goto Internet Options from Tools menu.
Click on Security Tab
