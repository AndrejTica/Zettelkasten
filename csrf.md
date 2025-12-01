---
date: 2025-11-05
tags:
  - networking
  - security  
---
When you log into a webapp, the browser trusts that behind the browser it is really you. CSRF attack takes advantage of this trust.
The bad guys then perform actions on your behalf. 

The bad guy will first create a malicious request that mimics the real one. But of course the bad guy can't just perform this request himself, he needs someone else.
The bad guy then sends a fake link to a user who is already logged into the account. This might be within a message or email. 
The link then behind the scenes sends a request to the server to perform the malicious request.
So the server needs to know from where the request comes from. 

## Solution 
Use CSRF tokens. This token is generated randomly by the backend and sent to the browser to be stored in the cookies.
The backend also stores this token on the backend and compares it to a userID each time a request is performed.
And if we are using HTTPS, then the request that contains the token also can't be stolen by an attacker with something like wireshark.

Unlike [[cross-site scripting]], which exploits the trust a user has for a particular site, CSRF exploits the trust that a site has in a user's browser.

