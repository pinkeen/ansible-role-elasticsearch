# Universal role which installs and configures an elasticsearch node. (for CentOS6/7)

Supported vars:
 - es_interface_name (default: lo) - elastic shall bind to this iface, 'any' -> bind to all ifaces
 - es_cluster_name (default: elastic)
 - es_multicast (default: false)
 - es_unicast_hosts (default: []) - list of other es hosts in cluster
 - es_http_port (default: 9200-9299)
 - es_transport_port (default: 9300-9400)
 - es_nodes_group (default: false) - name of the ansible group which holds all hosts in this cluster
 - es_allowed_ips (passed to open-port)
 - es_allowed_group (passed to open-port)
