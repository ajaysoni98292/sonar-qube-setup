#**Steps to setup Sonar qube in your project**

**Step 1** - Download the sonar from the [enter link description here][1]


**Step 2** - When downloading is completed then extract the zip file and copy the folder into the program files.

**Step 3** - Go to the folder-

>  C:\Program Files\sonarqube-5.0\conf 

and you see sonar.properties file.

**Step 4** - Now you see the sonar's properties in sonar.properties file. Uncomment the sonar.jdbc.url. Actually you have seen there are many sonar.jdbc.url are shown according to different different databases. Uncomment only sonar.jdbc.url which you want to use for saving the sonar related data.

![enter image description here][2]


In my case i am using the mysql database so i have given the sonar.jdbc.url is 

> sonar.jdbc.url=jdbc:mysql://localhost:3306/sonar?useUnicode=true&characterEncoding=utf8&rewriteBatchedStatements=true&useConfigs=maxPerformance

**Step 5** - Now save the sonar.properties. Make sure no other changes you should do in this file.

**Step 6** - Now you should open the setting.xml file for your maven project or you can write the properties in pom.xml file. You can choose any option. Difference is only that setting.xml is available to all the projects.

        <profiles>
        <profile>
            <id>sonar</id>
            <activation>
                <activeByDefault>true</activeByDefault>
            </activation>
            <properties>
                <sonar.jdbc.url>jdbc:mysql://localhost:3306/sonar</sonar.jdbc.url>
                <sonar.jdbc.driver>com.mysql.jdbc.Driver</sonar.jdbc.driver>
                <sonar.jdbc.username>sonar</sonar.jdbc.username>
                <sonar.jdbc.password>sonar</sonar.jdbc.password>
            </properties>
        </profile>
    </profiles>

Make sure you don't change the sonar username and password from the profile.
I already mentioned that this profile can be in pom.xml or can be in setting.xml.

**Step 7** - Now you all the configurations are done. NO other thins you to do in configuration. 

**Step 8** - Now you have to create a user with name sonar and password with sonar. so for this you have to open mysql and write some scripts as below

> 
C:\Windows\System32>mysql -uroot -pajay

> mysql> CREATE USER 'sonar'@'localhost' IDENTIFIED BY 'sonar';
>  
mysql> grant usage on *.* to sonar@localhost identified by 'sonar';

**Step - 9** Now go to the maven project and write the 

> mvn clean install -Psonar sonar:sonar

and hit the enter you see your project is successfully build. and open the link
 

> http://localhost:9000/ 

you see your  project listed in sonar qube 

 ![enter image description here][3]


  [1]: http://i.stack.imgur.com/knkRp.jpg
  [2]: http://i.stack.imgur.com/Ru7Im.jpg
  [3]: http://i.stack.imgur.com/knkRp.jpg
