# UC SAAS product auth flows with inhouse auth server
[OAuth2_Support_SAAS.pdf](https://github.com/khatwaniNikhil/AuthN_AuthZ/files/12380184/OAuth2.support.in.Uniware.pdf)

1.  e-commerce seller data exposed over JSON based REST endpoints as well as XML based SOAP api’s
2. HTTP BASIC for soap api’s
3. OAuth based registration and auth flows for third party apps to access on behalf of seller.
    1. Android app for within warehouse pick/pack: password grant type(provides seller credentials)
        1. client registered or not verification as well as current user login credentials verification
        2. Token issuance
        3. Token based REST api access
    2. Main SAAS Web App LOGIN - SSO + JSessionID/cookie 
        1. CAS based SSO via custom oauth grant type “service ticket grant” flow to get list of domains where given tenant has access and service ticket for current requested domain access.
        2. Issued service ticket by auth server is validated to issue cookie based web access.
     3. authorization Code grant type - org. internal ops and dev access to ticketing internal s/w 
           

# Migration from inhouse auth server to Keycloak
# Why keycloak chosen
1. open source
2. admin UI support
3. support customisation - leveraged for on demand migration of users
4. MFA via TOTP

# Keycloak - Sequence Diagram
![](https://github.com/khatwaniNikhil/AuthN_AuthZ/blob/main/keycloak_sequence_diagram.png)

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
