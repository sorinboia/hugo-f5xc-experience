+++
title = "Load Balancer Routing"
weight = 20
+++


The last step will be to instruct the **Load Balancer** to send the relevant traffic to the service hosted in the Virtual Kubernetes environment.



1. Create a pool that represent the vK8s deployment.

![](/images/6/Slide2.PNG)

{{< code >}}
{
  "metadata": {
    "name": "arcadia-stocks-vk8s",
    "namespace": "::namespace::",
    "labels": {},
    "annotations": {},
    "disable": false
  },
  "spec": {
    "origin_servers": [
      {
        "k8s_service": {
          "service_name": "arcadia-stocks.::namespace::",
          "site_locator": {
            "site": {             
              "tenant": "ves-io", 
              "namespace": "system",
              "name": "tn2-lon",
              "kind": "site"
            }
          },
          "vk8s_networks": {}
        },
        "labels": {}
      }
    ],
    "no_tls": {},
    "port": 80,
    "same_as_endpoint_port": {},
    "healthcheck": [
      {
        "tenant": "f5-sales-public-qdpwiibg",
        "namespace": "::namespace::",
        "name": "tcp-monitor",
        "kind": "healthcheck"
      }
    ],
    "loadbalancer_algorithm": "LB_OVERRIDE",
    "endpoint_selection": "LOCAL_PREFERRED"
  }
}
{{< /code >}} 

2. Change the routing config

![](/images/7/Slide3.PNG)


