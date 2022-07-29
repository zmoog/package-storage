# Palo Alto Cortex XDR Integration

The PANW XDR integration collects alerts with multiple events from the [Cortex XDR API,](https://docs.paloaltonetworks.com/cortex/cortex-xdr/cortex-xdr-api/cortex-xdr-apis/incident-management/get-alerts).

## Logs

### Alerts

The Cortex XDR Alerts API is used to retrieve alerts generated by Cortex XDR based on raw endpoint data. A single alert might include one or more local endpoint events, each event generating its own document on Elasticsearch.

The Palo Alto XDR integration requires both an API key and API key ID, both which can be retrieved from the Cortex XDR UI. See: [Get Started with Cortex XDR API](https://docs.paloaltonetworks.com/cortex/cortex-xdr/cortex-xdr-api/cortex-xdr-api-overview/get-started-with-cortex-xdr-apis.html)

An example event for `alerts` looks as following:

```json
{
    "@timestamp": "2020-10-21T11:31:28.980Z",
    "agent": {
        "ephemeral_id": "a7da9a06-658a-4f11-a037-4f3c5009996a",
        "id": "b1d83907-ff3e-464a-b79a-cf843f6f0bba",
        "name": "docker-fleet-agent",
        "type": "filebeat",
        "version": "8.0.0-beta1"
    },
    "data_stream": {
        "dataset": "panw_cortex_xdr.alerts",
        "namespace": "ep",
        "type": "logs"
    },
    "ecs": {
        "version": "8.2.0"
    },
    "elastic_agent": {
        "id": "b1d83907-ff3e-464a-b79a-cf843f6f0bba",
        "snapshot": false,
        "version": "8.0.0-beta1"
    },
    "event": {
        "action": "BLOCKED",
        "agent_id_status": "verified",
        "category": [
            "malware"
        ],
        "created": "2020-10-21T11:31:28.980Z",
        "dataset": "panw_cortex_xdr.alerts",
        "id": "800800",
        "ingested": "2022-01-02T08:57:33Z",
        "kind": "alert",
        "original": "{\"action\":\"BLOCKED\",\"action_pretty\":\"Prevented (Blocked)\",\"agent_data_collection_status\":true,\"agent_device_domain\":null,\"agent_fqdn\":\"test\",\"agent_is_vdi\":null,\"agent_os_sub_type\":\"XP\",\"agent_os_type\":\"Windows\",\"agent_version\":\"1.2.3.4\",\"alert_id\":\"1001\",\"attempt_counter\":55,\"bioc_category_enum_key\":null,\"bioc_indicator\":null,\"category\":\"Exploit\",\"deduplicate_tokens\":null,\"description\":\"Local privilege escalation prevented\",\"detection_timestamp\":1603279888980,\"end_match_attempt_ts\":1603552062824,\"endpoint_id\":\"12345678\",\"events\":{\"action_country\":\"UNKNOWN\",\"action_external_hostname\":null,\"action_file_macro_sha256\":null,\"action_file_md5\":null,\"action_file_name\":null,\"action_file_path\":null,\"action_file_sha256\":null,\"action_local_ip\":null,\"action_local_port\":null,\"action_process_causality_id\":null,\"action_process_image_command_line\":null,\"action_process_image_name\":null,\"action_process_image_sha256\":null,\"action_process_instance_id\":null,\"action_process_signature_status\":\"N/A\",\"action_process_signature_vendor\":null,\"action_registry_data\":null,\"action_registry_full_key\":null,\"action_registry_key_name\":null,\"action_registry_value_name\":null,\"action_remote_ip\":null,\"action_remote_port\":null,\"actor_causality_id\":null,\"actor_process_causality_id\":null,\"actor_process_command_line\":\"c:\\\\tmp\\\\virus.exe\",\"actor_process_image_md5\":null,\"actor_process_image_name\":\"virus.exe\",\"actor_process_image_path\":\"c:\\\\tmp\\\\virus.exe\",\"actor_process_image_sha256\":\"133ee989293f92736301280c6f14c89d521200c17dcdcecca30cd20705332d44\",\"actor_process_instance_id\":\"1234\",\"actor_process_os_pid\":1234,\"actor_process_signature_status\":\"N/A\",\"actor_process_signature_vendor\":null,\"actor_thread_thread_id\":null,\"agent_host_boot_time\":null,\"agent_install_type\":\"NA\",\"association_strength\":null,\"causality_actor_causality_id\":null,\"causality_actor_process_command_line\":null,\"causality_actor_process_execution_time\":null,\"causality_actor_process_image_md5\":null,\"causality_actor_process_image_name\":null,\"causality_actor_process_image_path\":null,\"causality_actor_process_image_sha256\":null,\"causality_actor_process_signature_status\":\"N/A\",\"causality_actor_process_signature_vendor\":null,\"dns_query_name\":null,\"dst_action_country\":null,\"dst_action_external_hostname\":null,\"dst_action_external_port\":null,\"dst_agent_id\":null,\"dst_association_strength\":null,\"dst_causality_actor_process_execution_time\":null,\"event_id\":null,\"event_sub_type\":null,\"event_timestamp\":1603279888980,\"event_type\":\"Process Execution\",\"fw_app_category\":null,\"fw_app_id\":null,\"fw_app_subcategory\":null,\"fw_app_technology\":null,\"fw_device_name\":null,\"fw_email_recipient\":null,\"fw_email_sender\":null,\"fw_email_subject\":null,\"fw_interface_from\":null,\"fw_interface_to\":null,\"fw_is_phishing\":\"N/A\",\"fw_misc\":null,\"fw_rule\":null,\"fw_rule_id\":null,\"fw_serial_number\":null,\"fw_url_domain\":null,\"fw_vsys\":null,\"fw_xff\":null,\"module_id\":\"Privilege Escalation Protection\",\"os_actor_causality_id\":null,\"os_actor_effective_username\":null,\"os_actor_process_causality_id\":null,\"os_actor_process_command_line\":null,\"os_actor_process_image_name\":null,\"os_actor_process_image_path\":null,\"os_actor_process_image_sha256\":null,\"os_actor_process_instance_id\":null,\"os_actor_process_os_pid\":null,\"os_actor_process_signature_status\":\"N/A\",\"os_actor_process_signature_vendor\":null,\"os_actor_thread_thread_id\":null,\"story_id\":null,\"user_name\":null},\"external_id\":\"800800\",\"filter_rule_id\":null,\"host_ip\":[\"10.0.255.20\"],\"host_name\":\"Test\",\"is_whitelisted\":false,\"local_insert_ts\":1603279967500,\"mac\":null,\"mac_address\":[\"00:11:22:33:44:55\"],\"matching_service_rule_id\":null,\"matching_status\":\"FAILED\",\"mitre_tactic_id_and_name\":[\"\"],\"mitre_technique_id_and_name\":[\"\"],\"name\":\"Kernel Privilege Escalation\",\"severity\":\"high\",\"source\":\"XDR Agent\",\"starred\":false}",
        "reason": "Local privilege escalation prevented",
        "severity": 4,
        "type": [
            "info"
        ]
    },
    "host": {
        "hostname": "test",
        "id": "12345678",
        "ip": [
            "10.0.255.20"
        ],
        "name": "test",
        "os": {
            "name": "Windows",
            "version": "XP"
        }
    },
    "input": {
        "type": "httpjson"
    },
    "message": "Kernel Privilege Escalation",
    "panw_cortex": {
        "xdr": {
            "action_pretty": "Prevented (Blocked)",
            "agent_data_collection_status": true,
            "agent_version": "1.2.3.4",
            "alert_id": "1001",
            "attempt_counter": 55,
            "category": "Exploit",
            "end_match_attempt_ts": "2020-10-24T15:07:42.824Z",
            "events": {
                "actor_process_signature_status": "N/A",
                "agent_install_type": "NA",
                "event_type": "Process Execution",
                "fw_is_phishing": "N/A",
                "module_id": "Privilege Escalation Protection",
                "os_actor_process_signature_status": "N/A"
            },
            "is_whitelisted": false,
            "local_insert_ts": "2020-10-21T11:32:47.500Z",
            "mac_address": [
                "00:11:22:33:44:55"
            ],
            "matching_status": "FAILED",
            "source": "XDR Agent",
            "starred": false
        }
    },
    "process": {
        "code_signature": {
            "status": "N/A"
        },
        "command_line": "c:\\tmp\\virus.exe",
        "entity_id": "1234",
        "executable": "c:\\tmp\\virus.exe",
        "hash": {
            "sha256": "133ee989293f92736301280c6f14c89d521200c17dcdcecca30cd20705332d44"
        },
        "name": "virus.exe",
        "parent": {
            "code_signature": {
                "status": "N/A"
            }
        },
        "pid": 1234
    },
    "related": {
        "hash": [
            "133ee989293f92736301280c6f14c89d521200c17dcdcecca30cd20705332d44"
        ]
    },
    "tags": [
        "preserve_original_event",
        "forwarded",
        "panw_cortex_xdr"
    ]
}
```

**Exported fields**

| Field | Description | Type |
|---|---|---|
| @timestamp | Event timestamp. | date |
| cloud.account.id | The cloud account or organization id used to identify different entities in a multi-tenant environment. Examples: AWS account id, Google Cloud ORG Id, or other unique identifier. | keyword |
| cloud.availability_zone | Availability zone in which this host is running. | keyword |
| cloud.image.id | Image ID for the cloud instance. | keyword |
| cloud.instance.id | Instance ID of the host machine. | keyword |
| cloud.instance.name | Instance name of the host machine. | keyword |
| cloud.machine.type | Machine type of the host machine. | keyword |
| cloud.project.id | Name of the project in Google Cloud. | keyword |
| cloud.provider | Name of the cloud provider. Example values are aws, azure, gcp, or digitalocean. | keyword |
| cloud.region | Region in which this host is running. | keyword |
| container.id | Unique container id. | keyword |
| container.image.name | Name of the image the container was built on. | keyword |
| container.labels | Image labels. | object |
| container.name | Container name. | keyword |
| data_stream.dataset | Data stream dataset name. | constant_keyword |
| data_stream.namespace | Data stream namespace. | constant_keyword |
| data_stream.type | Data stream type. | constant_keyword |
| destination.as.number | Unique number allocated to the autonomous system. The autonomous system number (ASN) uniquely identifies each network on the Internet. | long |
| destination.as.organization.name | Organization name. | keyword |
| destination.as.organization.name.text | Multi-field of `destination.as.organization.name`. | match_only_text |
| destination.geo.city_name | City name. | keyword |
| destination.geo.continent_name | Name of the continent. | keyword |
| destination.geo.country_iso_code | Country ISO code. | keyword |
| destination.geo.country_name | Country name. | keyword |
| destination.geo.location | Longitude and latitude. | geo_point |
| destination.geo.region_iso_code | Region ISO code. | keyword |
| destination.geo.region_name | Region name. | keyword |
| destination.ip | IP address of the destination (IPv4 or IPv6). | ip |
| destination.port | Port of the destination. | long |
| dns.question.name | The name being queried. If the name field contains non-printable characters (below 32 or above 126), those characters should be represented as escaped base 10 integers (\DDD). Back slashes and quotes should be escaped. Tabs, carriage returns, and line feeds should be converted to \t, \r, and \n respectively. | keyword |
| ecs.version | ECS version this event conforms to. `ecs.version` is a required field and must exist in all events. When querying across multiple indices -- which may conform to slightly different ECS versions -- this field lets integrations adjust to the schema version of the events. | keyword |
| email.from.address | The email address of the sender, typically from the RFC 5322 `From:` header field. | keyword |
| email.subject | A brief summary of the topic of the message. | keyword |
| email.subject.text | Multi-field of `email.subject`. | match_only_text |
| email.to.address | The email address of recipient | keyword |
| event.action | The action captured by the event. This describes the information in the event. It is more specific than `event.category`. Examples are `group-add`, `process-started`, `file-created`. The value is normally defined by the implementer. | keyword |
| event.category | This is one of four ECS Categorization Fields, and indicates the second level in the ECS category hierarchy. `event.category` represents the "big buckets" of ECS categories. For example, filtering on `event.category:process` yields all events relating to process activity. This field is closely related to `event.type`, which is used as a subcategory. This field is an array. This will allow proper categorization of some events that fall in multiple categories. | keyword |
| event.created | event.created contains the date/time when the event was first read by an agent, or by your pipeline. This field is distinct from @timestamp in that @timestamp typically contain the time extracted from the original event. In most situations, these two timestamps will be slightly different. The difference can be used to calculate the delay between your source generating an event, and the time when your agent first processed it. This can be used to monitor your agent's or pipeline's ability to keep up with your event source. In case the two timestamps are identical, @timestamp should be used. | date |
| event.dataset | Event dataset | constant_keyword |
| event.ingested | Timestamp when an event arrived in the central data store. This is different from `@timestamp`, which is when the event originally occurred.  It's also different from `event.created`, which is meant to capture the first time an agent saw the event. In normal conditions, assuming no tampering, the timestamps should chronologically look like this: `@timestamp` \< `event.created` \< `event.ingested`. | date |
| event.kind | This is one of four ECS Categorization Fields, and indicates the highest level in the ECS category hierarchy. `event.kind` gives high-level information about what type of information the event contains, without being specific to the contents of the event. For example, values of this field distinguish alert events from metric events. The value of this field can be used to inform how these kinds of events should be handled. They may warrant different retention, different access control, it may also help understand whether the data coming in at a regular interval or not. | keyword |
| event.module | Event module | constant_keyword |
| event.original | Raw text message of entire event. Used to demonstrate log integrity or where the full log message (before splitting it up in multiple parts) may be required, e.g. for reindex. This field is not indexed and doc_values are disabled. It cannot be searched, but it can be retrieved from `_source`. If users wish to override this and index this field, please see `Field data types` in the `Elasticsearch Reference`. | keyword |
| event.reason | Reason why this event happened, according to the source. This describes the why of a particular action or outcome captured in the event. Where `event.action` captures the action from the event, `event.reason` describes why that action was taken. For example, a web proxy with an `event.action` which denied the request may also populate `event.reason` with the reason why (e.g. `blocked site`). | keyword |
| event.severity | The numeric severity of the event according to your event source. What the different severity values mean can be different between sources and use cases. It's up to the implementer to make sure severities are consistent across events from the same source. The Syslog severity belongs in `log.syslog.severity.code`. `event.severity` is meant to represent the severity according to the event source (e.g. firewall, IDS). If the event source does not publish its own severity, you may optionally copy the `log.syslog.severity.code` to `event.severity`. | long |
| event.type | This is one of four ECS Categorization Fields, and indicates the third level in the ECS category hierarchy. `event.type` represents a categorization "sub-bucket" that, when used along with the `event.category` field values, enables filtering events down to a level appropriate for single visualization. This field is an array. This will allow proper categorization of some events that fall in multiple event types. | keyword |
| file.hash.md5 | MD5 hash. | keyword |
| file.hash.sha256 | SHA256 hash. | keyword |
| file.name | Name of the file including the extension, without the directory. | keyword |
| file.path | Full path to the file, including the file name. It should include the drive letter, when appropriate. | keyword |
| file.path.text | Multi-field of `file.path`. | match_only_text |
| host.architecture | Operating system architecture. | keyword |
| host.containerized | If the host is a container. | boolean |
| host.domain | Name of the domain of which the host is a member. For example, on Windows this could be the host's Active Directory domain or NetBIOS domain name. For Linux this could be the domain of the host's LDAP provider. | keyword |
| host.hostname | Hostname of the host. It normally contains what the `hostname` command returns on the host machine. | keyword |
| host.id | Unique host id. As hostname is not always unique, use values that are meaningful in your environment. Example: The current usage of `beat.name`. | keyword |
| host.ip | Host ip addresses. | ip |
| host.mac | Host mac addresses. | keyword |
| host.name | Name of the host. It can contain what `hostname` returns on Unix systems, the fully qualified domain name, or a name specified by the user. The sender decides which value to use. | keyword |
| host.os.build | OS build information. | keyword |
| host.os.codename | OS codename, if any. | keyword |
| host.os.family | OS family (such as redhat, debian, freebsd, windows). | keyword |
| host.os.kernel | Operating system kernel version as a raw string. | keyword |
| host.os.name | Operating system name, without the version. | keyword |
| host.os.name.text | Multi-field of `host.os.name`. | text |
| host.os.platform | Operating system platform (such centos, ubuntu, windows). | keyword |
| host.os.version | Operating system version as a raw string. | keyword |
| host.type | Type of host. For Cloud providers this can be the machine type like `t2.medium`. If vm, this could be the container, for example, or other information meaningful in your environment. | keyword |
| input.type | Type of Filebeat input. | keyword |
| log.file.path | Path to the log file. | keyword |
| log.flags | Flags for the log file. | keyword |
| log.offset | Offset of the entry in the log file. | long |
| message | For log events the message field contains the log message, optimized for viewing in a log viewer. For structured logs without an original message field, other fields can be concatenated to form a human-readable summary of the event. If multiple messages exist, they can be combined into one message. | match_only_text |
| observer.egress.interface.name | Interface name as reported by the system. | keyword |
| observer.ingress.interface.name | Interface name as reported by the system. | keyword |
| observer.serial_number | Observer serial number. | keyword |
| panw_cortex.xdr.action_pretty | Pretty description of the action type. | keyword |
| panw_cortex.xdr.agent_data_collection_status | Collection status of the agent. | boolean |
| panw_cortex.xdr.agent_is_vdi | If agent is running inside a Virtual Desktop. | keyword |
| panw_cortex.xdr.agent_version | Version of the XDR Endpoint agent. | keyword |
| panw_cortex.xdr.alert_id | The ID of the alert. | keyword |
| panw_cortex.xdr.attempt_counter | Attempts to block or stop the malicious process. | long |
| panw_cortex.xdr.bioc_category_enum_key | Behavior Indicator type key. | keyword |
| panw_cortex.xdr.bioc_description | A description of the related bioc event. | object |
| panw_cortex.xdr.bioc_indicator | The Behavioral Indicator type matching to the event. | keyword |
| panw_cortex.xdr.category | The Alert category. | keyword |
| panw_cortex.xdr.deduplicate_tokens |  | keyword |
| panw_cortex.xdr.description | A description of the related event. | keyword |
| panw_cortex.xdr.end_match_attempt_ts |  | date |
| panw_cortex.xdr.endpoint_id | The unique ID of the endpoint. | keyword |
| panw_cortex.xdr.events.action_country |  | keyword |
| panw_cortex.xdr.events.action_external_hostname | Any external hostname related to the specific event action. | keyword |
| panw_cortex.xdr.events.action_file_macro_sha256 |  | keyword |
| panw_cortex.xdr.events.action_process_causality_id | The parent processor ID related to the action. | keyword |
| panw_cortex.xdr.events.actor_causality_id | The parent process ID of the actor process. | keyword |
| panw_cortex.xdr.events.actor_process_causality_id | The parent processor ID related to the actor. | keyword |
| panw_cortex.xdr.events.actor_process_signature_status | The signature of the actor process. | keyword |
| panw_cortex.xdr.events.actor_process_signature_vendor | The signature vendor of the actor process. | keyword |
| panw_cortex.xdr.events.agent_host_boot_time | Uptime of the host. | keyword |
| panw_cortex.xdr.events.agent_install_type | Display name of the actor. | keyword |
| panw_cortex.xdr.events.association_strength |  | long |
| panw_cortex.xdr.events.contains_featured_host |  | keyword |
| panw_cortex.xdr.events.contains_featured_ip |  | keyword |
| panw_cortex.xdr.events.contains_featured_user |  | keyword |
| panw_cortex.xdr.events.dns_query_name | The related DNS query for the event. | keyword |
| panw_cortex.xdr.events.dst_action_country | The country related to the destination. | keyword |
| panw_cortex.xdr.events.dst_action_external_hostname | The external hostname of the destination. | keyword |
| panw_cortex.xdr.events.dst_action_external_port | The external (NAT) port of the destination. | keyword |
| panw_cortex.xdr.events.dst_agent_id | The endpoint ID of a destination agent. | keyword |
| panw_cortex.xdr.events.dst_association_strength |  | long |
| panw_cortex.xdr.events.dst_causality_actor_process_execution_time | The process execution time of the destination process. | keyword |
| panw_cortex.xdr.events.event_id | The ID unique to the underlying event related to the alert. | keyword |
| panw_cortex.xdr.events.event_sub_type | Sub type of the event related to the alert. | keyword |
| panw_cortex.xdr.events.event_type | Event type | keyword |
| panw_cortex.xdr.events.fw_app_category | Layer 7 application category related to the firewall event. | keyword |
| panw_cortex.xdr.events.fw_app_id | The layer 7 application ID from the firewall event. | keyword |
| panw_cortex.xdr.events.fw_app_subcategory | Layer 7 application subcategory related to the firewall event. | keyword |
| panw_cortex.xdr.events.fw_app_technology | Layer 7 application type related to the firewall event. | keyword |
| panw_cortex.xdr.events.fw_device_name | Related firewall device. | keyword |
| panw_cortex.xdr.events.fw_email_recipient |  | keyword |
| panw_cortex.xdr.events.fw_email_sender |  | keyword |
| panw_cortex.xdr.events.fw_email_subject |  | keyword |
| panw_cortex.xdr.events.fw_is_phishing | If event is related to a phishing campaign. | keyword |
| panw_cortex.xdr.events.fw_misc | Additional information related to the firewall event. | keyword |
| panw_cortex.xdr.events.fw_url_domain | Related domain to the firewall event. | keyword |
| panw_cortex.xdr.events.fw_vsys | The related VSYS name if applicable. | keyword |
| panw_cortex.xdr.events.fw_xff |  | keyword |
| panw_cortex.xdr.events.module_id | The ID of the module that caught the event. | keyword |
| panw_cortex.xdr.events.os_actor_causality_id | The ID of the OS actor process | keyword |
| panw_cortex.xdr.events.os_actor_effective_username | Username related to the OS actor. | keyword |
| panw_cortex.xdr.events.os_actor_process_causality_id | The ID of the parent process related to the OS actor. | keyword |
| panw_cortex.xdr.events.os_actor_process_command_line | OS actor full command line example. | keyword |
| panw_cortex.xdr.events.os_actor_process_image_name | OS actor binary name. | keyword |
| panw_cortex.xdr.events.os_actor_process_image_path | OS actor binary path. | keyword |
| panw_cortex.xdr.events.os_actor_process_image_sha256 | SHA256 hash indentifier of the OS actor process. | keyword |
| panw_cortex.xdr.events.os_actor_process_instance_id | The process ID related to the OS actor. | keyword |
| panw_cortex.xdr.events.os_actor_process_os_pid | The OS PID related to the related process. | keyword |
| panw_cortex.xdr.events.os_actor_process_signature_status | Signature of the OS actor process. | keyword |
| panw_cortex.xdr.events.os_actor_process_signature_vendor | Signature vendor of the OS actor process. | keyword |
| panw_cortex.xdr.events.os_actor_thread_thread_id | The thread ID related to the related OS actor process. | keyword |
| panw_cortex.xdr.events.story_id |  | keyword |
| panw_cortex.xdr.external_id | External ID related to the Alert itself. | keyword |
| panw_cortex.xdr.filter_rule_id | ID of the filter rule. | keyword |
| panw_cortex.xdr.is_whitelisted | If process is whitelisted. | boolean |
| panw_cortex.xdr.local_insert_ts |  | date |
| panw_cortex.xdr.mac | Main MAC address of the agent. | keyword |
| panw_cortex.xdr.mac_address | Array of all the MAC addresses related to the agent. | keyword |
| panw_cortex.xdr.matching_service_rule_id |  | keyword |
| panw_cortex.xdr.matching_status | Matching status of the endpoint group. | keyword |
| panw_cortex.xdr.mitre_tactic_id_and_name |  | keyword |
| panw_cortex.xdr.mitre_technique_id_and_name |  | keyword |
| panw_cortex.xdr.source |  | keyword |
| panw_cortex.xdr.starred | If alert type is prioritized (starred). | boolean |
| process.code_signature.status | Additional information about the certificate status. This is useful for logging cryptographic errors with the certificate validity or trust status. Leave unpopulated if the validity or trust of the certificate was unchecked. | keyword |
| process.code_signature.subject_name | Subject name of the code signer | keyword |
| process.command_line | Full command line that started the process, including the absolute path to the executable, and all arguments. Some arguments may be filtered to protect sensitive information. | wildcard |
| process.command_line.text | Multi-field of `process.command_line`. | match_only_text |
| process.entity_id | Unique identifier for the process. The implementation of this is specified by the data source, but some examples of what could be used here are a process-generated UUID, Sysmon Process GUIDs, or a hash of some uniquely identifying components of a process. Constructing a globally unique identifier is a common practice to mitigate PID reuse as well as to identify a specific process over time, across multiple monitored hosts. | keyword |
| process.executable | Absolute path to the process executable. | keyword |
| process.executable.text | Multi-field of `process.executable`. | match_only_text |
| process.hash.md5 | MD5 hash. | keyword |
| process.hash.sha256 | SHA256 hash. | keyword |
| process.name | Process name. Sometimes called program name or similar. | keyword |
| process.name.text | Multi-field of `process.name`. | match_only_text |
| process.parent.code_signature.status | Additional information about the certificate status. This is useful for logging cryptographic errors with the certificate validity or trust status. Leave unpopulated if the validity or trust of the certificate was unchecked. | keyword |
| process.parent.code_signature.subject_name | Subject name of the code signer | keyword |
| process.parent.command_line | Full command line that started the process, including the absolute path to the executable, and all arguments. Some arguments may be filtered to protect sensitive information. | wildcard |
| process.parent.command_line.text | Multi-field of `process.parent.command_line`. | match_only_text |
| process.parent.entity_id | Unique identifier for the process. The implementation of this is specified by the data source, but some examples of what could be used here are a process-generated UUID, Sysmon Process GUIDs, or a hash of some uniquely identifying components of a process. Constructing a globally unique identifier is a common practice to mitigate PID reuse as well as to identify a specific process over time, across multiple monitored hosts. | keyword |
| process.parent.executable | Absolute path to the process executable. | keyword |
| process.parent.executable.text | Multi-field of `process.parent.executable`. | match_only_text |
| process.parent.hash.md5 | MD5 hash. | keyword |
| process.parent.hash.sha256 | SHA256 hash. | keyword |
| process.parent.name | Process name. Sometimes called program name or similar. | keyword |
| process.parent.name.text | Multi-field of `process.parent.name`. | match_only_text |
| process.parent.uptime | Seconds the process has been up. | long |
| process.pid | Process id. | long |
| process.thread.id | Thread ID. | long |
| registry.data.strings | Content when writing string types. Populated as an array when writing string data to the registry. For single string registry types (REG_SZ, REG_EXPAND_SZ), this should be an array with one string. For sequences of string with REG_MULTI_SZ, this array will be variable length. For numeric data, such as REG_DWORD and REG_QWORD, this should be populated with the decimal representation (e.g `"1"`). | wildcard |
| registry.key | Hive-relative path of keys. | keyword |
| registry.path | Full path, including hive, key and value | keyword |
| registry.value | Name of the value written. | keyword |
| related.hash | All the hashes seen on your event. Populating this field, then using it to search for hashes can help in situations where you're unsure what the hash algorithm is (and therefore which key name to search). | keyword |
| related.user | All the user names or other user identifiers seen on the event. | keyword |
| rule.id | A rule ID that is unique within the scope of an agent, observer, or other entity using the rule for detection of this event. | keyword |
| rule.name | The name of the rule or signature generating the event. | keyword |
| source.as.number | Unique number allocated to the autonomous system. The autonomous system number (ASN) uniquely identifies each network on the Internet. | long |
| source.as.organization.name | Organization name. | keyword |
| source.as.organization.name.text | Multi-field of `source.as.organization.name`. | match_only_text |
| source.geo.continent_name | Name of the continent. | keyword |
| source.geo.country_iso_code | Country ISO code. | keyword |
| source.geo.country_name | Country name. | keyword |
| source.geo.location | Longitude and latitude. | geo_point |
| source.ip | IP address of the source (IPv4 or IPv6). | ip |
| source.port | Port of the source. | long |
| tags | List of keywords used to tag each event. | keyword |
| user.name | Short name or login of the user. | keyword |
| user.name.text | Multi-field of `user.name`. | match_only_text |

