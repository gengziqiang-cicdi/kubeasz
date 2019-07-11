FROM 172.16.12.236/base/centos7-jdk8-kubectl:201903
MAINTAINER geng.ziqiang
#copy war into image
ADD cicdi-rdplatform.jar /cicdi-rdplatform.jar
#expose port
EXPOSE 8080
EXPOSE 5005
EXPOSE 18082
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime
ENV LANG zh_CN.UTF-8
ENV JAVA_OPTS "-Dfile.encoding=UTF-8 -Xms256m -Xmx256m -Xdebug -Xrunjdwp:transport=dt_socket,server=y,suspend=n,address=5005 -Dcom.sun.management.jmxremote -Dcom.sun.ma
nagement.jmxremote.port=18082 -Dcom.sun.management.jmxremote.rmi.port=18082 -Dcom.sun.management.jmxremote.local.only=false -Dcom.sun.management.jmxremote.authenticate=
false -Dcom.sun.management.jmxremote.ssl=false -Djava.rmi.server.hostname=cicdi-rdpplatform-remote-svc.platform"
#define entry point which will be run first when the container starts up
ENTRYPOINT java $JAVA_OPTS -jar /cicdi-rdplatform.jar