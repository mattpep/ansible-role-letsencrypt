LetsEncrypt
===========

A thin-ish wrapper around the acme\_ modules within ansible to set up a cert for an nginx virtual host, creating an account if necessary, and also reloading nginx if desired.

Requirements
------------

nginx installed on the host.

Role Variables
--------------
* *letsencrypt_account_email* (_optional_) The email address to which LE should send reminders
* *letsencrypt_cert_domain* The primary certificate domain. Will not be used if letsencrypt\_cert\_domains is specified.
* *letsencrypt_cert_domains* List of domain names for which the cert will be valid.
* *letsencrypt_prod_cert* (_optional)_ Whether the cert should be creating using the LE staging or prod cert. You probably want this set to true.
* *letsencrypt_csr_subject_prefix* `'/C=GB/ST=London/L=London/O=ExampleOrg/'`

Dependencies
------------

nginx role (https://github.com/jdauphant/ansible-role-nginx.git), though only if you set `letsencrypt_handle_nginx`.

Example Playbook
----------------

    - hosts: servers
      roles:
      -  role: letsencrypt
         vars:
           letsencrypt_cert_domains:
             - www.example.com
             - www.example.co.uk
             - www.example.co.fr

Notes
-----

Now works on version 2 of the LetsEncrypt API
