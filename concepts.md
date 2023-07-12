# References
1. https://medium.com/vx-company/oauth-and-openid-explained-with-real-life-examples-bf40daa8049f
2. https://developer.okta.com/blog/2019/10/21/illustrated-guide-to-oauth-and-oidc
3. https://medium.com/@robert.broeckelmann/when-to-use-which-oauth2-grants-and-oidc-flows-ec6a5c00d864
4. https://darutk.medium.com/the-simplest-guide-to-oauth-2-0-8c71bd9a15bb
5. https://darutk.medium.com/diagrams-and-movies-of-all-the-oauth-2-0-flows-194f3c3ade85
6. https://darutk.medium.com/oauth-2-0-client-authentication-4b5f929305d4
7. https://videos.pingidentity.com/detail/video/1494397722001/oauth-deep-dive:-client-credentials-grant

# OAuth
1. Real word example
    1. Giving Linkedin a restricted access(without sharing username and password) to our google contacts to join linkedin
    2. on hotel checkin - post user identity check, key issued is analogous to access token for acccessing specific room and other allowed services like gym, spa etc.
2. Key steps
   1. verify the actual owner identity(user who is sharing his google contacts)
   2. grant permissions to third-party(linkedin)
3. Authentication code (commonly used grant type)
    1. post user identity verificaiton, third party is provided authenticaiton code
    2. Using auth code along with client id and client secret, third party requests for authentication token with limited scope and TTL.
    3. above step is skipped in implicit grant type but would be less secure.
4. How is Security handled
   1. access token with limited scopes

# OpenID connect
1. Real world example
   1. Logging into Spotify with your Facebook account
      1. You log into Facebook
      2. Facebook sends your name and e-mail to Spotify.
      3. Spotify uses those details to identify you
      4. Facebook does not manage all apps where user has given what permission around data access
    2. At hotel, receptionist asks for your passport which is already verfified by govt.
       1. passport document mentioned details can be used to board plane, check into hotel etc.
3. OpenID communicates identity, not permissions.
4. OpenID is decentralized authentication 
   1. decentralized - it is unaware of the existence of any resources or applications that need to be protected, unlike user google contacts to be accessed securely in above oauth example.
   2. authentication - user verifies it identity over facebook by entering login credentials.
5. How is Security handled
   1. access tokens with claims(contain information about an identity)

# Trust and Confidentiality 
   ## Untrusted versus trusted
   1. Security guidelines for Untrusted client
      1. users credentials are never exposed to the client makes it more secure, user enters credentials at auth server domain and client is just provided access token
      2. Untrusted does not mean malicious but need user intervention to get access token.
   2. Trusted client
      1. Client asks for credentials from user and then client passes the same to Auth server to get token

  ## Confidential versus public clients
   1. Confidential
      1. clients that can hide their client credentials, can’t reverse engineer them to get secrets.
      2. Clients running a server side and use it for OAuth flow integration
      3. not running on a desktop or distributed through an app store
   2. Public
      1. browsers, mobile apps, and IoT devices
      2. clients that cannot hide their client credentials
      3. your client is downloaded by your user
      4. ran in the user's browser (source code is visible and can be searched for the credentials)
      5. native desktop client(theoretically source code can be decompiled)

  ## Choosing authorisation flow basis Trust and Confidentiality 

  ![](https://github.com/khatwaniNikhil/AuthN_AuthZ/blob/main/different_authorisation_flows.png)
  **Note** - Second column “token” means implicit flow

  ### Recommended grant types
  #### 1. authorization code
  (user auth + access permissions)  ->  (issued auth code to client)  ->(client auth via secret + token exchange using auth code)

  ##### use case
  1. web and mobile apps, as it provided extra layer of security via extra hop of sharing secret and authcode to token exchange.
  2. For native apps, use native browser so that redirection is possible
  3. if secret cannot be stored securely or for extra security against attacks using PKCE extension.

  #### 2. client credentials driven token
  (client enters his clientid and secret) -> (token issued) -> (client access data using token)
  
  ##### use case
  1. user auth skipped
  2. server to server api based integration use case
  3. access is for resources which are somewhat owned by client

 ### Not recommended grant types
 #### 1. implicit flow
 1. skips auth code and directly gives token but  insecure, broken, deprecated, and should never, ever be used 

 #### 2. resource Owner Password flow 
 1. user/resource owner credentials are shared directly with client app instead of opening a browser and sharing with auth server in authorization grant
 2. does not support any of the auxiliary security features like Multi-factor authentication and Password resets.


