# nginucme reverse-proxy-container -p 8989:80 reverse-proxy-imageontainer-reverse-proxy
if you want to create a reserve proxy for docker containers 
 
# create Reverse-Proxy directory

   mkdir Reverse-Proxy

# create Dockerfile in the directory 

   wget https://raw.githubusercontent.com/zeineldin/nginx-container-reverse-proxy/master/README.md

# create default.conf 

   wget https://raw.githubusercontent.com/zeineldin/nginx-container-reverse-proxy/master/default.conf

# edit the default.conf and update the containers name and ports of app1 & app2

   vim default.conf

   server {
    listen       80;
    server_name  nginxserver;

    location /app1 {
         proxy_pass http://javaapp1-container:8888/devopsarea-1.0/;
    }

    location /app2 {
         proxy_pass http://javaapp2-container:8000/devopsarea-1.0/;
    }


    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }


# create docker image from the docker file

   docker build -t reverse-proxy-image .

# create docker container from created image

   docker run -d --name reverse-proxy-container -p 8989:80 reverse-proxy-image



<img width="790" alt="screen shot 2018-08-03 at 17 25 47" src="https://user-images.githubusercontent.com/20526165/43651626-2b8037d0-9743-11e8-9040-ffd1bd969f58.png">
