# Key decision making criteria
## Feature set
1. User management:
   1. complete lifecycle support signup, signin, deactivation
   2. Access control
   3. password policies supported:
      1. Password History - While resetting the password, last 3 password should not be accepted by the system.
      2. Password Age - Every password must be be expirable after certain time duration
      3. Password Complexity - For example, the password must contain some uppercase letter, special characters etc.
      4. Password Length - Each password must have a minimum length
      5. Lockout - Locking of profile after 3 unsuccessful login attempts       
3. Social login: LDAP, Active Directory, google etc.
4. SSO
5. MFA

## Data residence
1. no third party hosting
2. open source for cost benefits
