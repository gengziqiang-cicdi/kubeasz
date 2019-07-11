FROM 172.16.12.203/base/centos7.4-base-jdk18
MAINTAINER geng.ziqiang
#copy war into image
ADD eureka-1.0.jar /eureka-1.0.jar
#expose port
EXPOSE 8761
ENV LANG zh_CN.GBK
ENV JAVA_OPTS "-Dfile.encoding=GBK -Xms512m -Xmx512m "
ENV SPRING_OPTS --eureka.client.serviceUrl.defaultZone=http://eureka-serverpeer1-svc.platform:8761/eureka/,http://eureka-serverpeer3-svc.platform:8761/eureka/ --eureka.
instance.hostname=eureka-serverpeer2-svc.platform
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime
#define entry point which will be run first when the container starts up
ENTRYPOINT java $JAVA_OPTS -jar /eureka-1.0.jar $SPRING_OPTS