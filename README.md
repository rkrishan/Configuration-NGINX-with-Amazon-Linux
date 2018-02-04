configure nginx with node on Amazon Linux

sudo yum update
sudo yum install nginx
make sure that nginx is start when start the system
command for that   (sudo chkconfig --level 345 nginx on)
Install nodeJs     
curl -sL https://rpm.nodesource.com/setup | bash -(if not work then put sudo before bash)
now install pm2 which run the nodejs continously
npm install pm2 -g --unsafe-perm
For starting the server use (pm2 start server.js)
Now let’s add the proxy info to nginx for that use 
Edit that file by using vim ,(vim edit /etc/nginx/nginx.conf) if not work put sudo before vim 
Add port number on which you want to run your application by default run on port number 8080 you can change according to you (e.g proxy_pass http://localhost:8080;)
Then restart the nginx by using (sudo service nginx restart)        
Also can below link can be follow (https://theglassicon.com/computing/web-servers/install-nginx-amazon-linux-ami/)
And also (http://thomasmullaly.com/2014/11/02/node-dot-js-and-nginx-on-an-amazon-linux-ec2-instance/)
if the above file server portion is not working then edit the portion(/usr/local/nginx/conf/nginx.conf) file and change the server portion of that file ,it will work
I have changes nginx.conf file and change the server Portion of the the file.open that file in place. 
Server_portion : IP Address of the Machine (I have put here automation.elucidata.io whcih is link to particular IP address )
In location portion put your (proxy_pass http://localhost:3000;) 3000 is the node running on the port number.
