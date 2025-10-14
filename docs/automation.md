A. Identity Provider Authentication via Integration

Where REDCap is configured with LDAP, SSO, or Shibboleth, a user can access the project they are assigned to by using institutional credentials. The manual account creation step is by-passed when the account is accessed for the first time. However, the Project Administrator continues to exercise project governance and can restrict access according to the username or a group. Further information is available from the REDCap software's technical documentation repository and the configuration files. 

B. Technical Users and the API

Where suitable project permissions exist, a user can be granted access to data stored by the project's REDCap account using an API key. The scripts can be written in R or Python. Amongst the features available to manage users from an API are:
- Batch additions or ammendments to user accounts 
- Configuration of user rights or roles
- Querying user activity logs
