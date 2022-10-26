+++
title = "Load balancer onprem"
weight = 20
+++

1. Publish the LB
![](/images/6/Slide1.PNG)

{{< code >}}
{
  "metadata": {
    "name": "arcadia-ce-onprem",
    "labels": {},
    "annotations": {},
    "disable": false
  },
  "spec": {
    "domains": [
      "::acradiaCe::"
    ],
    "https": {
      "http_redirect": false,
      "add_hsts": false,
      "port": 443,
      "tls_parameters": {
        "tls_config": {
          "default_security": {}
        },
        "tls_certificates": [
          {
            "certificate_url": "string:///LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURwekNDQW8rZ0F3SUJBZ0lVUC91T1ZITmladElUaFdNN0lSRDVMMFo2cXpBd0RRWUpLb1pJaHZjTkFRRUwKQlFBd1l6RUxNQWtHQTFVRUJoTUNTVXd4RXpBUkJnTlZCQWdNQ2xOdmJXVXRVM1JoZEdVeElUQWZCZ05WQkFvTQpHRWx1ZEdWeWJtVjBJRmRwWkdkcGRITWdVSFI1SUV4MFpERWNNQm9HQTFVRUF3d1RLaTVoWTJObGMzTXVkV1JtCkxtWTFMbU52YlRBZUZ3MHlNakV3TWpReE5URTNOVE5hRncweU16RXdNalF4TlRFM05UTmFNR014Q3pBSkJnTlYKQkFZVEFrbE1NUk13RVFZRFZRUUlEQXBUYjIxbExWTjBZWFJsTVNFd0h3WURWUVFLREJoSmJuUmxjbTVsZENCWAphV1JuYVhSeklGQjBlU0JNZEdReEhEQWFCZ05WQkFNTUV5b3VZV05qWlhOekxuVmtaaTVtTlM1amIyMHdnZ0VpCk1BMEdDU3FHU0liM0RRRUJBUVVBQTRJQkR3QXdnZ0VLQW9JQkFRREhhRGZyNktFMlRXK0dLUEdDSVlOdVNrTHEKdW5zaWRxTzJBazFBMFI1eGZPN042bm02WXBNRVN4T0tvYldQNCtCbXNNek0zOExPS05ERm9reklNRUs3ZFdBZwpYa0FTZTVzNkpkTEFRSXFmOThPbWVFbWZUcW02OGFPMWlGWXphYTdMSEM4cjZPMlhyb2VUWnZJUXhNTVVvMlNwCld2Si91cUFJalcwRnNjSU1seVJhTzVlNWZNNUNWczRFV1ZCbHFQWkRTeWRrYjRLZFZydWtJNmR2MDRUSUwzWlAKbGJldnE5TjAzMzdnbnoxN2VERCtmemJwa2Z5c0Q3aEFSVytmQVQ5NzZPbDAwdkhDOENGaWdJMzhJdm5TSjE0Zgp5eE1EL0Z5Njd4WjdxRWliakN5MzdETlFTZzlpdmxjYUR1NkpBT21YZ09wakFMc3dXZUN1bE1ZQlNtWk5BZ01CCkFBR2pVekJSTUIwR0ExVWREZ1FXQkJRTTRjbElMeVNaTnFuSlNVaVNFZ2RYWWc1TGJ6QWZCZ05WSFNNRUdEQVcKZ0JRTTRjbElMeVNaTnFuSlNVaVNFZ2RYWWc1TGJ6QVBCZ05WSFJNQkFmOEVCVEFEQVFIL01BMEdDU3FHU0liMwpEUUVCQ3dVQUE0SUJBUUN4bVhTVEJVaDJHVFFnYys1TDdZSEdFY3ExeWZhRmNDWHEzdnhVeFk3d2txZURKZTdyCjJlK0xwODZ2ZitzQkxwOHV6MktXb2Q3YmxiaUVpeGdveHRZSm9qVlNYeDgrdk1Zc2JiZXlHSmVTZXR6SWhkZkgKSUlpZXNrM3ZMT3BpWDFLRm4yWE9jaFRFWE5SK3NFR2RaZy9sZ1U3MDVrWllZbndIZFppaUF6UjI1YXJUbWEwNgpTekdWZDR0cnJsdVVKR1BBcGZUMHhRL0tMMUpDTnEwR3ZtbzVmc3QrWlJWdHBOSVhPSitHVWlQMDlZZzNseitYCnBWTEhrV3kxcWFiejhaNWp3aTVxaXBwWjVBQVdFTS9qUXhGMWRCYWFNL2ZSWXVLdmFtM1ZsQStIU0FtZUk1K3kKVWN6YVF4d21VNEJ3YWFlbGQ5WXh0VnArUlk5RXBIWXlTWGJSCi0tLS0tRU5EIENFUlRJRklDQVRFLS0tLS0=",
            "private_key": {
              "clear_secret_info": {
                "url": "string:///LS0tLS1CRUdJTiBQUklWQVRFIEtFWS0tLS0tCk1JSUV2QUlCQURBTkJna3Foa2lHOXcwQkFRRUZBQVNDQktZd2dnU2lBZ0VBQW9JQkFRREhhRGZyNktFMlRXK0cKS1BHQ0lZTnVTa0xxdW5zaWRxTzJBazFBMFI1eGZPN042bm02WXBNRVN4T0tvYldQNCtCbXNNek0zOExPS05ERgpva3pJTUVLN2RXQWdYa0FTZTVzNkpkTEFRSXFmOThPbWVFbWZUcW02OGFPMWlGWXphYTdMSEM4cjZPMlhyb2VUClp2SVF4TU1VbzJTcFd2Si91cUFJalcwRnNjSU1seVJhTzVlNWZNNUNWczRFV1ZCbHFQWkRTeWRrYjRLZFZydWsKSTZkdjA0VElMM1pQbGJldnE5TjAzMzdnbnoxN2VERCtmemJwa2Z5c0Q3aEFSVytmQVQ5NzZPbDAwdkhDOENGaQpnSTM4SXZuU0oxNGZ5eE1EL0Z5Njd4WjdxRWliakN5MzdETlFTZzlpdmxjYUR1NkpBT21YZ09wakFMc3dXZUN1CmxNWUJTbVpOQWdNQkFBRUNnZ0VBYmp4WkhkdCtzOHhmS09XZGpYa0ZkWVVzTlNOZVN4RVhNOWxWNTgwemJUM0oKcnFBL0p5Q3pjWjRuY1c0d054bWN4bWhhNzYrTHUvaW9ZWGwxeFAyWkJwUyt6V1lOT2FxSGg3KzlJSGNOcTUyRwoxWktOOExuRjd3a0NuYXAvTFBEeHBtc3dVSy8yR1BKdEZMbkdmQ3FxUmRDR0ozR1Z1YkxzSVk0OWhQWmQ5aUxsCjUvMVdWWnN1NDk5NW41TThHY3JNbkprVWdwYXdsUkY0TUNmbVpmQ2hSVkprcWQrc0RKRDRKR3RzS1p1OHViSkUKRFQ0ekw4YWprNUdGRnh2N292M0d0czVMUUhNTDBXSVh6SSs4bW53VzZBZkhjNlg1VDg3Q1FqakV4UGpjd0JRZwpHbm11YnBwQmdFbEtmckNPZGlGMkR3SG05di9WOU4yYTdFZk5BSk51cVFLQmdRRHM5Nm0rNEJkdjBQNmlDbDVtCjVUNHN2cDhJOGM5UldNTDNWMlIvQXBzNXFETHNPZ2FIRmVreG8wTG1iYmFEWEluLzZLbkV2Vi83SEYrRGhRM1gKaDlvNW5KV1h2TGxLUURxc2pUN0NhME1LRGNxWVI3VkN5alZWcDV2LzhySEJsZHVvcER0V2hZNjgrYUZzSUJxego2bGY5aWxVTzg1c1JwbVpVRlFiSGdvVHZId0tCZ1FEWGJFVUNheTgyT3R6OHZYbXA2akExRytMZlVwOWc3OFZuClJad0Zvb3ZxN2VDRUQrZDQrNU1IM3F3MUNaemRUSmtNY2RTMVJXK3JGaVZhNWJDdmRUREREVzVMOHJRSG1zM3MKcm16OC8zUEdhb2p6OGszVFdiTjBWakNLNWpHb1M5a3Z0SHhNcE9qcEtvODJJVkZ6QUZjZ0JvQldpOU10a1k2MAppWmczY2JsNUV3S0JnQmlpWW40YVU3Vm5GNkdHekd1TDkxdTFjVmovc2xxMWpJY2tDYWwrZnQ2T2tzU2wvNW01CmVHV1ZvRlhPSUFRbDhaNnQ5RUFrbzc2NkkxL0x6RFdVeE9YcVZrN1E2cjVDVVJjeEU4NG9VbTdRSWppVWM4NSsKc082M251c0xzdGo2R0R5KzNnQlBvQmdiSjJIVE1KTjFrREltV0ZOV2xjOU82aUpoa1RQYWFMRm5Bb0dBZlZKaApPeXo3eEVLdU9PSkptdzNBaWNUMVVSSVI0aVRhNUY5Y2l2S3JEenJmdURSQVp1T0QvN29NMkxZRTZjRWI4Rjl3CmJSdytBSHZiczJ1WVJCcWJDWDRRd21JcFZaczdYUXVFSUJMRVdaTzBwS1k3bkU2ODFWc20xa2RnY0JYZi9aNjAKQ1NxT3pNYVRsZHdBTkRUb2Vwc05va3VweVFLNjBGQ1RtdjJ2OXIwQ2dZQjA2VndOazQwRERGbXBJenhDalZoSApFWWwrUWhOdmJ5TGxKaFVBczZaeGhUYUZrb2tkVVRiOTRjcHNWeHZKenVoZ3VJblJiYWtlL1FWTnl6ZG9uWlNmCkJYWTZ2bktnY292QTNwOEpOeFNNcUh4eVE0WmVJQnZYRFBFYXhYR0Qzcmo0eURVZFZJY1p4Szgwb0NFWWNOcWkKM2VTUHU3cGRLWlNxYWF0NFltdEpxUT09Ci0tLS0tRU5EIFBSSVZBVEUgS0VZLS0tLS0="
              }
            },
            "disable_ocsp_stapling": {}
          }
        ],
        "no_mtls": {}
      },
      "default_header": {},
      "enable_path_normalize": {},
      "non_default_loadbalancer": {}
    },
    "advertise_custom": {
      "advertise_where": [
        {
          "site": {
            "network": "SITE_NETWORK_INSIDE_AND_OUTSIDE",
            "site": {
              "namespace": "system",
              "name": "::ceOnPrem::",
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