# References
1. https://medium.com/vx-company/oauth-and-openid-explained-with-real-life-examples-bf40daa8049f
2. https://developer.okta.com/blog/2019/10/21/illustrated-guide-to-oauth-and-oidc

# OAuth
1. Real word example
    1. Linkedin given restricted access(without sharing username and password) to our google contacts to join linkedin
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
