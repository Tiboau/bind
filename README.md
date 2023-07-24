# Bind

Install & configure bind

## Requirements

```
```

## Var

```
listen_address: 172.17.1.40;
allow_query: 172.17.1.0/24;
domain_name: monlab.local
forwardzone:
  - name: monlab.local
    def:
    - name: bind
      record: A
      ip: 172.17.1.40
    - name: quay
      record: A
      ip: 172.17.1.50

reversezone:
  - name: "1.17.172.in-addr.arpa"
    def:
    - name: bind
      record: PTR
      last_digit: 40
    - name: quay
      record: PTR
      last_digit: 50
```

## Playbook

```
- name: bind
  hosts: bind
  gather_facts: yes
  roles:
    - bind
```
