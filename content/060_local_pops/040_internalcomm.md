+++
title = "Inter DC communication"
weight = 40
+++

1. Create the **internal Load Balancer** which will route the traffic from the AWS site **Stock transaction** service to the onprem **Users** service

![](/images/6/Slide4.PNG)

{{< code >}}
{
  "metadata": {
    "name": "arcadia-aws-to-onprem",
    "labels": {},
    "annotations": {},
    "disable": false
  },
  "spec": {
    "domains": [
      "arcadiaonprem.aws.internal"
    ],
    "http": {
      "dns_volterra_managed": false,
      "port": 80
    },
    "advertise_custom": {
      "advertise_where": [
        {
          "site": {
            "network": "SITE_NETWORK_INSIDE_AND_OUTSIDE",
            "site": {
              "namespace": "system",
              "name": "::ceOnAws::",
              "kind": "site"
            }
          },
          "use_default_port": {}
        }
      ]
    },
    "default_route_pools": [
      {
        "pool": {
          "name": "arcadia-onprem-origin-pool",
          "kind": "origin_pool"
        },
        "weight": 1,
        "priority": 1,
        "endpoint_subsets": {}
      }
    ],
    "disable_waf": {},
    "add_location": true,
    "no_challenge": {},
    "user_id_client_ip": {},
    "disable_rate_limit": {},
    "service_policies_from_namespace": {},
    "round_robin": {},
    "disable_trust_client_ip_headers": {},
    "disable_ddos_detection": {},
    "disable_malicious_user_detection": {},
    "disable_api_discovery": {},
    "disable_bot_defense": {},
    "disable_api_definition": {},
    "disable_ip_reputation": {},
    "disable_client_side_defense": {}
  }
}
{{< /code >}}

2. Go ahead and verify that you can buy/sell crypto currency.

3. Go to the **"arcadia-aws-to-onprem" Load Balancer** statistics and observe that the inter sites communication is fully visible.

![](/images/6/Slide7.PNG)