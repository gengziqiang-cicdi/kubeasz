FROM 172.16.12.236/base/centos7-nginx:201903
MAINTAINER geng.ziqiang
#copy war into image
COPY dist/ /usr/share/nginx/html
RUN chown -R nginx:nginx  /usr/share/nginx/html