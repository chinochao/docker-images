# Duo Auth Proxy Docker Image


## Require environment variables:

```
DUO_API_HOST : Duo API Host URL
DUO_IKEY : Duo API IKEY 
DUO_SKEY : Duo API SKEY


CONFIG_CLIENT : Config client, choices are ad_client and radius_client(still under work)
CONFIG_LDAP_HOST : Host for AD/LDAP , RADIUS
CONFIG_LDAP_SERVICE_ACCOUNT_USERNAME : LDAP Service Account Username
CONFIG_LDAP_SERVICE_ACCOUNT_PASSWORD : LDAP Service Account Password
CONFIG_LDAP_SEARCH_DN : LDAP Search DN
CONFIG_LDAP_BIND_DN : LDAP Account Full DN
CONFIG_LDAP_SECRET : Only needed if using RADIUS
CONFIG_LDAP_EXEMPT_OU_1 : Exempt User or Group
```

```
## Optional environment variables:
CONFIG_DEBUG : Debug logs (Defaults to false, choices are true or false)
CONFIG_LDAP_SSL_VERIFY : Verify SSL from AD/LDAP Host (Defaults to true, choices are true or false)
CONFIG_LDAP_TRANSPORT : Transport (Defaults to ldaps, choices are clear, ldaps, and starttls)
CONFIG_LDAP_PORT : Port to connect to in AD/LDAP (Defaults to 636)
CONFIG_LDAP_HOST_2 : Secondary/fallback domain controller
CONFIG_LDAP_HOST_3 : Tertiary/fallback domain controller
CONFIG_LDAP_HOST_4 : Quaternary/fallback domain controller
CONFIG_LDAP_HOST_5 : Quinary/fallback domain controller
CONFIG_LDAP_EXEMPT_OU_2 : Extra user or groups to exempt
CONFIG_LDAP_EXEMPT_OU_3 : Extra user or groups to exempt
CONFIG_LDAP_EXEMPT_OU_4 : Extra user or groups to exempt
```