# [WIP] Velotix Application on Google Marketplace

## Prerequisites 

* Wildcard SSL for your domain

* DNS records for:

`velotix.mydomain.com` - The main site for Velotix interface

`velotix-be.velotix.com` - The backend of Velotix

`velotix-se.velotix.com` - Superset service for Velotix dashboards

`velotix-ke.velotix.com` - Keycloak service for Velotix User Federation

# TBD

# velotix-mp

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square)

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| suite.global.ingress.wildcardDomain | string | `nil` |  |
| suite.global.ingress.wildcardCert | string | `nil` |  |
| suite.global.ingress.wildcardCertKey | string | `nil` |  |
| suite.global.ingress.subDomains.superset | string | `nil` |  |
| suite.global.ingress.subDomains.keycloak | string | `nil` |  |
| suite.global.ingress.subDomains.client | string | `nil` |  |
| suite.global.ingress.subDomains.fe | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_ADMIN_USER | string | `admin` |  |
| suite.fe.configMap.data.KEYCLOAK_ADMIN_PASS | string | `admin` |  |
| suite.fe.configMap.data.KEYCLOAK_UFED_VENDOR | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_UFED_BIND_CREDENTIAL | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_UFED_BIND_DN | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_UFED_CONNECTION_URL | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_UFED_USERS_DN | string | `nil` |  |
