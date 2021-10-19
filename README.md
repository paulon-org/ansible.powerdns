# Examples
## nginx authenticator
```
- hosts: <hosts>
  vars:
    powerdns:
      admin: yes
      master: yes
      
  roles:
    - certbot
```
# custom dns authenticator (support DNAMEs and odd DNS zones)
```
- hosts: <hosts>
  vars:
    certbot:
      mail: mail@example.org
      certname: site1.example.org
      domains: [ site1.example.org, site2.example.org ]
      authenticator: dns
      dns:
        server: dns1.example.org
        zone: example.org
        record: _acme-challenge.example.org.
        keyname: dns_key.example.org
        algorithm: hmac-sha512
        secret: someverysecretkey
  roles:
    - certbot
```