## Referral Link Checkout Testing

The /checkout/ endpoint showed unusual session handling. Referral links
(including fake codes like /checkout/fakecode123456) would sometimes
load a dashboard without asking for credentials. This happened across
different accounts and browsers even with fresh sessions.

This behavior was inconsistent. On retesting with completely clean
browser sessions, the endpoint correctly redirected unauthenticated
users to the login page. The earlier access was likely from session
data persisting in the browser.

The inconsistency itself is worth noting, session cleanup may not be
immediate. But no reliable authentication bypass was found.

## Steps to Reproduce (Inconsistent)

1. Open a referral link (real or fake) in incognito
2. Sometimes the page loads a dashboard without login
3. Sometimes it redirects to login page
4. No reliable trigger found, behavior changed between tests.

Result: Authentication enforced succesfully, Couldn't by pass. 