
# Load balancing exercise

In this exercise, you will increase the load-handling capacity of a sample application by running multiple instances and distributing incoming requests between them using an API Gateway configured for load balancing.

In this repository, you will find a Node.js application that exposes an endpoint returning the port of the running instance. This allows you to see which instance is responding to each request.

The repository also includes a configuration file for the API Gateway. You will use NGINX, a popular web server/reverse proxy that can serve static files, forward requests to backend servers, and load balance traffic, which is the focus of this exercise.

## API Gateway

To run the API Gateway, you first need to complete the configuration file by adding the addresses of the running Node.js application instances. Once the addresses are added, you can start the API Gateway:

1. Install NGINX:

On mac via Homebrew:
```
brew install nginx
```
On windows: https://nginx.org/en/docs/windows.html

2. Start NGINX using the custom config file:
```
sudo nginx -c /your/path/load-balancing-exercise/load-balancing-exercise/api-gateway-nginx.conf
```
Now the API Gateway should be listening in `localhost:8080`.

Make sure when you refresh the page multiple times you get different port numbers, that means the requests are being distributed across the different instances of the application.

To stop the API Gateway:
```
sudo nginx -s stop 
```

