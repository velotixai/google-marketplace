# [WIP] Velotix Application on Google Marketplace

## Prerequisites 

* Wildcard SSL for your domain

* DNS records for:

`velotix.mydomain.com` - The main site for Velotix interface

`velotix-be.mydomain.com` - The backend of Velotix

`velotix-se.mydomain.com` - Superset service for Velotix dashboards

`velotix-ke.mydomain.com` - Keycloak service for Velotix User Federation

# TBD

# velotix-mp

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square)

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| suite.global.ingress.wildcardDomain | string | `nil` | The domain you will use with wildcard SSL. I.E: `mydomain.com` |
| suite.global.ingress.wildcardCert | string | `nil` | Base64 encoded tls.crt of the wildcard SSL |
| suite.global.ingress.wildcardCertKey | string | `nil` | Base64 encoded tls.key of the wildcard SSL |
| suite.global.ingress.subDomains.superset | string | `velotix-se` | Superset subdomain. (Recommended to not change) |
| suite.global.ingress.subDomains.keycloak | string | `velotix-ke` | Keycloak subdomain. (Recommended to not change) |
| suite.global.ingress.subDomains.client | string | `velotix` | Velotix main subdomain. (Recommended to not change) |
| suite.global.ingress.subDomains.fe | string | `velotix-be` | Velotix backend subdomain. (Recommended to not change) |
| suite.fe.configMap.data.KEYCLOAK_ADMIN_USER | string | `admin` | Keycloak first admin credentials (User), can be changed after deployment. |
| suite.fe.configMap.data.KEYCLOAK_ADMIN_PASS | string | `admin` | Keycloak first admin credentials (Password), can be changed after deployment. |
| suite.fe.configMap.data.KEYCLOAK_UFED_VENDOR | string | `nil` | LDAP Vendor, I.E: `ad` for Active Directory |
| suite.fe.configMap.data.KEYCLOAK_UFED_BIND_DN | string | `nil` | LDAP admin user |
| suite.fe.configMap.data.KEYCLOAK_UFED_BIND_CREDENTIAL | string | `nil` | LDAP admin password |
| suite.fe.configMap.data.KEYCLOAK_UFED_CONNECTION_URL | string | `nil` | LDAP URL (Recommended to use `ldaps` protocol) |
| suite.fe.configMap.data.KEYCLOAK_UFED_USERS_DN | string | `nil` | LDAP UsersDn, I.E: `OU=AADDC Users,DC=mydomain,DC=com` |
