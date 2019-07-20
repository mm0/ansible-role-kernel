Ansible Role: Kernel
===

[![Build Status](https://travis-ci.org/mm0/ansible-role-kernel.svg?branch=master)](https://travis-ci.org/mm0/ansible-role-kernel)

An Ansible role that optimizes sysctl and sysfs for cloud database performance

Requirements
---

None 

Role Variables
---

Available variables are listed below:

```yml
kernel_vars:
  - name: vm.swappiness
    value: 0
  - name: net.ipv4.tcp_tw_reuse
    value: 1
  - name: net.ipv4.tcp_slow_start_after_idle
    value: 0
  - name: net.ipv4.tcp_max_syn_backlog
    value: 8096
  - name: net.ipv4.tcp_rmem
    value: 4096 12582912 16777216
  - name: net.ipv4.tcp_wmem
    value: 4096 12582912 16777216
  - name: net.core.wmem_max
    value: 16777216
  - name: net.core.rmem_max
    value: 16777216
  - name: net.core.netdev_max_backlog
    value: 5000
  - name: net.core.somaxconn
    value: 65536
  - name: vm.max_map_count
    value: 262144
  - name: net.netfilter.nf_conntrack_max
    value: 2621440
kernel_modules:
  - nf_conntrack
  - nf_conntrack_ipv4
io_vars:
  - echo never > /sys/kernel/mm/transparent_hugepage/enabled
  - echo "512" > /proc/sys/net/core/somaxconn
```

Dependencies
---

None 

Example Playbook
---

```yml
- hosts: nodes
  roles:
  - { role: mm0.kernel }
```

License
---------------

BSD-2

Author Information
------------------

[Matt Margolin](mailto:matt.margolin@gmail.com)

[mm0](https://github.com/mm0) on github
