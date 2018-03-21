FROM 	maven:3.5-jdk-8 as dependencies

ARG 	build_artefact=wcn-data-fed-0.0.1-SNAPSHOT.jar

COPY 	pom.xml /usr/src/myapp/pom.xml

RUN 	mvn -f /usr/src/myapp/pom.xml clean verify --fail-never

FROM 	maven:3.5-jdk-8 as build
COPY 	--from=dependencies /root/.m2 /root/.m2

COPY  . /usr/src/myapp

RUN 	cat /usr/src/myapp/pom.xml && ls -ls /usr/src/myapp &&  mvn -f /usr/src/myapp/pom.xml clean package

FROM 	openjdk:8u151-jre-alpine3.7

COPY 	--from=build /usr/src/myapp/target/${build_artefact} /${build_artefact}

ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/./urandom","-jar","/wcn-data-fed-0.0.1-SNAPSHOT.jar", \
            "--spring.wcndatafeed.oauth.client=${RPG_WCN_DATA_CLIENT}", \
            "--spring.wcndatafeed.oauth.secret=${RPG_WCN_DATA_SECRET}", \
            "--spring.wcndatafeed.oauth.user=${RPG_WCN_DATA_USER}", \
            "--spring.wcndatafeed.oauth.password=${RPG_WCN_DATA_PASSWORD}"]
