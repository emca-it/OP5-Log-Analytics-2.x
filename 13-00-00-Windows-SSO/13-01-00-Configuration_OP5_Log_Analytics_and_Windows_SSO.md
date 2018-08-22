Configuration OP5 Log Analytics and Windows SSO
==============================================

The configuration for AD has to be done in *`properties.yml`* file which can be found 
in *`src/main/resources`* directory in elasticsearch-auth plugin source code.

The various settings that needs to be done in this file are specified as below:

|**Direcitve**                                                    |**Description**                                    
|-----------------------------------------------------------------|---------------------------------------------------
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

Place this *`properties.yml`* file under config directory of elasticsearch installation.\
After finish restart the Elasticsearch:
*`systemctl restart elsticsearch`*


Configuring the SSL support for AD authentication in elasticsearch plugin. (Since version 2.3.6)
-------------------------------
1. Open the certificate manager where the AD server is installed:\
![](/./media/media/image100.png)

