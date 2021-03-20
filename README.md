
##Steps: 
1. Install Websphere Liberty Core.
2. go to [WLC HOME]/bin and run
    ```shell
       $server create micro-one
       $server create micro-two
    ```
3. Go to to [WLC HOME]/usr/servers/micro-one and open server.xml and add 
   ```xml
        <featureManager>
            <feature>springBoot-2.0</feature>
            <feature>servlet-3.1</feature>
        </featureManager>
    ```
4. go to [WLC HOME]/bin and run
    ```shell
    $springBootUtility install servlet-3.1
    $springBootUtility install springBoot-2.0
    ```
5. Go to to [WLC HOME]/usr/servers/micro-one and open server.xml and add
   ```xml
        <webContainer deferServletLoad="false"/>
    
        <springBootApplication location="micro-one.jar">
            <applicationArgument>--server.context-path=/mc1</applicationArgument>
        </springBootApplication>
    ```
6. go to [WLC HOME]/bin and to start the microservices run
    ```shell
       $server run micro-one
       $server run micro-two
    ```
7. go to [WLC HOME]/bin and to stop the microservices run  
    ```shell
       $server stop micro-one
       $server stop micro-two
    ```
8. Logs generated by the each microservices will be in  [WLC HOME]/usr/servers/micro-one/logs/messages.log


### Some URLS  referenced: 
> https://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/twlp_dep_springboot.html
>
>https://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/twlp_dep_sb_apparguments.html
>
>https://www.ibm.com/support/knowledgecenter/SSD28V_liberty/com.ibm.websphere.wlp.core.doc/ae/rwlp_springboot.html
>https://www.ibm.com/support/knowledgecenter/SSD28V_liberty/com.ibm.websphere.wlp.core.doc/ae/twlp_config_servlet31.html
>
>https://github.com/WASdev/sample.SpringBootMVC
>http://www.adeveloperdiary.com/java/spring-boot/deploy-spring-boot-application-ibm-liberty-8-5/
