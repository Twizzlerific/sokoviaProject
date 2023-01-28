
# Marvel-Based LDAP 
![verion](https://img.shields.io/badge/version-1.0-blue) ![Marvel](https://img.shields.io/badge/-Marvel%20Comics-red)

Create an LDAP server based on Marvel Comics with:
- 97 Groups
- 701 Users

The group memberships are pefect for testing complex permissions and Role-Based Access Controls .

## Quick Start with Docker


Using the [osixia-openldap](https://github.com/osixia/docker-openldap) image to set up an openLDAP instance:
```
# docker run \
--name sokovia \
--env=LDAP_BASE_DN=dc=example,dc=com \
--env=LDAP_ADMIN_PASSWORD=admin \
--env=LDAP_RFC2307BIS_SCHEMA=true \
--env=LDAP_DOMAIN=example.com \
-p 389:389 -p 636:636 -d osixia/openldap:1.5.0

# ldapadd -H ldap://localhost:389 -D "cn=admin,dc=example,dc=com" -w admin -f base.ldif
# ldapadd -H ldap://localhost:389 -D "cn=admin,dc=example,dc=com" -w admin -f users.ldif
# ldapadd -H ldap://localhost:389 -D "cn=admin,dc=example,dc=com" -w admin -f groups.ldif
```

The `combined.ldif` can be used to import the OUs, users, and groups with a single file. 


## Groups
Included with all of the groups are service `svc` groups which add another layer of association by linking users by categories such as:

- Villians
- Heroes
- Previously Deceased
- Avengers-Related
- etc.

> NOTE: All users are part of the `ldap-users` group.
