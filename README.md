# TrustedSec Ldapsearch cheatsheet


**User's Info:** ldapsearch "(samAccountName={USERNAME})" 0 {DC}

**Find Users by Name:** ldapsearch "(&(objectClass=user)(name=Smith))" name 0 {DC}

**User's Groups:** ldapsearch "(samAccountName={USERNAME})" memberOf 0 {DC}

**Find by Group:** ldapsearch "(memberOf=cn=Domain Admins,cn=Users,dc={DOMAIN},dc={DOMAIN},dc=local)" 0 {DC}

**Domain Groups:** ldapsearch "(objectClass=group)" cn,member,distinguishedName 0 {DC}

**Organizational Units:** ldapsearch "(objectClass=organizationalUnit)" 0 {DC}

**Computers:** ldapsearch "(objectClass=computer)" name 0 {DC}

**Domain Trusts:** ldapsearch "(objectClass=trustedDomain)" flatname,trustdirection,name,distinguishedName 0 {DC}

**List Members of Domain Admins:** ldapsearch "(&(objectCategory=Person)(sAMAccountName=)(memberOf=cn=Domain Admins,cn=Users,dc={DOMAIN},dc={DOMAIN},dc=LOCAL))" cn,sAMAccountName 0 {DC}

**List Members of Domain Admins Recursively:** ldapsearch "(&(objectCategory=Person)(sAMAccountName=)(memberOf:1.2.840.113556.1.4.1941:=cn=Domain Admins,cn=Users,dc={DOMAIN},dc={DOMAIN},dc=LOCAL))" cn,sAMAccountName 0 {DC}

**All Admins:** ldapsearch "(&(objectClass=user)(objectCategory=Person)(adminCount=1))" cn,sAMAccountName 0 {DC}

**Search by Title:** ldapsearch "(&(objectCategory=person)(objectClass=user)(title=Manager*))" cn,sAMAccountName 0 {DC} 
