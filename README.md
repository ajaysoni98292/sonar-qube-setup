#**Steps to setup Sonar qube in your project**

**Step 1** - Download the sonar from the [enter link description here][1]


**Step 2** - When downloading is completed then extract the zip file and copy the folder into the program files.

**Step 3** - Go to the folder-

>  C:\Program Files\sonarqube-5.0\conf 

and you see sonar.properties file.

**Step 4** - Now you see the sonar's properties in sonar.properties file. Uncomment the sonar.jdbc.url. Actually you have seen there are many sonar.jdbc.url are shown according to different different databases. Uncomment only sonar.jdbc.url which you want to use for saving the sonar related data.

![enter image description here][2] 


  [1]: http://www.sonarqube.org/downloads/
  [2]: http://i.stack.imgur.com/psKSp.jpg

In my case i am using the mysql database so i have given the sonar.jdbc.url is 

> sonar.jdbc.url=jdbc:mysql://localhost:3306/sonar?useUnicode=true&characterEncoding=utf8&rewriteBatchedStatements=true&useConfigs=maxPerformance

Step 5 - Now save the sonar.properties. Make sure no other changes you should do in this file.

Step 6 - Now you should open the setting.xml file for your maven project or you can write the properties in pom.xml file. You can choose any option. Difference is only that setting.xml is available to all the projects.

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

**Step 7** - Now you all the configurations are done. NO  
