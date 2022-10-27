+++
title = "Multicloud App"
weight = 30
+++

1. Create a new **Pool** for the part of the application that is deployed in AWS
![](/images/6/Slide2.PNG)

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

2. Change the **"arcadia" Load Balancer** configuration. Since we decided to move our app into the cloud we will change the default pool to the Aws application pool.  
At the same time the **Login** and **User** services deal with sensetive data and the regulation does not allow us to move this services, they will need to remain in our onprem environment.
![](/images/6/Slide6.PNG)

{{< code >}}
{
  "metadata": {
    "name": "arcadia",
    "namespace": "::namespace::",
    "annotations": {},
    "disable": false
  },
  "spec": {
    "domains": [
      "::acradiaCe::"
    ],
    "https_auto_cert": {
      "http_redirect": true,
      "add_hsts": false,
      "port": 443,
      "tls_config": {
        "default_security": {}
      },
      "no_mtls": {},
      "default_header": {},
      "enable_path_normalize": {},
      "non_default_loadbalancer": {},
      "header_transformation_type": {
        "default_header_transformation": {}
      }
    },
    "advertise_on_public_default_vip": {},
    "default_route_pools": [
      {
        "pool": {
          "tenant": "f5-sales-public-qdpwiibg",
          "namespace": "::namespace::",
          "name": "arcadia-aws-origin-pool",
          "kind": "origin_pool"
        },
        "weight": 1,
        "priority": 1,
        "endpoint_subsets": {}
      }
    ],
    "routes": [
      {
        "simple_route": {
          "path": {
            "prefix": "/v1/login"
          },
          "origin_pools": [
            {
              "pool": {
                "tenant": "f5-sales-public-qdpwiibg",
                "namespace": "::namespace::",
                "name": "arcadia-onprem-origin-pool",
                "kind": "origin_pool"
              },
              "weight": 1,
              "priority": 1,
              "endpoint_subsets": {}
            }
          ],
          "auto_host_rewrite": {}
        }
      },
      {
        "simple_route": {
          "path": {
            "prefix": "/v1/user"
          },
          "origin_pools": [
            {
              "pool": {
                "tenant": "f5-sales-public-qdpwiibg",
                "namespace": "::namespace::",
                "name": "arcadia-onprem-origin-pool",
                "kind": "origin_pool"
              },
              "weight": 1,
              "priority": 1,
              "endpoint_subsets": {}
            }
          ],
          "auto_host_rewrite": {}
        }
      }
    ],
    "app_firewall": {
      "tenant": "f5-sales-public-qdpwiibg",
      "namespace": "::namespace::",
      "name": "arcadia-waf",
      "kind": "app_firewall"
    },
    "add_location": false,
    "no_challenge": {},
    "user_id_client_ip": {},
    "disable_rate_limit": {},
    "waf_exclusion_rules": [],
    "data_guard_rules": [],
    "blocked_clients": [],
    "trusted_clients": [],
    "ddos_mitigation_rules": [],
    "active_service_policies": {
      "policies": [
        {
          "tenant": "f5-sales-public-qdpwiibg",
          "namespace": "::namespace::",
          "name": "arcadia-api-enforcer",
          "kind": "service_policy"
        }
      ]
    },
    "round_robin": {},
    "disable_trust_client_ip_headers": {},
    "enable_ddos_detection": {},
    "enable_malicious_user_detection": {},
    "enable_api_discovery": {
      "disable_learn_from_redirect_traffic": {}
    },
    "api_definition": {
      "tenant": "f5-sales-public-qdpwiibg",
      "namespace": "::namespace::",
      "name": "arcadia-api-definition",
      "kind": "api_definition"
    }
  }
}
{{< /code >}}

3. Try and buy or sell a crypto currency.  
You will observe that the transaction is stuck. This is happening because the **Stock Transaction** service in AWS needs to contact the **User** service which has remained on prem.  
We will enable secure connectivity in the next steps.