---
slug: /events
---

# Event Sources
---------------

Event Sources represent event types from your ngrok account. You can subscribe to one or more of them using an Event Subscription. Each Event Subscription can send these events to a configurable destination such as Amazon CloudWatch Logs, Amazon Kinesis (as a data stream) or Amazon Kinesis Firehose (as a delivery stream).

Many objects within ngrok have corresponding events that are generated when an instance of the object is created, updated and deleted. All Event Types have a version, represented in the Event Type string following the period. The initial version for all Event Types is `v0`.

Some event types support filters and selectable fields. Not all selectable fields are usable in filters. A full list of event types and their fields follows. A field marked "filterable" indicates that it is usable in the filter for an event source.

### Event Payloads

Events are sent as JSON to the configured destinations. These event payloads are purposefully identical to the ngrok API responses. All events include the following fields:

| Name | Description | Example |
| --- | --- | --- |
| `event_id` | unique identifier for this event, always prefixed with ev_ | `ev_1vPlyBW3OR44bpPphS4HIZyajDD` |
| `event_type` | identifies the object, action, and version of the event | `ip_policy_created.v0` |
| `event_timestamp` | timestamp of when the event fired in RFC 3339 format | `2021-07-16T21:44:37Z` |
| `object` | a JSON object describing the resource where the event occurred | See examples below |

### Event Payloads Examples

#### Complete example payload for an ip\_policy\_created.v0 event

    {
        "event_id": "ev_25X2AsJ5xpvuOParTYUQWe12XKo",
        "event_type": "ip_policy_created.v0",
        "event_timestamp": "2022-02-23T23:29:29Z",
        "object": {
            "id": "ipp_25X2Ao39z73FlVQKZ1iReMPe6Qv",
            "uri": "https://api.ngrok.com/ip_policies/ipp_25X2Ao39z73FlVQKZ1iReMPe6Qv",
            "created_at": "2022-02-23T23:29:29Z",
            "description": "Home network IP",
            "metadata": "",
            "action": "allow"
        }
    }

#### Complete example payload for an http\_request\_complete.v0 event

    {
        "event_id": "ev_25X3yFS6TDkig1KDJWIc4nnJO0c",
        "event_type": "http_request_complete.v0",
        "event_timestamp": "2022-02-23T23:44:16Z",
        "object": {
            "conn": {
                "client_ip": "2601:0:8200:9e:4cd7:0:c97f:7823",
                "server_name": "ngrok-docs-example.ngrok.io",
                "server_port": ""
            },
            "http": {
                "request": {
                    "first_byte_ts": null,
                    "last_byte_ts": null,
                    "method": "GET",
                    "url": {
                        "path": "/docs/events"
                    },
                    "version": "HTTP/2.0"
                },
                "response": {
                    "body_length": 13079,
                    "first_byte_ts": "2022-02-23T23:44:16.732791273Z",
                    "last_byte_ts": "2022-02-23T23:44:16.737257209Z",
                    "status_code": 200
                }
            }
        }
    }

#### Complete example payload for an tcp\_connection\_closed.v0 event

    {
        "event_id": "ev_25X4osod1q306srserDeFyghTC4",
        "event_type": "tcp_connection_closed.v0",
        "event_timestamp": "2022-02-23T23:51:14Z",
        "object": {
            "conn": {
                "bytes_in": 3437,
                "bytes_out": 90256,
                "client_ip": "2601:0:8200:9e:4cd7:0:c97f:7823",
                "end_ts": "2022-02-23T23:51:14.005372199Z",
                "server_name": "ngrok-docs-example.ngrok.io",
                "server_port": "",
                "start_ts": "2022-02-23T23:44:16.528374173Z"
            }
        }
    }

## Event Sources

