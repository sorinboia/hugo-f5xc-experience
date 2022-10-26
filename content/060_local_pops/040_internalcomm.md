+++
title = "Inter DC communication"
weight = 40
+++

1. Create the internal LB


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