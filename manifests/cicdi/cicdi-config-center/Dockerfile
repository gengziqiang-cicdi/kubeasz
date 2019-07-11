FROM 172.16.12.236/base/centos7-jdk8:201903
MAINTAINER geng.ziqiang
#copy war into image
ADD apigateway.jar /apigateway.jar
#expose port
EXPOSE 8080
EXPOSE 5005
EXPOSE 18082
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime
ENV LANG zh_CN.UTF-8
ENV JAVA_OPTS "-Dfile.encoding=UTF-8 -Xms256m -Xmx256m -Xdebug -Xrunjdwp:transport=dt_socket,server=y,suspend=n,address=5005 -Dcom.sun.management.jmxremote -Dcom.sun.ma
nagement.jmxremote.port=18082 -Dcom.sun.management.jmxremote.rmi.port=18082 -Dcom.sun.management.jmxremote.local.only=false -Dcom.sun.management.jmxremote.authenticate=
false -Dcom.sun.management.jmxremote.ssl=false -Djava.rmi.server.hostname=apigateway-remote-svc.platform"
ENV SPRING_OPTS "--eureka.client.serviceUrl.defaultZone=http://eureka-serverpeer1-svc.platform:8761/eureka/,http://eureka-serverpeer2-svc.platform:8761/eureka/,http://e
ureka-serverpeer3-svc.platform:8761/eureka/ --eureka.instance.hostname=apigateway-svc.platform --spring.cloud.stream.kafka.binder.brokers=172.16.12.37:9092,172.16.12.78
:9092,172.16.12.79:9092 --spring.cloud.stream.kafka.binder.zk-nodes=172.16.12.37:2181,172.16.12.78:2181,172.16.12.79:2181"
#define entry point which will be run first when the container starts up
ENTRYPOINT java $JAVA_OPTS -jar /apigateway.jar $SPRING_OPTS