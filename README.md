Sets up elasticsearch 1.7 on CentOS 7
=====================================

Simplified to the core.

Look at defaults for available config.

Example set up of a cluster using ansible group:

```yml
- name: Elasticsearch
  user: root
  hosts: search
  pre_tasks:
    - name: Initialize elasticsearch hosts var
      set_fact:
        es_unicast_hosts: []
    - name: Gather elasticsearch hosts by group
      set_fact:
        es_unicast_hosts: "{{ es_unicast_hosts }} + [ '{{ hostvars[item].intnet_host }}' ]"
      when: item != inventory_hostname
      with_items: "{{ groups['search'] }}"
    - debug:
        msg: "Initialized elasticsearch hosts: {{ es_unicast_hosts|join(', ') }}"
  roles:
    - pinkeen.elasticsearch
```



