---
layout : post
date : 2025-02-16
title : Learning nginx 
---

# Learning Nginx 

Nginx is a reverse proxy , that means is sits in front of the server and then its role is to redirect the traffic ( aka acts as a load balancer ) and hides the IP of the server 


## Setup and practices to perform 


Creates 2 directories 
```
mkdir -p /home/mohit/Desktop/mdesktop/reverse_proxy/sites-available
mkdir -p /home/mohit/Desktop/mdesktop/reverse_proxy/sites-enabled
```

sites-available : stores sites configurations
sites-enabled : contains symbolic link to configurations in sites-enabled


Now we need to add this in the nginx conf file as a directive..

Directive are the key values pairs in the nginx conf files like shown below:

```
include /home/mohit/Desktop/mdesktop/reverse_proxy/sites-enabled/*; 

include is the key
path is the value
These together are called directive 
```

Nginx configuration: 

```
server {
    listen 80;
    server_name mysite.local;

    location / {
        return 200 'Hello from your custom Nginx configuration!';
        add_header Content-Type text/plain;
    }
}
```

server : server block, that defines settings for a specific site 
listen 80 : tells nginx to listen on port 80 (HTTP)
server_name mysite.local : domain name this conf applies to  
location / { ... }: Begins a location block that handles requests for the root path (/) 
return 200 'Hello...';: Returns an HTTP 200 (OK) status with the specified text
add_header Content-Type text/plain;: Sets the Content-Type header to plain text


```
ln -s /home/mohit/Desktop/mdesktop/reverse_proxy/sites-available/mysite /home/mohit/Desktop/mdesktop/reverse_proxy/sites-enabled/
```

This creates a symbolic link to the configuration to the site ( CHECK : for location )  

```
chmod -R o+r /home/mohit/Desktop/mdesktop/reverse_proxy/
```


Then in the host file add the loopback IP address ( localhost ) to the domain name that we are assigning ( Sounds like DNS ?? ) 



Next steps : 

```
server {
    listen 80;
    server_name nodeapp.local;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

This sets up a reverse proxy for a node.js application running on port 3000 




## In More Depth:

Directives : key value pairs

```
proxy_pass  http://localhost:8000
```

```
events{

}
```
These are known as contexts, within context we have directive

## Writing a custom nginx file 

```
http{
  server{
    listen 8080;
    root /home/mohit/Desktop/mdesktop/reverse_proxy/
  }
}

events {}
```


Find the problem causing your nginx to not work : 
```
sudo journalctl -u nginx --no-pager --since "10 minutes ago"
```

Most common problem is access problem, u need to give access to all the parent folders and not just the final folder. 


## Mime Types

We need to tell nginx how to render which type of content .. that information is stored in mime types file and we just need to include it 

```
http  {
    include mime.types

    server {
        root /home/Desktop/<file-path>
        listen 8080;
    }

}

events {}
```

## Location blocks 


```
http  {
    include mime.types

    server {
        listen 8080;
        root /home/Desktop/<file-path>;

        location /fruits {
            root /home/Desktop/<file-path>; ( this auto adds /fruits at the end ) 

        }
    }

}

events {}
```

location /fruits : means this directory will only open when the endpoint is defined as in this case : http:localhost:8080/fruits 

using root : it appends the location defined in it at the end 
using alias : it doesnt append the location at the end so u can add at the end automatically 


By default, it looks for `index.html` files, so we can use try_files to try for these files also 

```
events {}

http { 

    include mime.types;
    
    server {
        listen 8080;
        root /home/mohit/Desktop/mdesktop/reverse_proxy;

        location /vegetable { 
            root /home/mohit/Desktop/mdesktop/reverse_proxy;
            try_files /vegetable/veggies.html /index.html =404; 

        }
    }
}
```

## nginx as a load balancer 

Lets say want to route it between 4 servers such that the time is saved per user .. 
what we can do is : 

create a dockerfile and expose the ports accordingly from it 

All the exposed ports becomes as a proxy_pass for a nginx file and we perform the routing from it !!

So what happens in a DIY home setup :

DNS routes the domain to IP 
Firewall passes that IP to the desired internal IP for which the port is exposed
The nginx should be running on that machine, and listening for requests on port 80 ( http ) or 443 ( https)

Once the request comes to that port , nginx then forwards that request to the internal IP's and (DOUBTFUL ON HOW?) get the data from there and sends back to the user ! 

[Nginx](https://www.xda-developers.com/how-to-set-up-nginx-reverse-proxies-in-your-home-lab/)

So we need a seperate dockerFile for frontend , a seperate docker file for backend and then nginx will need to be enabled from the frontend docker file and that will look for changes ( the init for nginx will be defined in the nginx.conf file !! )


nginx conf start -> looks for requests coming on port 80 











