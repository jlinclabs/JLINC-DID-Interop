A JLINC authorization capability (ZCAP) is a JSON-LD based document based on W3C recommendations for “Authorization Capabilities for Linked Data.“ It contains JLINC DIDs (referred to herein as DIDs and defined at https://did-spec.jlinc.org).

N.B. All of the issuing, delegating, and checking of signatures and metadata can be accomplished using https://github.com/jlinclabs/jlinc-zcap

At a minimum the ZCAP must contain DID’s for an issuer and an invoker, and appropriate digital signatures by the private keys referencing the DIDs, as well as purposes or actions for which the ZCAP provides authorization (described in a caveats array), and other data as defined in the ZCAP specification.

Assuming that we have two platforms that wish to partner with each other by facilitating seamless login to each other's platforms for their users, we'll call them platform A and platform B.

Use case - platform A delegates a capability to platform B or to an end user of platform B.

a. The service doing the delegating (the delegator, in this case platform A) must assign DIDs to each delegatee (their own user) or validate and register the DID offered by any delegatee, providing that it is a DID using the JLINC method or another DID method that all parties to the use case know how to resolve.

b. The delegator creates one or more purpose-specific ZCAP delegatable capability documents. The delegated capability is restricted to one or more particular actions, purposes, or access permissions with respect to platform B.

c. On demand and with proper authorization the delegator creates a capability document delegated to the delegatee, and optionally creates and transmits an invocation of that delegated document on behalf of the delegatee as its agent.

d. Either the delegator or platform B relying on the capability may revoke the capability at any time using the capability’s unique identifier.

e. The relying party (in this case platform B) or its agent checks that the invoking DID is still current, that the capability has not been revoked or become expired, checks all signatures and relevant data, and if all is correct grants the associated delegatee the purpose-specific access the capability has invoked.
