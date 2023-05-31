# Keycloak - Sequence Diagram
![](https://github.com/khatwaniNikhil/AuthN_AuthZ/blob/main/keycloak_sequence_diagram.png)

# Use cases by Grant Types 
1. Password grant type
   1. Android app used in warehouse, REST S2S integration 
2. CAS protocol based SSO (using service ticket grant type, self hosted CAS server)
   1. SAAS tenant's user SSO across multiple accounts of same tenant
   2. org. internal ops and dev access to tenant web app
3. authorization Code grant type
   1. org. internal ops and dev access to ticketing internal s/w 

# Why keycloak chosen
1. open source
2. admin UI support
3. support customisation - leveraged for on demand migration of users
4. MFA via TOTP

# challenges | roadmap
1. single user map to multi tenants
2. keycloak as centralised place to login/logout user from specific/all applications. preferably single click
3. Forgot Password support
4. Password policies:
    1. Password History - While resetting the password, last 3 password should not be accepted by the system.
    2. Password Age - Every password must be be expirable after certain time duration
    3. Password Complexity - For example, the password must contain some uppercase letter, special characters etc.
    4. Password Length - Each password must have a minimum length
    5. Lockout - Locking of profile after 3 unsuccessful login attempts
5. Strong auditing (e.g. save last x days worth of login sessions). - IP based
6. Federated identity support - Social Login can be enabled if required.
7. Device Type identification
