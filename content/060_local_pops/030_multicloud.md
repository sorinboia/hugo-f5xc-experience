+++
title = "Multicloud App"
weight = 30
+++

1. Create AWS Pool


{{< code >}}
{
  "metadata": {
    "name": "arcadia-aws-origin-pool",
    "labels": {},
    "annotations": {},
    "disable": false
  },
  "spec": {
    "origin_servers": [
      {
        "private_name": {
          "dns_name": "arcadiaaws.aws.internal",
          "site_locator": {
            "site": {
              "namespace": "system",
              "name": "::ceOnAws::",
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

2. Change the LB configuration

{{< code >}}
{{< /code >}}