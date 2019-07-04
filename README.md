# Marvel LDIF Project

### Project Objectives

The primary objective of this project was to learn Python by applying it to a use case. The use case for this was to create an LDAP Data Interchange Format (LDIF) file with data from the JSON files from the Marvel API. LDIF files can be used to create directory objects such as Users and Groups within LDAP services such as Active Directory and OpenLDAP.

### Use Cases


My main need for an LDIF like this was for testing Server authentication, Linux SSSD w/ Kerberos, and group-based access. 

__LINUX SSSD__

Allow each user to be signed into a linux node via SSSD. Each user will have a default shell. Once the LDIF is created, we can then create a script to create keytabs for those users within MIT KDC. 


__GROUP BASED ACCESS/AUTHENTICATION__

A common scenario is to use AD groups to provide access to a server or service. This access is done in one of two ways:

- Additive: Providing only those users who can access the service. Users not mentioned have an implicit denial.
- Subtractive: Providing those users who are not allowed to have access (i.e. Access provided to memberOf=X-Men but Access denied for users who are memberOf=Brotherhood of Mutants). 

The benefit of this LDIF is that there are some overlaps (i.e. Wolverine) who is a member of both the X-men and the Brotherhood of Mutants. In this case, most security services (such as ACLs, Apache Ranger, etc) will use the order of the defined rules but even those can be defined to provide either the "First denial meaning total denial" or "First approval meaning total approval". 


### NEXT STEPS

- Code mechanism to parse name and provide different values for `sn`, `givenName`. 
- Code mapping for `l (locality)`, `st (state)`, etc to provide true locations so permissions can be based on that person's location within the world.
- Find a suitable LDAP object for Powers
- Create DB of categories and ensure all objects have at least 3. 