| Event | Description |
| --- | --- |
| [`api_key_created.v0`](#api_key_createdv0) | Triggers when an API key is created |
| [`api_key_deleted.v0`](#api_key_deletedv0) | Triggers when an API key is deleted |
| [`api_key_updated.v0`](#api_key_updatedv0) | Triggers when an API key is updated |
| [`certificate_authority_created.v0`](#certificate_authority_createdv0) | Triggers when a certificate authority is created |
| [`certificate_authority_deleted.v0`](#certificate_authority_deletedv0) | Triggers when a certificate authority is deleted |
| [`certificate_authority_updated.v0`](#certificate_authority_updatedv0) | Triggers when a certificate authority is updated |
| [`domain_created.v0`](#domain_createdv0) | Triggers when a domain is created |
| [`domain_deleted.v0`](#domain_deletedv0) | Triggers when a domain is deleted |
| [`domain_updated.v0`](#domain_updatedv0) | Triggers when a domain is updated |
| [`event_destination_created.v0`](#event_destination_createdv0) | Triggers when an Event Destination is created |
| [`event_destination_deleted.v0`](#event_destination_deletedv0) | Triggers when an Event Destination is deleted |
| [`event_destination_updated.v0`](#event_destination_updatedv0) | Triggers when an Event Destination is updated |
| [`event_subscription_created.v0`](#event_subscription_createdv0) | Triggers when an Event Subscription is created |
| [`event_subscription_deleted.v0`](#event_subscription_deletedv0) | Triggers when an Event Subscription is deleted |
| [`event_subscription_updated.v0`](#event_subscription_updatedv0) | Triggers when an Event Subscription is updated |
| [`http_request_complete.v0`](#http_request_completev0) | Triggers when an HTTP request completes. This is a high cardinality event. Use filters to reduce number of events. |
| [`ip_policy_created.v0`](#ip_policy_createdv0) | Triggers when an IP Policy is created. |
| [`ip_policy_deleted.v0`](#ip_policy_deletedv0) | Triggers when an IP Policy is deleted. |
| [`ip_policy_updated.v0`](#ip_policy_updatedv0) | Triggers when an IP Policy is updated. |
| [`ip_policy_rule_created.v0`](#ip_policy_rule_createdv0) | Triggers when an IP Policy Rule is created. |
| [`ip_policy_rule_deleted.v0`](#ip_policy_rule_deletedv0) | Triggers when an IP Policy Rule is deleted. |
| [`ip_policy_rule_updated.v0`](#ip_policy_rule_updatedv0) | Triggers when an IP Policy Rule is updated. |
| [`ip_restriction_created.v0`](#ip_restriction_createdv0) | Triggers when an IP Restriction is created. |
| [`ip_restriction_deleted.v0`](#ip_restriction_deletedv0) | Triggers when an IP Restriction is deleted. |
| [`ip_restriction_updated.v0`](#ip_restriction_updatedv0) | Triggers when an IP Restriction is updated. |
| [`ssh_certificate_authority_created.v0`](#ssh_certificate_authority_createdv0) | Triggers when an SSH certificate authority is created. |
| [`ssh_certificate_authority_deleted.v0`](#ssh_certificate_authority_deletedv0) | Triggers when an SSH certificate authority is deleted. |
| [`ssh_certificate_authority_updated.v0`](#ssh_certificate_authority_updatedv0) | Triggers when an SSH certificate authority is updated. |
| [`ssh_host_certificate_created.v0`](#ssh_host_certificate_createdv0) | Triggers when an SSH host certificate is created. |
| [`ssh_host_certificate_deleted.v0`](#ssh_host_certificate_deletedv0) | Triggers when an SSH host certificate is deleted. |
| [`ssh_host_certificate_updated.v0`](#ssh_host_certificate_updatedv0) | Triggers when an SSH host certificate is updated. |
| [`ssh_public_key_created.v0`](#ssh_public_key_createdv0) | Triggers when an SSH public key is created. |
| [`ssh_public_key_deleted.v0`](#ssh_public_key_deletedv0) | Triggers when an SSH public key is deleted. |
| [`ssh_public_key_updated.v0`](#ssh_public_key_updatedv0) | Triggers when an SSH public key is updated. |
| [`ssh_user_certificate_created.v0`](#ssh_user_certificate_createdv0) | Triggers when an SSH user certificate is created. |
| [`ssh_user_certificate_deleted.v0`](#ssh_user_certificate_deletedv0) | Triggers when an SSH user certificate is deleted. |
| [`ssh_user_certificate_updated.v0`](#ssh_user_certificate_updatedv0) | Triggers when an SSH user certificate is updated. |
| [`tcp_address_created.v0`](#tcp_address_createdv0) | Triggers when a TCP address is created. |
| [`tcp_address_deleted.v0`](#tcp_address_deletedv0) | Triggers when a TCP address is deleted. |
| [`tcp_address_updated.v0`](#tcp_address_updatedv0) | Triggers when a TCP address is updated. |
| [`tcp_connection_closed.v0`](#tcp_connection_closedv0) | Triggers when a TCP connection to an endpoint closes. This is a high cardinality event. Use filters to select the events you need. |
| [`tls_certificate_created.v0`](#tls_certificate_createdv0) | Triggers when a TLS certificate is created. |
| [`tls_certificate_deleted.v0`](#tls_certificate_deletedv0) | Triggers when a TLS certificate is deleted. |
| [`tls_certificate_updated.v0`](#tls_certificate_updatedv0) | Triggers when a TLS certificate is updated. |
| [`tunnel_credential_created.v0`](#tunnel_credential_createdv0) | Triggers when a tunnel credential is created. |
| [`tunnel_credential_deleted.v0`](#tunnel_credential_deletedv0) | Triggers when a tunnel credential is deleted. |
| [`tunnel_credential_updated.v0`](#tunnel_credential_updatedv0) | Triggers when a tunnel credential is updated. |

## Event Types

This is a complete list of all the event types and fields available in the events system.


### API Key

#### api\_key\_created.v0

Triggers when an API key is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique API key resource identifier |
| uri | string | URI to the API resource of this API key |
| description | string | human-readable description of what uses the API key to authenticate. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined data of this API key. optional, max 4096 bytes |
| created_at | string | timestamp when the api key was created, RFC 3339 format |
| token | string | the bearer token that can be placed into the Authorization header to authenticate request to the ngrok API. **This value is only available one time, on the API response from key creation. Otherwise it is null.** |

#### api\_key\_deleted.v0

Triggers when an API key is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique API key resource identifier |
| uri | string | URI to the API resource of this API key |
| description | string | human-readable description of what uses the API key to authenticate. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined data of this API key. optional, max 4096 bytes |
| created_at | string | timestamp when the api key was created, RFC 3339 format |
| token | string | the bearer token that can be placed into the Authorization header to authenticate request to the ngrok API. **This value is only available one time, on the API response from key creation. Otherwise it is null.** |

#### api\_key\_updated.v0

Triggers when an API key is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique API key resource identifier |
| uri | string | URI to the API resource of this API key |
| description | string | human-readable description of what uses the API key to authenticate. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined data of this API key. optional, max 4096 bytes |
| created_at | string | timestamp when the api key was created, RFC 3339 format |
| token | string | the bearer token that can be placed into the Authorization header to authenticate request to the ngrok API. **This value is only available one time, on the API response from key creation. Otherwise it is null.** |


### Certificate Authority

#### certificate\_authority\_created.v0

Triggers when a certificate authority is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this Certificate Authority |
| uri | string | URI of the Certificate Authority API resource |
| created_at | string | timestamp when the Certificate Authority was created, RFC 3339 format |
| description | string | human-readable description of this Certificate Authority. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this Certificate Authority. optional, max 4096 bytes. |
| ca_pem | string | raw PEM of the Certificate Authority |
| subject\_common\_name | string | subject common name of the Certificate Authority |
| not_before | string | timestamp when this Certificate Authority becomes valid, RFC 3339 format |
| not_after | string | timestamp when this Certificate Authority becomes invalid, RFC 3339 format |
| key_usages | List&lt;string&gt; | set of actions the private key of this Certificate Authority can be used for |
| extended\_key\_usages | List&lt;string&gt; | extended set of actions the private key of this Certificate Authority can be used for |

#### certificate\_authority\_deleted.v0

Triggers when a certificate authority is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this Certificate Authority |
| uri | string | URI of the Certificate Authority API resource |
| created_at | string | timestamp when the Certificate Authority was created, RFC 3339 format |
| description | string | human-readable description of this Certificate Authority. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this Certificate Authority. optional, max 4096 bytes. |
| ca_pem | string | raw PEM of the Certificate Authority |
| subject\_common\_name | string | subject common name of the Certificate Authority |
| not_before | string | timestamp when this Certificate Authority becomes valid, RFC 3339 format |
| not_after | string | timestamp when this Certificate Authority becomes invalid, RFC 3339 format |
| key_usages | List&lt;string&gt; | set of actions the private key of this Certificate Authority can be used for |
| extended\_key\_usages | List&lt;string&gt; | extended set of actions the private key of this Certificate Authority can be used for |

#### certificate\_authority\_updated.v0

Triggers when a certificate authority is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this Certificate Authority |
| uri | string | URI of the Certificate Authority API resource |
| created_at | string | timestamp when the Certificate Authority was created, RFC 3339 format |
| description | string | human-readable description of this Certificate Authority. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this Certificate Authority. optional, max 4096 bytes. |
| ca_pem | string | raw PEM of the Certificate Authority |
| subject\_common\_name | string | subject common name of the Certificate Authority |
| not_before | string | timestamp when this Certificate Authority becomes valid, RFC 3339 format |
| not_after | string | timestamp when this Certificate Authority becomes invalid, RFC 3339 format |
| key_usages | List&lt;string&gt; | set of actions the private key of this Certificate Authority can be used for |
| extended\_key\_usages | List&lt;string&gt; | extended set of actions the private key of this Certificate Authority can be used for |

### Domain

#### domain_created.v0

Triggers when a domain is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique reserved domain resource identifier |
| uri | string | URI of the reserved domain API resource |
| created_at | string | timestamp when the reserved domain was created, RFC 3339 format |
| description | string | human-readable description of what this reserved domain will be used for |
| metadata | string | arbitrary user-defined machine-readable data of this reserved domain. Optional, max 4096 bytes. |
| domain | string | hostname of the reserved domain |
| region | string | reserve the domain in this geographic ngrok datacenter. Optional, default is us. (au, eu, ap, us, jp, in, sa) |
| cname_target | string | DNS CNAME target for a custom hostname, or null if the reserved domain is a subdomain of *.ngrok.io |
| certificate.id | string | a resource identifier |
| certificate.uri | string | a uri for locating a resource |
| certificate\_management\_policy.authority | string | certificate authority to request certificates from. The only supported value is letsencrypt. |
| certificate\_management\_policy.private\_key\_type | string | type of private key to use when requesting certificates. Defaults to rsa, can be either rsa or ecdsa. |
| certificate\_management\_status.renews_at | string | timestamp when the next renewal will be requested, RFC 3339 format |
| certificate\_management\_status.provisioning\_job.error\_code | string | if present, an error code indicating why provisioning is failing. It may be either a temporary condition (INTERNAL\_ERROR), or a permanent one the user must correct (DNS\_ERROR). |
| certificate\_management\_status.provisioning_job.msg | string | a message describing the current status or error |
| certificate\_management\_status.provisioning\_job.started\_at | string | timestamp when the provisioning job started, RFC 3339 format |
| certificate\_management\_status.provisioning\_job.retries\_at | string | timestamp when the provisioning job will be retried |
| acme\_challenge\_cname_target | string | DNS CNAME target for the host _acme-challenge.example.com, where example.com is your reserved domain name. This is required to issue certificates for wildcard, non-ngrok reserved domains. Must be null for non-wildcard domains and ngrok subdomains. |

#### domain_deleted.v0

Triggers when a domain is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique reserved domain resource identifier |
| uri | string | URI of the reserved domain API resource |
| created_at | string | timestamp when the reserved domain was created, RFC 3339 format |
| description | string | human-readable description of what this reserved domain will be used for |
| metadata | string | arbitrary user-defined machine-readable data of this reserved domain. Optional, max 4096 bytes. |
| domain | string | hostname of the reserved domain |
| region | string | reserve the domain in this geographic ngrok datacenter. Optional, default is us. (au, eu, ap, us, jp, in, sa) |
| cname_target | string | DNS CNAME target for a custom hostname, or null if the reserved domain is a subdomain of *.ngrok.io |
| certificate.id | string | a resource identifier |
| certificate.uri | string | a uri for locating a resource |
| certificate\_management\_policy.authority | string | certificate authority to request certificates from. The only supported value is letsencrypt. |
| certificate\_management\_policy.private\_key\_type | string | type of private key to use when requesting certificates. Defaults to rsa, can be either rsa or ecdsa. |
| certificate\_management\_status.renews_at | string | timestamp when the next renewal will be requested, RFC 3339 format |
| certificate\_management\_status.provisioning\_job.error\_code | string | if present, an error code indicating why provisioning is failing. It may be either a temporary condition (INTERNAL\_ERROR), or a permanent one the user must correct (DNS\_ERROR). |
| certificate\_management\_status.provisioning_job.msg | string | a message describing the current status or error |
| certificate\_management\_status.provisioning\_job.started\_at | string | timestamp when the provisioning job started, RFC 3339 format |
| certificate\_management\_status.provisioning\_job.retries\_at | string | timestamp when the provisioning job will be retried |
| acme\_challenge\_cname_target | string | DNS CNAME target for the host _acme-challenge.example.com, where example.com is your reserved domain name. This is required to issue certificates for wildcard, non-ngrok reserved domains. Must be null for non-wildcard domains and ngrok subdomains. |

#### domain_updated.v0

Triggers when a domain is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique reserved domain resource identifier |
| uri | string | URI of the reserved domain API resource |
| created_at | string | timestamp when the reserved domain was created, RFC 3339 format |
| description | string | human-readable description of what this reserved domain will be used for |
| metadata | string | arbitrary user-defined machine-readable data of this reserved domain. Optional, max 4096 bytes. |
| domain | string | hostname of the reserved domain |
| region | string | reserve the domain in this geographic ngrok datacenter. Optional, default is us. (au, eu, ap, us, jp, in, sa) |
| cname_target | string | DNS CNAME target for a custom hostname, or null if the reserved domain is a subdomain of *.ngrok.io |
| certificate.id | string | a resource identifier |
| certificate.uri | string | a uri for locating a resource |
| certificate\_management\_policy.authority | string | certificate authority to request certificates from. The only supported value is letsencrypt. |
| certificate\_management\_policy.private\_key\_type | string | type of private key to use when requesting certificates. Defaults to rsa, can be either rsa or ecdsa. |
| certificate\_management\_status.renews_at | string | timestamp when the next renewal will be requested, RFC 3339 format |
| certificate\_management\_status.provisioning\_job.error\_code | string | if present, an error code indicating why provisioning is failing. It may be either a temporary condition (INTERNAL\_ERROR), or a permanent one the user must correct (DNS\_ERROR). |
| certificate\_management\_status.provisioning_job.msg | string | a message describing the current status or error |
| certificate\_management\_status.provisioning\_job.started\_at | string | timestamp when the provisioning job started, RFC 3339 format |
| certificate\_management\_status.provisioning\_job.retries\_at | string | timestamp when the provisioning job will be retried |
| acme\_challenge\_cname_target | string | DNS CNAME target for the host _acme-challenge.example.com, where example.com is your reserved domain name. This is required to issue certificates for wildcard, non-ngrok reserved domains. Must be null for non-wildcard domains and ngrok subdomains. |

### Event Destination

#### event\_destination\_created.v0

Triggers when an Event Destination is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | Unique identifier for this Event Destination. |
| metadata | string | Arbitrary user-defined machine-readable data of this Event Destination. Optional, max 4096 bytes. |
| created_at | string | Timestamp when the Event Destination was created, RFC 3339 format. |
| description | string | Human-readable description of the Event Destination. Optional, max 255 bytes. |
| format | string | The output format you would like to serialize events into when sending to their target. Currently the only accepted value is `JSON`. |
| target.firehose.auth.role.role_arn | string | An ARN that specifies the role that ngrok should use to deliver to the configured target. |
| target.firehose.auth.creds.aws\_access\_key_id | string | The ID portion of an AWS access key. |
| target.firehose.auth.creds.aws\_secret\_access_key | string | The secret portion of an AWS access key. |
| target.firehose.delivery\_stream\_arn | string | An Amazon Resource Name specifying the Firehose delivery stream to deposit events into. |
| target.kinesis.auth.role.role_arn | string | An ARN that specifies the role that ngrok should use to deliver to the configured target. |
| target.kinesis.auth.creds.aws\_access\_key_id | string | The ID portion of an AWS access key. |
| target.kinesis.auth.creds.aws\_secret\_access_key | string | The secret portion of an AWS access key. |
| target.kinesis.stream_arn | string | An Amazon Resource Name specifying the Kinesis stream to deposit events into. |
| target.cloudwatch\_logs.auth.role.role\_arn | string | An ARN that specifies the role that ngrok should use to deliver to the configured target. |
| target.cloudwatch\_logs.auth.creds.aws\_access\_key\_id | string | The ID portion of an AWS access key. |
| target.cloudwatch\_logs.auth.creds.aws\_secret\_access\_key | string | The secret portion of an AWS access key. |
| target.cloudwatch\_logs.log\_group_arn | string | An Amazon Resource Name specifying the CloudWatch Logs group to deposit events into. |
| uri | string | URI of the Event Destination API resource. |

#### event\_destination\_deleted.v0

Triggers when an Event Destination is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | Unique identifier for this Event Destination. |
| metadata | string | Arbitrary user-defined machine-readable data of this Event Destination. Optional, max 4096 bytes. |
| created_at | string | Timestamp when the Event Destination was created, RFC 3339 format. |
| description | string | Human-readable description of the Event Destination. Optional, max 255 bytes. |
| format | string | The output format you would like to serialize events into when sending to their target. Currently the only accepted value is `JSON`. |
| target.firehose.auth.role.role_arn | string | An ARN that specifies the role that ngrok should use to deliver to the configured target. |
| target.firehose.auth.creds.aws\_access\_key_id | string | The ID portion of an AWS access key. |
| target.firehose.auth.creds.aws\_secret\_access_key | string | The secret portion of an AWS access key. |
| target.firehose.delivery\_stream\_arn | string | An Amazon Resource Name specifying the Firehose delivery stream to deposit events into. |
| target.kinesis.auth.role.role_arn | string | An ARN that specifies the role that ngrok should use to deliver to the configured target. |
| target.kinesis.auth.creds.aws\_access\_key_id | string | The ID portion of an AWS access key. |
| target.kinesis.auth.creds.aws\_secret\_access_key | string | The secret portion of an AWS access key. |
| target.kinesis.stream_arn | string | An Amazon Resource Name specifying the Kinesis stream to deposit events into. |
| target.cloudwatch\_logs.auth.role.role\_arn | string | An ARN that specifies the role that ngrok should use to deliver to the configured target. |
| target.cloudwatch\_logs.auth.creds.aws\_access\_key\_id | string | The ID portion of an AWS access key. |
| target.cloudwatch\_logs.auth.creds.aws\_secret\_access\_key | string | The secret portion of an AWS access key. |
| target.cloudwatch\_logs.log\_group_arn | string | An Amazon Resource Name specifying the CloudWatch Logs group to deposit events into. |
| uri | string | URI of the Event Destination API resource. |

#### event\_destination\_updated.v0

Triggers when an Event Destination is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | Unique identifier for this Event Destination. |
| metadata | string | Arbitrary user-defined machine-readable data of this Event Destination. Optional, max 4096 bytes. |
| created_at | string | Timestamp when the Event Destination was created, RFC 3339 format. |
| description | string | Human-readable description of the Event Destination. Optional, max 255 bytes. |
| format | string | The output format you would like to serialize events into when sending to their target. Currently the only accepted value is `JSON`. |
| target.firehose.auth.role.role_arn | string | An ARN that specifies the role that ngrok should use to deliver to the configured target. |
| target.firehose.auth.creds.aws\_access\_key_id | string | The ID portion of an AWS access key. |
| target.firehose.auth.creds.aws\_secret\_access_key | string | The secret portion of an AWS access key. |
| target.firehose.delivery\_stream\_arn | string | An Amazon Resource Name specifying the Firehose delivery stream to deposit events into. |
| target.kinesis.auth.role.role_arn | string | An ARN that specifies the role that ngrok should use to deliver to the configured target. |
| target.kinesis.auth.creds.aws\_access\_key_id | string | The ID portion of an AWS access key. |
| target.kinesis.auth.creds.aws\_secret\_access_key | string | The secret portion of an AWS access key. |
| target.kinesis.stream_arn | string | An Amazon Resource Name specifying the Kinesis stream to deposit events into. |
| target.cloudwatch\_logs.auth.role.role\_arn | string | An ARN that specifies the role that ngrok should use to deliver to the configured target. |
| target.cloudwatch\_logs.auth.creds.aws\_access\_key\_id | string | The ID portion of an AWS access key. |
| target.cloudwatch\_logs.auth.creds.aws\_secret\_access\_key | string | The secret portion of an AWS access key. |
| target.cloudwatch\_logs.log\_group_arn | string | An Amazon Resource Name specifying the CloudWatch Logs group to deposit events into. |
| uri | string | URI of the Event Destination API resource. |

### Event Subscription

#### event\_subscription\_created.v0

Triggers when an Event Subscription is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | Unique identifier for this Event Subscription. |
| uri | string | URI of the Event Subscription API resource. |
| created_at | string | When the Event Subscription was created (RFC 3339 format). |
| metadata | string | Arbitrary customer supplied information intended to be machine readable. Optional, max 4096 chars. |
| description | string | Arbitrary customer supplied information intended to be human readable. Optional, max 255 chars. |
| sources.type | string | Type of event for which an event subscription will trigger |
| sources.uri | string | URI of the Event Source API resource. |
| destinations.id | string | a resource identifier |
| destinations.uri | string | a uri for locating a resource |

#### event\_subscription\_deleted.v0

Triggers when an Event Subscription is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | Unique identifier for this Event Subscription. |
| uri | string | URI of the Event Subscription API resource. |
| created_at | string | When the Event Subscription was created (RFC 3339 format). |
| metadata | string | Arbitrary customer supplied information intended to be machine readable. Optional, max 4096 chars. |
| description | string | Arbitrary customer supplied information intended to be human readable. Optional, max 255 chars. |
| sources.type | string | Type of event for which an event subscription will trigger |
| sources.uri | string | URI of the Event Source API resource. |
| destinations.id | string | a resource identifier |
| destinations.uri | string | a uri for locating a resource |

#### event\_subscription\_updated.v0

Triggers when an Event Subscription is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | Unique identifier for this Event Subscription. |
| uri | string | URI of the Event Subscription API resource. |
| created_at | string | When the Event Subscription was created (RFC 3339 format). |
| metadata | string | Arbitrary customer supplied information intended to be machine readable. Optional, max 4096 chars. |
| description | string | Arbitrary customer supplied information intended to be human readable. Optional, max 255 chars. |
| sources.type | string | Type of event for which an event subscription will trigger |
| sources.uri | string | URI of the Event Source API resource. |
| destinations.id | string | a resource identifier |
| destinations.uri | string | a uri for locating a resource |

### HTTP Request Complete

#### http\_request\_complete.v0

Triggers when an HTTP request completes.

This event type supports filters and selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| backend.connection_reused | bool | True if ngrok reused a TCP connection to transmit the HTTP request to the upstream service. |
| basic_auth.decision | string | ‘allow’ if the Basic Auth module permitted the request to the upstream service, otherwise ‘block’ |
| basic_auth.username | string | The username in the HTTP basic auth credentials |
| circuit_breaker.decision | string | Whether the HTTP request was sent to the upstream service. ‘allow’ if the breaker was closed, ‘block’ if the breaker was open, ‘allow\_while\_open’ if the request was allowed while the breaker is open |
| compression.algorithm | string | The compression algorithm used to encode responses from the endpoint. Either ‘gzip’, ‘deflate’, or ‘none’. |
| compression.bytes_saved | int64 | The difference between the size of the raw response and the size of the response as compressed by the Compression Module |
| conn.client_ip | string | filterable | The source IP of the TCP connection to the ngrok edge |
| conn.server_ip | string | filterable | The IP address of the server that received the request |
| conn.server_name | string | filterable | The hostname associated with this connection. |
| conn.server_port | int32 | filterable | The port that the connection for this request came in on |
| conn.start_ts | timestamp | The timestamp when the TCP connection to the ngrok edge is established |
| http.request.body_length | int64 | The size of the request body in bytes |
| http.request.headers | Map&lt;string, List<string&gt;> | A map of normalized headers from the requesting client. Header keys are capitalized and header values are lowercased. |
| http.request.method | string | The request method, normalized to lowercase |
| http.request.url.host | string | The host component of the request URL |
| http.request.url.path | string | The path component of the request URL |
| http.request.url.query | string | The query string component of the request URL |
| http.request.url.raw | string | The full URL of the request including scheme, host, path, and query string |
| http.request.url.scheme | string | The scheme component of the request URL |
| http.request.user_agent | string | The value of the User-Agent header in the request received by ngrok edge |
| http.response.body_length | int64 | The size of the response body in bytes |
| http.response.headers | Map&lt;string, List<string&gt;> | A map of normalized response headers. Header keys are capitalized and header values are lowercased. |
| http.response.status_code | int32 | The status code of the response returned by the ngrok edge |
| ip_policy.decision | string | ‘allow’ if IP Policy module permitted the request to the upstream service, ‘block’ otherwise |
| oauth.app\_client\_id | string | The OAuth application client ID |
| oauth.decision | string | ‘allow’ if the OAuth module permitted the request to the upstream service, ‘block’ otherwise |
| oauth.user.id | string | The authenticated user’s ID returned by the OAuth provider |
| oauth.user.name | string | The authenticated user’s name returned by the OAuth provider |
| tls.cipher_suite | string | The cipher suite selected during the TLS handshake |
| tls.client\_cert.serial\_number | string | The serial number of the client’s leaf TLS certificate in the Mutual TLS handshake |
| tls.client_cert.subject.cn | string | The subject common name of the client’s leaf TLS certificate in the Mutual TLS handshake |
| tls.version | string | The version of the TLS protocol used between the client and the ngrok edge |
| webhook_verification.decision | string | ‘allow’ if the Webhook Verification module permitted the request to the upstream service, ‘block’ otherwise |

### IP Policy

#### ip\_policy\_created.v0

Triggers when an IP Policy is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this IP policy |
| uri | string | URI of the IP Policy API resource |
| created_at | string | timestamp when the IP policy was created, RFC 3339 format |
| description | string | human-readable description of the source IPs of this IP policy. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this IP policy. optional, max 4096 bytes. |


#### ip\_policy\_updated.v0

Triggers when an IP Policy is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this IP policy |
| uri | string | URI of the IP Policy API resource |
| created_at | string | timestamp when the IP policy was created, RFC 3339 format |
| description | string | human-readable description of the source IPs of this IP policy. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this IP policy. optional, max 4096 bytes. |


#### ip\_policy\_deleted.v0

Triggers when an IP Policy is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this IP policy |
| uri | string | URI of the IP Policy API resource |
| created_at | string | timestamp when the IP policy was created, RFC 3339 format |
| description | string | human-readable description of the source IPs of this IP policy. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this IP policy. optional, max 4096 bytes. |

### IP Policy Rule

#### ip\_policy\_rule_created.v0

Triggers when an IP Policy Rule is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this IP policy rule |
| uri | string | URI of the IP policy rule API resource |
| created_at | string | timestamp when the IP policy rule was created, RFC 3339 format |
| description | string | human-readable description of the source IPs of this IP rule. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this IP policy rule. optional, max 4096 bytes. |
| cidr | string | an IP or IP range specified in CIDR notation. IPv4 and IPv6 are both supported. |
| ip_policy.id | string | a resource identifier |
| ip_policy.uri | string | a uri for locating a resource |
| action | string | the action to apply to the policy rule, either `allow` or `deny` |

#### ip\_policy\_rule_deleted.v0

Triggers when an IP Policy Rule is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this IP policy rule |
| uri | string | URI of the IP policy rule API resource |
| created_at | string | timestamp when the IP policy rule was created, RFC 3339 format |
| description | string | human-readable description of the source IPs of this IP rule. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this IP policy rule. optional, max 4096 bytes. |
| cidr | string | an IP or IP range specified in CIDR notation. IPv4 and IPv6 are both supported. |
| ip_policy.id | string | a resource identifier |
| ip_policy.uri | string | a uri for locating a resource |
| action | string | the action to apply to the policy rule, either `allow` or `deny` |

#### ip\_policy\_rule_updated.v0

Triggers when an IP Policy Rule is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this IP policy rule |
| uri | string | URI of the IP policy rule API resource |
| created_at | string | timestamp when the IP policy rule was created, RFC 3339 format |
| description | string | human-readable description of the source IPs of this IP rule. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this IP policy rule. optional, max 4096 bytes. |
| cidr | string | an IP or IP range specified in CIDR notation. IPv4 and IPv6 are both supported. |
| ip_policy.id | string | a resource identifier |
| ip_policy.uri | string | a uri for locating a resource |
| action | string | the action to apply to the policy rule, either `allow` or `deny` |

### IP Restriction

#### ip\_restriction\_created.v0

Triggers when an IP Restriction is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this IP restriction |
| uri | string | URI of the IP restriction API resource |
| created_at | string | timestamp when the IP restriction was created, RFC 3339 format |
| description | string | human-readable description of this IP restriction. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this IP restriction. optional, max 4096 bytes. |
| enforced | boolean | true if the IP restriction will be enforced. if false, only warnings will be issued |
| type | string | the type of IP restriction. this defines what traffic will be restricted with the attached policies. four values are currently supported: `dashboard`, `api`, `agent`, and `endpoints` |
| ip_policies.id | string | a resource identifier |
| ip_policies.uri | string | a uri for locating a resource |

#### ip\_restriction\_deleted.v0

Triggers when an IP Restriction is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this IP restriction |
| uri | string | URI of the IP restriction API resource |
| created_at | string | timestamp when the IP restriction was created, RFC 3339 format |
| description | string | human-readable description of this IP restriction. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this IP restriction. optional, max 4096 bytes. |
| enforced | boolean | true if the IP restriction will be enforced. if false, only warnings will be issued |
| type | string | the type of IP restriction. this defines what traffic will be restricted with the attached policies. four values are currently supported: `dashboard`, `api`, `agent`, and `endpoints` |
| ip_policies.id | string | a resource identifier |
| ip_policies.uri | string | a uri for locating a resource |

#### ip\_restriction\_updated.v0

Triggers when an IP Restriction is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this IP restriction |
| uri | string | URI of the IP restriction API resource |
| created_at | string | timestamp when the IP restriction was created, RFC 3339 format |
| description | string | human-readable description of this IP restriction. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this IP restriction. optional, max 4096 bytes. |
| enforced | boolean | true if the IP restriction will be enforced. if false, only warnings will be issued |
| type | string | the type of IP restriction. this defines what traffic will be restricted with the attached policies. four values are currently supported: `dashboard`, `api`, `agent`, and `endpoints` |
| ip_policies.id | string | a resource identifier |
| ip_policies.uri | string | a uri for locating a resource |

### SSH Certificate Authority

#### ssh\_certificate\_authority_created.v0

Triggers when an SSH certificate authority is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this SSH Certificate Authority |
| uri | string | URI of the SSH Certificate Authority API resource |
| created_at | string | timestamp when the SSH Certificate Authority API resource was created, RFC 3339 format |
| description | string | human-readable description of this SSH Certificate Authority. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this SSH Certificate Authority. optional, max 4096 bytes. |
| public_key | string | raw public key for this SSH Certificate Authority |
| key_type | string | the type of private key for this SSH Certificate Authority |

#### ssh\_certificate\_authority_deleted.v0

Triggers when an SSH certificate authority is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this SSH Certificate Authority |
| uri | string | URI of the SSH Certificate Authority API resource |
| created_at | string | timestamp when the SSH Certificate Authority API resource was created, RFC 3339 format |
| description | string | human-readable description of this SSH Certificate Authority. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this SSH Certificate Authority. optional, max 4096 bytes. |
| public_key | string | raw public key for this SSH Certificate Authority |
| key_type | string | the type of private key for this SSH Certificate Authority |

#### ssh\_certificate\_authority_updated.v0

Triggers when an SSH certificate authority is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this SSH Certificate Authority |
| uri | string | URI of the SSH Certificate Authority API resource |
| created_at | string | timestamp when the SSH Certificate Authority API resource was created, RFC 3339 format |
| description | string | human-readable description of this SSH Certificate Authority. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this SSH Certificate Authority. optional, max 4096 bytes. |
| public_key | string | raw public key for this SSH Certificate Authority |
| key_type | string | the type of private key for this SSH Certificate Authority |


### SSH Host Certificate

#### ssh\_host\_certificate_created.v0

Triggers when an SSH host certificate is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this SSH Host Certificate |
| uri | string | URI of the SSH Host Certificate API resource |
| created_at | string | timestamp when the SSH Host Certificate API resource was created, RFC 3339 format |
| description | string | human-readable description of this SSH Host Certificate. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this SSH Host Certificate. optional, max 4096 bytes. |
| public_key | string | a public key in OpenSSH Authorized Keys format that this certificate signs |
| key_type | string | the key type of the `public_key`, one of `rsa`, `ecdsa` or `ed25519` |
| ssh\_certificate\_authority_id | string | the ssh certificate authority that is used to sign this ssh host certificate |
| principals | List&lt;string&gt; | the list of principals included in the ssh host certificate. This is the list of hostnames and/or IP addresses that are authorized to serve SSH traffic with this certificate. Dangerously, if no principals are specified, this certificate is considered valid for all hosts. |
| valid_after | string | the time when the ssh host certificate becomes valid, in RFC 3339 format. |
| valid_until | string | the time after which the ssh host certificate becomes invalid, in RFC 3339 format. the OpenSSH certificates RFC calls this `valid_before`. |
| certificate | string | the signed SSH certificate in OpenSSH Authorized Keys format. this value should be placed in a `-cert.pub` certificate file on disk that should be referenced in your `sshd_config` configuration file with a `HostCertificate` directive |

#### ssh\_host\_certificate_deleted.v0

Triggers when an SSH host certificate is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this SSH Host Certificate |
| uri | string | URI of the SSH Host Certificate API resource |
| created_at | string | timestamp when the SSH Host Certificate API resource was created, RFC 3339 format |
| description | string | human-readable description of this SSH Host Certificate. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this SSH Host Certificate. optional, max 4096 bytes. |
| public_key | string | a public key in OpenSSH Authorized Keys format that this certificate signs |
| key_type | string | the key type of the `public_key`, one of `rsa`, `ecdsa` or `ed25519` |
| ssh\_certificate\_authority_id | string | the ssh certificate authority that is used to sign this ssh host certificate |
| principals | List&lt;string&gt; | the list of principals included in the ssh host certificate. This is the list of hostnames and/or IP addresses that are authorized to serve SSH traffic with this certificate. Dangerously, if no principals are specified, this certificate is considered valid for all hosts. |
| valid_after | string | the time when the ssh host certificate becomes valid, in RFC 3339 format. |
| valid_until | string | the time after which the ssh host certificate becomes invalid, in RFC 3339 format. the OpenSSH certificates RFC calls this `valid_before`. |
| certificate | string | the signed SSH certificate in OpenSSH Authorized Keys format. this value should be placed in a `-cert.pub` certificate file on disk that should be referenced in your `sshd_config` configuration file with a `HostCertificate` directive |

#### ssh\_host\_certificate_updated.v0

Triggers when an SSH host certificate is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this SSH Host Certificate |
| uri | string | URI of the SSH Host Certificate API resource |
| created_at | string | timestamp when the SSH Host Certificate API resource was created, RFC 3339 format |
| description | string | human-readable description of this SSH Host Certificate. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this SSH Host Certificate. optional, max 4096 bytes. |
| public_key | string | a public key in OpenSSH Authorized Keys format that this certificate signs |
| key_type | string | the key type of the `public_key`, one of `rsa`, `ecdsa` or `ed25519` |
| ssh\_certificate\_authority_id | string | the ssh certificate authority that is used to sign this ssh host certificate |
| principals | List&lt;string&gt; | the list of principals included in the ssh host certificate. This is the list of hostnames and/or IP addresses that are authorized to serve SSH traffic with this certificate. Dangerously, if no principals are specified, this certificate is considered valid for all hosts. |
| valid_after | string | the time when the ssh host certificate becomes valid, in RFC 3339 format. |
| valid_until | string | the time after which the ssh host certificate becomes invalid, in RFC 3339 format. the OpenSSH certificates RFC calls this `valid_before`. |
| certificate | string | the signed SSH certificate in OpenSSH Authorized Keys format. this value should be placed in a `-cert.pub` certificate file on disk that should be referenced in your `sshd_config` configuration file with a `HostCertificate` directive |


### SSH Public Key

#### ssh\_public\_key_created.v0

Triggers when an SSH public key is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique ssh credential resource identifier |
| uri | string | URI of the ssh credential API resource |
| created_at | string | timestamp when the ssh credential was created, RFC 3339 format |
| description | string | human-readable description of who or what will use the ssh credential to authenticate. Optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this ssh credential. Optional, max 4096 bytes. |
| public_key | string | the PEM-encoded public key of the SSH keypair that will be used to authenticate |
| acl | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains and addresses the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |

#### ssh\_public\_key_deleted.v0

Triggers when an SSH public key is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique ssh credential resource identifier |
| uri | string | URI of the ssh credential API resource |
| created_at | string | timestamp when the ssh credential was created, RFC 3339 format |
| description | string | human-readable description of who or what will use the ssh credential to authenticate. Optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this ssh credential. Optional, max 4096 bytes. |
| public_key | string | the PEM-encoded public key of the SSH keypair that will be used to authenticate |
| acl | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains and addresses the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |

#### ssh\_public\_key_updated.v0

Triggers when an SSH public key is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique ssh credential resource identifier |
| uri | string | URI of the ssh credential API resource |
| created_at | string | timestamp when the ssh credential was created, RFC 3339 format |
| description | string | human-readable description of who or what will use the ssh credential to authenticate. Optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this ssh credential. Optional, max 4096 bytes. |
| public_key | string | the PEM-encoded public key of the SSH keypair that will be used to authenticate |
| acl | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains and addresses the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |


### SSH User Certificate

#### ssh\_user\_certificate_created.v0

Triggers when an SSH user certificate is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this SSH User Certificate |
| uri | string | URI of the SSH User Certificate API resource |
| created_at | string | timestamp when the SSH User Certificate API resource was created, RFC 3339 format |
| description | string | human-readable description of this SSH User Certificate. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this SSH User Certificate. optional, max 4096 bytes. |
| public_key | string | a public key in OpenSSH Authorized Keys format that this certificate signs |
| key_type | string | the key type of the `public_key`, one of `rsa`, `ecdsa` or `ed25519` |
| ssh\_certificate\_authority_id | string | the ssh certificate authority that is used to sign this ssh user certificate |
| principals | List&lt;string&gt; | the list of principals included in the ssh user certificate. This is the list of usernames that the certificate holder may sign in as on a machine authorizing the signing certificate authority. Dangerously, if no principals are specified, this certificate may be used to log in as any user. |
| critical_options | Map&lt;string, string&gt; | A map of critical options included in the certificate. Only two critical options are currently defined by OpenSSH: `force-command` and `source-address`. See [the OpenSSH certificate protocol spec](https://github.com/openssh/openssh-portable/blob/master/PROTOCOL.certkeys) for additional details. |
| extensions | Map&lt;string, string&gt; | A map of extensions included in the certificate. Extensions are additional metadata that can be interpreted by the SSH server for any purpose. These can be used to permit or deny the ability to open a terminal, do port forwarding, x11 forwarding, and more. If unspecified, the certificate will include limited permissions with the following extension map: `{"permit-pty": "", "permit-user-rc": ""}` OpenSSH understands a number of predefined extensions. See [the OpenSSH certificate protocol spec](https://github.com/openssh/openssh-portable/blob/master/PROTOCOL.certkeys) for additional details. |
| valid_after | string | the time when the ssh host certificate becomes valid, in RFC 3339 format. |
| valid_until | string | the time after which the ssh host certificate becomes invalid, in RFC 3339 format. the OpenSSH certificates RFC calls this `valid_before`. |
| certificate | string | the signed SSH certificate in OpenSSH Authorized Keys Format. this value should be placed in a `-cert.pub` certificate file on disk that should be referenced in your `sshd_config` configuration file with a `HostCertificate` directive |

#### ssh\_user\_certificate_deleted.v0

Triggers when an SSH user certificate is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this SSH User Certificate |
| uri | string | URI of the SSH User Certificate API resource |
| created_at | string | timestamp when the SSH User Certificate API resource was created, RFC 3339 format |
| description | string | human-readable description of this SSH User Certificate. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this SSH User Certificate. optional, max 4096 bytes. |
| public_key | string | a public key in OpenSSH Authorized Keys format that this certificate signs |
| key_type | string | the key type of the `public_key`, one of `rsa`, `ecdsa` or `ed25519` |
| ssh\_certificate\_authority_id | string | the ssh certificate authority that is used to sign this ssh user certificate |
| principals | List&lt;string&gt; | the list of principals included in the ssh user certificate. This is the list of usernames that the certificate holder may sign in as on a machine authorizing the signing certificate authority. Dangerously, if no principals are specified, this certificate may be used to log in as any user. |
| critical_options | Map&lt;string, string&gt; | A map of critical options included in the certificate. Only two critical options are currently defined by OpenSSH: `force-command` and `source-address`. See [the OpenSSH certificate protocol spec](https://github.com/openssh/openssh-portable/blob/master/PROTOCOL.certkeys) for additional details. |
| extensions | Map&lt;string, string&gt; | A map of extensions included in the certificate. Extensions are additional metadata that can be interpreted by the SSH server for any purpose. These can be used to permit or deny the ability to open a terminal, do port forwarding, x11 forwarding, and more. If unspecified, the certificate will include limited permissions with the following extension map: `{"permit-pty": "", "permit-user-rc": ""}` OpenSSH understands a number of predefined extensions. See [the OpenSSH certificate protocol spec](https://github.com/openssh/openssh-portable/blob/master/PROTOCOL.certkeys) for additional details. |
| valid_after | string | the time when the ssh host certificate becomes valid, in RFC 3339 format. |
| valid_until | string | the time after which the ssh host certificate becomes invalid, in RFC 3339 format. the OpenSSH certificates RFC calls this `valid_before`. |
| certificate | string | the signed SSH certificate in OpenSSH Authorized Keys Format. this value should be placed in a `-cert.pub` certificate file on disk that should be referenced in your `sshd_config` configuration file with a `HostCertificate` directive |

#### ssh\_user\_certificate_updated.v0

Triggers when an SSH user certificate is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this SSH User Certificate |
| uri | string | URI of the SSH User Certificate API resource |
| created_at | string | timestamp when the SSH User Certificate API resource was created, RFC 3339 format |
| description | string | human-readable description of this SSH User Certificate. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this SSH User Certificate. optional, max 4096 bytes. |
| public_key | string | a public key in OpenSSH Authorized Keys format that this certificate signs |
| key_type | string | the key type of the `public_key`, one of `rsa`, `ecdsa` or `ed25519` |
| ssh\_certificate\_authority_id | string | the ssh certificate authority that is used to sign this ssh user certificate |
| principals | List&lt;string&gt; | the list of principals included in the ssh user certificate. This is the list of usernames that the certificate holder may sign in as on a machine authorizing the signing certificate authority. Dangerously, if no principals are specified, this certificate may be used to log in as any user. |
| critical_options | Map&lt;string, string&gt; | A map of critical options included in the certificate. Only two critical options are currently defined by OpenSSH: `force-command` and `source-address`. See [the OpenSSH certificate protocol spec](https://github.com/openssh/openssh-portable/blob/master/PROTOCOL.certkeys) for additional details. |
| extensions | Map&lt;string, string&gt; | A map of extensions included in the certificate. Extensions are additional metadata that can be interpreted by the SSH server for any purpose. These can be used to permit or deny the ability to open a terminal, do port forwarding, x11 forwarding, and more. If unspecified, the certificate will include limited permissions with the following extension map: `{"permit-pty": "", "permit-user-rc": ""}` OpenSSH understands a number of predefined extensions. See [the OpenSSH certificate protocol spec](https://github.com/openssh/openssh-portable/blob/master/PROTOCOL.certkeys) for additional details. |
| valid_after | string | the time when the ssh host certificate becomes valid, in RFC 3339 format. |
| valid_until | string | the time after which the ssh host certificate becomes invalid, in RFC 3339 format. the OpenSSH certificates RFC calls this `valid_before`. |
| certificate | string | the signed SSH certificate in OpenSSH Authorized Keys Format. this value should be placed in a `-cert.pub` certificate file on disk that should be referenced in your `sshd_config` configuration file with a `HostCertificate` directive |


### TCP Address

#### tcp\_address\_created.v0

Triggers when a TCP address is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique reserved address resource identifier |
| uri | string | URI of the reserved address API resource |
| created_at | string | timestamp when the reserved address was created, RFC 3339 format |
| description | string | human-readable description of what this reserved address will be used for |
| metadata | string | arbitrary user-defined machine-readable data of this reserved address. Optional, max 4096 bytes. |
| addr | string | hostname:port of the reserved address that was assigned at creation time |
| region | string | reserve the address in this geographic ngrok datacenter. Optional, default is us. (au, eu, ap, us, jp, in, sa) |

#### tcp\_address\_deleted.v0

Triggers when a TCP address is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique reserved address resource identifier |
| uri | string | URI of the reserved address API resource |
| created_at | string | timestamp when the reserved address was created, RFC 3339 format |
| description | string | human-readable description of what this reserved address will be used for |
| metadata | string | arbitrary user-defined machine-readable data of this reserved address. Optional, max 4096 bytes. |
| addr | string | hostname:port of the reserved address that was assigned at creation time |
| region | string | reserve the address in this geographic ngrok datacenter. Optional, default is us. (au, eu, ap, us, jp, in, sa) |

#### tcp\_address\_updated.v0

Triggers when a TCP address is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique reserved address resource identifier |
| uri | string | URI of the reserved address API resource |
| created_at | string | timestamp when the reserved address was created, RFC 3339 format |
| description | string | human-readable description of what this reserved address will be used for |
| metadata | string | arbitrary user-defined machine-readable data of this reserved address. Optional, max 4096 bytes. |
| addr | string | hostname:port of the reserved address that was assigned at creation time |
| region | string | reserve the address in this geographic ngrok datacenter. Optional, default is us. (au, eu, ap, us, jp, in, sa) |


### TCP Connection Closed

#### tcp\_connection\_closed.v0

Triggers when a TCP connection to an endpoint closes.

This event type supports filters and selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| conn.bytes_in | int64 | The number of bytes arriving at an endpoint from the frontend |
| conn.bytes_out | int64 | The number of bytes leaving an endpoint to the frontend |
| conn.client_ip | string | filterable | The source IP of the TCP connection to the ngrok edge |
| conn.end_ts | timestamp | The timestamp when the TCP connection to the ngrok edge is closed |
| conn.server_ip | string | filterable | The IP address of the server that received the request |
| conn.server_name | string | filterable | The hostname associated with this connection. |
| conn.server_port | int32 | filterable | The port that the connection for this request came in on |
| conn.start_ts | timestamp | The timestamp when the TCP connection to the ngrok edge is established |
| ip_policy.decision | string | ‘allow’ if IP Policy module permitted the request to the upstream service, ‘block’ otherwise |


### TLS Certificate

#### tls\_certificate\_created.v0

Triggers when a TLS certificate is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this TLS certificate |
| uri | string | URI of the TLS certificate API resource |
| created_at | string | timestamp when the TLS certificate was created, RFC 3339 format |
| description | string | human-readable description of this TLS certificate. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this TLS certificate. optional, max 4096 bytes. |
| certificate_pem | string | chain of PEM-encoded certificates, leaf first. See [Certificate Bundles](https://ngrok.com/docs/api#tls-certificates-pem). |
| subject\_common\_name | string | subject common name from the leaf of this TLS certificate |
| subject\_alternative\_names.dns_names | List&lt;string&gt; | set of additional domains (including wildcards) this TLS certificate is valid for |
| subject\_alternative\_names.ips | List&lt;string&gt; | set of IP addresses this TLS certificate is also valid for |
| issued_at | string | timestamp (in RFC 3339 format) when this TLS certificate was issued automatically, or null if this certificate was user-uploaded |
| not_before | string | timestamp when this TLS certificate becomes valid, RFC 3339 format |
| not_after | string | timestamp when this TLS certificate becomes invalid, RFC 3339 format |
| key_usages | List&lt;string&gt; | set of actions the private key of this TLS certificate can be used for |
| extended\_key\_usages | List&lt;string&gt; | extended set of actions the private key of this TLS certificate can be used for |
| private\_key\_type | string | type of the private key of this TLS certificate. One of rsa, ecdsa, or ed25519. |
| issuer\_common\_name | string | issuer common name from the leaf of this TLS certificate |
| serial_number | string | serial number of the leaf of this TLS certificate |
| subject_organization | string | subject organization from the leaf of this TLS certificate |
| subject\_organizational\_unit | string | subject organizational unit from the leaf of this TLS certificate |
| subject_locality | string | subject locality from the leaf of this TLS certificate |
| subject_province | string | subject province from the leaf of this TLS certificate |
| subject_country | string | subject country from the leaf of this TLS certificate |

#### tls\_certificate\_deleted.v0

Triggers when a TLS certificate is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this TLS certificate |
| uri | string | URI of the TLS certificate API resource |
| created_at | string | timestamp when the TLS certificate was created, RFC 3339 format |
| description | string | human-readable description of this TLS certificate. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this TLS certificate. optional, max 4096 bytes. |
| certificate_pem | string | chain of PEM-encoded certificates, leaf first. See [Certificate Bundles](https://ngrok.com/docs/api#tls-certificates-pem). |
| subject\_common\_name | string | subject common name from the leaf of this TLS certificate |
| subject\_alternative\_names.dns_names | List&lt;string&gt; | set of additional domains (including wildcards) this TLS certificate is valid for |
| subject\_alternative\_names.ips | List&lt;string&gt; | set of IP addresses this TLS certificate is also valid for |
| issued_at | string | timestamp (in RFC 3339 format) when this TLS certificate was issued automatically, or null if this certificate was user-uploaded |
| not_before | string | timestamp when this TLS certificate becomes valid, RFC 3339 format |
| not_after | string | timestamp when this TLS certificate becomes invalid, RFC 3339 format |
| key_usages | List&lt;string&gt; | set of actions the private key of this TLS certificate can be used for |
| extended\_key\_usages | List&lt;string&gt; | extended set of actions the private key of this TLS certificate can be used for |
| private\_key\_type | string | type of the private key of this TLS certificate. One of rsa, ecdsa, or ed25519. |
| issuer\_common\_name | string | issuer common name from the leaf of this TLS certificate |
| serial_number | string | serial number of the leaf of this TLS certificate |
| subject_organization | string | subject organization from the leaf of this TLS certificate |
| subject\_organizational\_unit | string | subject organizational unit from the leaf of this TLS certificate |
| subject_locality | string | subject locality from the leaf of this TLS certificate |
| subject_province | string | subject province from the leaf of this TLS certificate |
| subject_country | string | subject country from the leaf of this TLS certificate |

#### tls\_certificate\_updated.v0

Triggers when a TLS certificate is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique identifier for this TLS certificate |
| uri | string | URI of the TLS certificate API resource |
| created_at | string | timestamp when the TLS certificate was created, RFC 3339 format |
| description | string | human-readable description of this TLS certificate. optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this TLS certificate. optional, max 4096 bytes. |
| certificate_pem | string | chain of PEM-encoded certificates, leaf first. See [Certificate Bundles](https://ngrok.com/docs/api#tls-certificates-pem). |
| subject\_common\_name | string | subject common name from the leaf of this TLS certificate |
| subject\_alternative\_names.dns_names | List&lt;string&gt; | set of additional domains (including wildcards) this TLS certificate is valid for |
| subject\_alternative\_names.ips | List&lt;string&gt; | set of IP addresses this TLS certificate is also valid for |
| issued_at | string | timestamp (in RFC 3339 format) when this TLS certificate was issued automatically, or null if this certificate was user-uploaded |
| not_before | string | timestamp when this TLS certificate becomes valid, RFC 3339 format |
| not_after | string | timestamp when this TLS certificate becomes invalid, RFC 3339 format |
| key_usages | List&lt;string&gt; | set of actions the private key of this TLS certificate can be used for |
| extended\_key\_usages | List&lt;string&gt; | extended set of actions the private key of this TLS certificate can be used for |
| private\_key\_type | string | type of the private key of this TLS certificate. One of rsa, ecdsa, or ed25519. |
| issuer\_common\_name | string | issuer common name from the leaf of this TLS certificate |
| serial_number | string | serial number of the leaf of this TLS certificate |
| subject_organization | string | subject organization from the leaf of this TLS certificate |
| subject\_organizational\_unit | string | subject organizational unit from the leaf of this TLS certificate |
| subject_locality | string | subject locality from the leaf of this TLS certificate |
| subject_province | string | subject province from the leaf of this TLS certificate |
| subject_country | string | subject country from the leaf of this TLS certificate |


### Tunnel Credential

#### tunnel\_credential\_created.v0

Triggers when a tunnel credential is created

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique tunnel credential resource identifier |
| uri | string | URI of the tunnel credential API resource |
| created_at | string | timestamp when the tunnel credential was created, RFC 3339 format |
| description | string | human-readable description of who or what will use the credential to authenticate. Optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this credential. Optional, max 4096 bytes. |
| token | string | the credential’s authtoken that can be used to authenticate an ngrok agent. **This value is only available one time, on the API response from credential creation, otherwise it is null.** |
| acl | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains and addresses the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |

#### tunnel\_credential\_deleted.v0

Triggers when a tunnel credential is deleted

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique tunnel credential resource identifier |
| uri | string | URI of the tunnel credential API resource |
| created_at | string | timestamp when the tunnel credential was created, RFC 3339 format |
| description | string | human-readable description of who or what will use the credential to authenticate. Optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this credential. Optional, max 4096 bytes. |
| token | string | the credential’s authtoken that can be used to authenticate an ngrok agent. **This value is only available one time, on the API response from credential creation, otherwise it is null.** |
| acl | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains and addresses the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |

#### tunnel\_credential\_updated.v0

Triggers when a tunnel credential is updated

This event type does not support filters or selectable fields.

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| id  | string | unique tunnel credential resource identifier |
| uri | string | URI of the tunnel credential API resource |
| created_at | string | timestamp when the tunnel credential was created, RFC 3339 format |
| description | string | human-readable description of who or what will use the credential to authenticate. Optional, max 255 bytes. |
| metadata | string | arbitrary user-defined machine-readable data of this credential. Optional, max 4096 bytes. |
| token | string | the credential’s authtoken that can be used to authenticate an ngrok agent. **This value is only available one time, on the API response from credential creation, otherwise it is null.** |
| acl | List&lt;string&gt; | optional list of ACL rules. If unspecified, the credential will have no restrictions. The only allowed ACL rule at this time is the `bind` rule. The `bind` rule allows the caller to restrict what domains and addresses the token is allowed to bind. For example, to allow the token to open a tunnel on example.ngrok.io your ACL would include the rule `bind:example.ngrok.io`. Bind rules may specify a leading wildcard to match multiple domains with a common suffix. For example, you may specify a rule of `bind:*.example.com` which will allow `x.example.com`, `y.example.com`, `*.example.com`, etc. A rule of `'*'` is equivalent to no acl at all and will explicitly permit all actions. |