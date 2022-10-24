+++
title = "Directly inside"
date = 2020-07-08T14:37:59+03:00
weight = 10
+++



1. Create a HTTP health check object
![](/images/6/Slide1.PNG)


{{< code >}}
{
  "metadata": {
    "name": "http-hc",
    "labels": {},
    "annotations": {},
    "disable": false
  },
  "spec": {
    "http_health_check": {
      "host_header": "::makeid::.sales-public.f5demos.com",
      "path": "/",
      "use_http2": false,
      "headers": {}
    },
    "timeout": 3,
    "interval": 15,
    "unhealthy_threshold": 1,
    "healthy_threshold": 3,
    "jitter_percent": 30
  }
}
{{< /code >}} 

2. Create the pool that will represent our backend services
![](/images/6/Slide2.PNG)

{{< code >}}
{
  "metadata": {
    "name": "arcadia-onprem-origin-pool",
    "labels": {},
    "annotations": {},
    "disable": false
  },
  "spec": {
    "origin_servers": [
      {
        "private_ip": {
          "ip": "10.1.1.5",
          "site_locator": {
            "site": {
              "namespace": "system",
              "name": "::ceOnPrem::",
              "kind": "site"
            }
          },
          "outside_network": {}
        },
        "labels": {}
      },
      {
        "private_ip": {
          "ip": "10.1.1.6",
          "site_locator": {
            "site": {
              "namespace": "system",
              "name": "::ceOnPrem::",
              "kind": "site"
            }
          },
          "outside_network": {}
        },
        "labels": {}
      }
    ],
    "no_tls": {},
    "port": 31970,
    "same_as_endpoint_port": {},
    "healthcheck": [
      {
        "name": "http-hc",
        "kind": "healthcheck"
      }
    ],
    "loadbalancer_algorithm": "LB_OVERRIDE",
    "endpoint_selection": "LOCAL_PREFERRED"
  }
}
{{< /code >}} 



3. Point the Load Balancer directly to the internal servers

![](/images/6/Slide3.PNG)