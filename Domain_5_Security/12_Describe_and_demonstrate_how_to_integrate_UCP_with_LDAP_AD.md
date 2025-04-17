# Describe and demonstrate how to integrate UCP with LDAP/AD
Integrating Universal Control Plane (UCP) with LDAP/Active Directory (AD) allows you to manage users and groups from your organization's directory services, ensuring centralized authentication and authorization. Here’s a step-by-step guide on how to integrate UCP with LDAP/AD:

## Step-by-Step Guide
### 1. Access UCP Web UI:
- Log in to the UCP web interface using your administrator credentials.
### 2. Navigate to Authentication & Authorization:
- Go to "Admin Settings" > "Authentication & Authorization".
### 3. Enable LDAP:
- In the "Identity Provider" section, move the slider next to "LDAP" to enable LDAP settings.
### 4. Configure LDAP Server:
- LDAP Server URL: Enter the URL for the LDAP server.
- Reader DN: Enter the Distinguished Name (DN) of the LDAP account used to search entries in the LDAP server.
- Reader Password: Enter the password for the LDAP account.
- Skip TLS Verification: Set whether to verify the LDAP server certificate when TLS is in use.
- Use Start TLS: Define whether to authenticate or encrypt the connection after connecting to the LDAP server over TCP.
### 5. Set Up LDAP User Search Configurations:
- Base DN: Specify the distinguished name of the node in the LDAP directory tree where the search starts.
- Scope: Define the scope of the search (e.g., subtree).
- Filter: Set the filter to find users.
- Username Attribute: Specify the attribute used for the username.
- Full Name Attribute: Specify the attribute used for the full name.
### 6. Just-In-Time User Provisioning:
- Enable this option to create user accounts only when users log in for the first time.
### 7. Save Configuration:
- Click "Save" to apply the LDAP settings.

## Example Commands
### 1. Enable LDAP via CLI:
```
AUTHTOKEN=$(curl -sk -d '{"username":"<ucp_username>","password":"<ucp_password>"}' https://<ucp_url>/auth/login | jq -r .auth_token)
curl -sk -H "Authorization: Bearer $AUTHTOKEN" https://<ucp_url>/api/ucp/config-toml > ucp-config.toml
```

### 2. Update Configuration:
- Edit the ucp-config.toml file to include LDAP settings:
```
[auth]
backend = "ldap"
[auth.ldap]
url = "ldap://<ldap_server>"
reader_dn = "<reader_dn>"
reader_password = "<reader_password>"
base_dn = "<base_dn>"
scope = "sub"
filter = "(objectClass=person)"
username_attribute = "uid"
full_name_attribute = "cn"
```
### 3. Apply Configuration:
```
curl -sk -H "Authorization: Bearer $AUTHTOKEN" --upload-file ucp-config.toml https://<ucp_url>/api/ucp/config-toml
```
Relevant Documentation
For detailed instructions and more information, you can refer to the following official documentation:

Mirantis Documentation: Integrate with an LDAP Directory1
Docker Documentation: [LDAP Integration2](https://docs.mirantis.com/containers/v2.1/dockeree-products/ucp/admin/configure/integrate-with-LDAP-directory.html)
These resources provide comprehensive guidance on integrating UCP with LDAP/AD.
