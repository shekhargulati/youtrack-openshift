Quick install YouTrack to OpenShift
===================================

JetBrains offers a free license for its wonderful issue tracker called YouTrack, the responsive web design of YouTrack is enough to manage tasks from any device. Furthermore, RedHat and its fabulous product OpenShift offers free hosting for almost all main technologies, this solution is enough to manage tasks from anywhere (ok, anywhere with an internet connection). YouTrack is based on Java and OpenShift support Java, perfect solution was found.


How to install
--------------
If you don't have OpenShift account yet you can open it here https://openshift.redhat.com/app/account/new

Go to create Tomcat 7 application page https://openshift.redhat.com/app/console/application_type/cart!jbossews-2.0

Select name for your application, for example `youtrack`. It will be used in URL of your YouTrack instance. If you don't like it you can add your own domain (alias) later.

Click on the change Source Code link and set URL to this Git repository, i.e. https://github.com/stokito/youtrack-openshift.git

Click on Create Application button, and wait till YouTrack will deployed.

You should get to the created application page. At the top of this page should be link to your deployed YouTrack. Open it.

Now you need to wait first YouTrack run. It may take a lot of time and you may get 502 Proxy Timeout Error, but don't afraid and just refresh page once again.

If installation successful you will see basic YouTrack settings page.

If something went wrong just create a issue to this project with error messages.

YouTrack version
----------------
This repo contains YouTrack 5.0.
If you want to refresh version just fork this repo and replace `webapps/ROOT.war` with new downloaded YouTrack WAR file.
It can be downloaded from JetBrains site http://www.jetbrains.com/youtrack/download/get_youtrack.html (select JavaEE container version).

Please, don't forget to send a pull request.

Repo layout
-----------
`webapps/` - location for built war

`webapps/ROOT.war` - YouTrack WAR file

`.openshift/` - location for openshift specific files

`.openshift/action_hooks/deploy` - Deploy script - creates DB directories teamsysdata and teamsysdata-backup

`.openshift/action_hooks/pre_start_jbossews-1.0` - Script that gets run prior to starting EWS1.0 (Tomcat 6). Setup environment variables: PermGen size and YouTrack's DB dir path.

`.openshift/action_hooks/pre_start_jbossews-2.0` - Script that gets run prior to starting EWS2.0 (Tomcat 7). Setup environment variables: PermGen size and YouTrack's DB dir path.

Some helpful articles
---------------------
* [Cloudify YouTrack on OpenShift](http://www.codenibbles.com/blog/2012/07/16/cloudify-youtrack-on-openshift/)
* [YouTrack on OpenShift, quick and simple](http://toub.es/2013/07/15/youtrack-openshift-quick-and-simple)
* [In Russian: Как получить лучший трекер YouTrack бесплатно?](http://stokito.wordpress.com/2013/08/01/%d0%ba%d0%b0%d0%ba-%d0%bf%d0%be%d0%bb%d1%83%d1%87%d0%b8%d1%82%d1%8c-%d0%bb%d1%83%d1%87%d1%88%d0%b8%d0%b9-%d1%82%d1%80%d0%b5%d0%ba%d0%b5%d1%80-youtrack-%d0%b1%d0%b5%d1%81%d0%bf%d0%bb%d0%b0%d1%82%d0%bd/)
