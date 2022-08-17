+++
title = "Accessing the platform"

weight = 30
chapter = true
pre = "<b>3. </b>"
+++

Previously we have deployed the application but did not expose the services.  

We need to be able to route the requests to the relevant service.

Nginx Kubernetes Ingress to save the day! :)
The NGINX Ingress Controller for Kubernetes provides enterprise‑grade delivery services for Kubernetes applications, with benefits for users of both NGINX Open Source and NGINX Plus. With the NGINX Ingress Controller for Kubernetes, you get basic load balancing, SSL/TLS termination, support for URI rewrites, and upstream SSL/TLS encryption. NGINX Plus users additionally get session persistence for stateful applications and JSON Web Token (JWT) authentication for APIs.  

![](/images/Slide2.JPG)