Figgy does not maintain or manage any of its own credentials or keys, instead it offloads all authentication and 
authorization to your Identity Provider or to AWS. 

Figgy currently supports three main types of authentication. Regardless of which authentication method works best
for your use case, all three options enforce the following security best practices including:

- [x] Single sign on
- [x] Multi-factor authentication
- [x] Temporary session credentials for all Figgy activity with a max duration of 12 hours
- [x] Encrypted session storage


The three main types of SSO authentication are:

1. [Bastion](/docs/manual/figgy-cloud/bastion/)
1. [Google](/docs/manual/figgy-cloud/google/)
1. [OKTA](/docs/manual/figgy-cloud/okta/)

All of these enforce sign on through a single provider and do not require multiple sets of credentials to be maintained. 
For more details see [Figgy Cloud](/manual/figgy-cloud/).

## Local Session Caching

Figgy CLI will cache authenticated SSO sessions in its local encrypted 'lockbox' (`~/.figgy/vault/*`). 
Files in the lockbox are encrypted using symmetric encryption with a [fernet key](https://cryptography.io/en/latest/fernet/) 
generated by Figgy the first time the user runs Figgy. This key is stored in the user's OS Keychain under the name `figgy-encryption-key`
If a user has a valid active SSO Session, Figgy CLI will reuse the existing session to generate new 
STS credentials as needed. Figgy does not greedily generate sessions, instead sessions are generated as-needed to support requested CLI operations.

**Only temporary session credentials are stored in the Figgy Lockbox** 

## Local Password Storage

For Google and OKTA SSO configurations, the user's password will be saved in their local OS keychain under 
the `figgy` namespace. 

![Auth Keychain](/images/architecture/auth-keychain.png)

The Figgy CLI will attempt to retrieve these credentials on the user's behalf when existing cached SSO sessions have expired.
The frequency of this is dependant on SSO provider configurations. Organizations configured to use the [Bastion](/docs/manual/figgy-cloud/bastion/)
authentication provider do not require passwords and instead use AWS API Keys. These low-power keys are stored in the user's 
`~/.aws/credentials` file like all other AWS credentials. 

We **strongly recommend** enabling multi-factor authentication for Bastion configurations. 
