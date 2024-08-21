[![Build status](https://ci.appveyor.com/api/projects/status/igmov1g7hb9n5n4i?svg=true)](https://ci.appveyor.com/project/nshabankin/qaa-hw-09-02)
# Integrating ReportPortal with Docker, JUnit5 and Selenide
With reference to [this guide](https://github.com/reportportal/agent-java-junit5#readme).
## Step 1.
Fetch, download or clone ReportPortal [`docker-compose.yml`](https://raw.githubusercontent.com/reportportal/reportportal/master/docker-compose.yml) to a local directory (preferably outside of your project directory).
## Step 2.
Update [`build.gradle`](https://github.com/nshabankin/qaa-hw-09-02/blob/51ec1340a7a0e1124d031f8935f09952854f1155/build.gradle) dependencies.
## Step 3.
Add [`com.epam.reportportal.junit5.extension.Extension`](https://github.com/nshabankin/qaa-hw-09-02/blob/51ec1340a7a0e1124d031f8935f09952854f1155/src/test/resources/META-INF/services/org.junit.jupiter.api.extension.Extension) to `./resources/META-INF/services`.
## Step 4.
Add [`log4j2.xml`](https://github.com/nshabankin/qaa-hw-09-02/blob/51ec1340a7a0e1124d031f8935f09952854f1155/src/test/resources/log4j2.xml) to `./resources/`.
## Step 5.
Add [`reportportal.properties`](https://github.com/nshabankin/qaa-hw-09-02/blob/51ec1340a7a0e1124d031f8935f09952854f1155/src/test/resources/reportportal.properties) containing your generated API key to `./resources/`.
## Step 6.
Add [`Logger`](https://github.com/nshabankin/qaa-hw-09-02/blob/51ec1340a7a0e1124d031f8935f09952854f1155/src/test/java/ru/netology/delivery/test/DeliveryTest.java#L37) object to the test class.
## Step 7.
Register tests with [`@ExtendWith(ReportPortalExtension.class`](https://github.com/nshabankin/qaa-hw-09-02/blob/51ec1340a7a0e1124d031f8935f09952854f1155/src/test/java/ru/netology/delivery/test/DeliveryTest.java#L40) annotation.
## Step 8.
Run `docker-compose up` command from the directory containing `docker-compose.yml` of ReportPortal.
## Step 9.
After the container is up, open ReportPortal via `localhost:8080` and login with default credentials.
## Step 10.
Create a new project and copy your generated API key to `reportportal.properties`.
## Step 11.
Run `java -jar ./artifacts/app-replan.jar` command in your project directory to run the app.
## Step 12.
Run `./gradlew clean build --refresh-dependencies` command in your project directory to build with tests.
## Step 13.
Go to `Launches` folder of ReportPortal and see the reports.
## Screenshots
`Launches` folder:
![image](https://github.com/user-attachments/assets/6e98d097-567a-42e1-876a-b70b48c88cc1)
Launch #2:
![image](https://github.com/user-attachments/assets/6df20f5f-b6e9-42f0-b5d1-bcd9cdfa8765)
Performed tests:
![image](https://github.com/user-attachments/assets/71926f17-5b6d-4d73-beb6-ae66221b2034)
Failed test logs and report:
![image](https://github.com/user-attachments/assets/56315857-362d-4ad4-a8fc-21295a252d72)
