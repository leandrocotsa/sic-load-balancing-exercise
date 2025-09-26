
# Load balancing exercise

<p align="center">
  <img src="https://raw.githubusercontent.com/leandrocotsa/sic-load-balancing-exercise/refs/heads/main/readme-assets/load-balancing-diagram.jpg" width="600" />
</p>

In this exercise, you will increase the load-handling capacity of a sample application by running multiple instances and distributing incoming requests between them using an API Gateway configured for load balancing.

In this repository, you will find a Node.js application that exposes an endpoint returning the port of the running instance. This allows you to see which instance is responding to each request.

The repository also includes a configuration file for the API Gateway. You will use NGINX, a popular web server/reverse proxy that can serve static files, forward requests to backend servers, and load balance traffic, which is the focus of this exercise.

## API Gateway

To run the API Gateway, you first need to complete the configuration file by adding the addresses of the running Node.js application instances. Once the addresses are added, you can start the API Gateway:

1. Install NGINX:

    On mac via Homebrew:
    ```bash
    brew install nginx
    ```
    On Windows: [https://nginx.org/en/docs/windows.html](https://nginx.org/en/docs/windows.html)

2. Start NGINX using the custom config file:

    ```bash
    sudo nginx -c /your/path/load-balancing-exercise/load-balancing-exercise/api-gateway-nginx.conf
    ```
    Now the API Gateway should be listening on `localhost:8080`.

    Make sure when you refresh the page multiple times you get different port numbers — that means the requests are being distributed across the different instances of the application.

3. To stop the API Gateway:

    ```bash
    sudo nginx -s stop
    ```


