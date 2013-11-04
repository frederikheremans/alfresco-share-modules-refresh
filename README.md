About alfresco-share-modules-refresh
==============================

Artifacts to enable Alfresco Share to refresh deployed extension-modules, by calling a webscript.


Disclaimer
=============
This should **NOT** be used in production environments, intended for quick development time. Use this code at your own risk, the behaviour of the modules is not guaranteed
to work after the webscript is called. This is **NO** offcial Alfresco webscript.


Usage
=========
Adding the webscript to share should be done the same as with any other custom webscripts. To get started quick, you can find a 
simple guide to add the webscript, using the tomcat 'shared' folder.

1. Add the 'reload-modules.jar' file to the classpath of the Share-webapp (eg. WEB-INF/lib)
2. Make sure the 'shared' folder is added to the shared loader of your tomcat container (see http://wiki.alfresco.com/wiki/Install_Tomcat6, or alternatively, just use the real WEB-INF/classes folder)
3. Make sure the folder '$tomcat/shared/classes/alfresco/web-extension' exists.
4. Copy all files in 'share-artifacts' folder to the web-extensions folder.
5. Add (or modify if you already have one) the share-config-custom.xml file in the web-extensions folder and add the folowing line to the 'Web-Framework' config evaluator: ```<enable-dynamic-extension-modules>true</enable-dynamic-extension-modules>```.
6. Also, alter the module-deployment mode configuration in the same 'Web-Framework' config evaluator: 
```    <module-deployment>
       <mode>auto</mode>
       <enable-auto-deploy-modules>true</enable-auto-deploy-modules>
    </module-deployment>```
7. Start the share tomcat
8. Call http://localhost:8081/share/service/reload-module-deployments. A simple text-response should be returned, if the webscript is deployed successfuly.
