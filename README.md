# Ansible Collection - puppeteers.ovhcloud

This collection contains roles for managing [OVHcloud](https://www.ovhcloud.com/en/).

# Roles

## puppeteers.ovhcloud.certbot_dns

This role manages creation and renewal of certbot DNS wildcard certificates for
domains in OVHcloud. It uses Podman to run the [certbot/dns-ovh
image](https://hub.docker.com/r/certbot/dns-ovh) as a normal user. By default
the renewal runs from cron every day, but new certificates are requested only
if the old ones are about to expire.

Before using this role you must create credentials for OVHcloud with enough
permissions to manage your domain records. This part is well-documented in
[certbot-dns-ovh
documentation](https://certbot-dns-ovh.readthedocs.io/en/stable/).

To use the role you must pass the following parameters:

* **puppeteers_ovhcloud_certbot_dns_local_user**: local system user run Podman/certbot as.
* **puppeteers_ovhcloud_certbot_dns_domain**: DNS domain to request certificates for.
* **puppeteers_ovhcloud_certbot_dns_application_key**: application key for the OVHcloud.
* **puppeteers_ovhcloud_certbot_dns_application_secret**: application secret for OVHcloud.
* **puppeteers_ovhcloud_certbot_dns_consumer_key**: consumer key for OVHcloud.

Other, optional parameters are defined in
[roles/certbot_dns/defaults/main.yml](roles/certbot_dns/defaults/main.yml).

This role places the OVHcloud credentials file to
`~/.config/certbot-dns-ovh/credentials.ini` and the generated certificates can
be found from `~/.local/share/letsencrypt/`.
