A JLINC authorization capability (ZCAP) is a JSON-LD based document based on W3C recommendations for “Authorization Capabilities for Linked Data.“ It contains JLINC DIDs (referred to herein as DIDs and defined at https://did-spec.jlinc.org).

N.B. All of the issuing, delegating, and checking of signatures and metadata can be accomplished using https://github.com/jlinclabs/jlinc-zcap

At a minimum the ZCAP must contain DID’s for an issuer and an invoker, and appropriate digital signatures by the private keys referenced by the DIDs, as well as purposes or actions for which the ZCAP provides authorization (described in a caveats array), and other data as defined in the JLINC ZCAP specification.

Assume we have two platforms that wish to interoperate with each other by facilitating seamless login to each other's platforms for their users - we'll call them platform A and platform B.

Use case - platform A wishes to delegate a capability to its users to authenticate to platform B.

a. Platform A as the delegator must assign DIDs to each delegatee (their own users).

b. The delegator creates a parent capability document, restricted to one or more particular actions, purposes, or access permissions with respect to platform B. 

* The parent capability must be signed with the delegator's private signing key and persisted. 
* It must contain a unique ID, a target url (the appropriate platform B endpoint), a set of caveats (permissions being authorized), an issuer (platform A) object, and a proof section (the signature). 
* The issuer object must contain the issuer's DID, and its authorization endpoint - the API endpoint where the validity of the capability may be checked via its ID value.

c. On demand by and with proper authentication from its end user, the delegator creates a signed capability document, based on the parent capability, and delegated to the delegatee (platform A's end user). It then transmits an invocation of that delegated document to platform B's API endpoint, acting as the end user's agent.

d. The relying party (platform B) checks that the invoking DID is still current, that the capability has not been revoked or become expired, checks all signatures and relevant data, and if all is correct grants the associated delegatee the purpose-specific access the capability has invoked.

e. Either the delegator (platform A) or the relying party (platform B) may revoke the capability at any time using the capability’s unique identifier.

