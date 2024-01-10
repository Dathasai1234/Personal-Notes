


- Microsoft Entra Id uses Conditional Access to give access to the resources based on the *identity signal*.
- identity signal include
	1. Who is the user is,
	2. Where the user is,
	3. What device the user is requesting from
- provides more granular MFA experience to the users.
- user is not challenged for second authentication factor if they are in the known location.
- is challenged for 2nd authentication factor if their sign-in signals are unusual or they’re at an unexpected location.
- During sign-in, 
- Conditional Access collects signals from the user
- makes decisions based on those signals, 
- and then enforces that decision by allowing or denying the access request or challenging for a multifactor authentication response.