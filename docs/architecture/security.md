
## Security

Figgy is security oriented and has been built with a focus on:

- [x] Availability & Resiliency
- [x] Observability
- [x] Privacy
- [x] Confidentiality

Here are some high-level guidelines on how Figgy supports these objectives. 

## Availability & Resiliency

- Figgy is built on top of highly available AWS services that have their own [AWS supported SLAs](https://aws.amazon.com/legal/service-level-agreements/).
Figgy does not require any custom infrastructure that has to be monitored.

- Figgy is serverless, which removes the need to manage, maintain, or patch infrastructure. The default 
configurations of Figgy are designed for pay-per-request or pay-as-you-go. As a result,
AWS will manage the scaling of components required to support Figgy and maintain high availability while
protecting from server overload or throttling.

- All non-cache database tables are configured with point-in-time recovery enabled by default.

## Observability

- Figgy is built with native AWS serverless components that have built-in AWS observability metrics such as:
    - AWS Cloudwatch Metrics
    - AWS Cloudwatch Logs
    - AWS Cloudtrail Logs
<br/>
<br/>

- Figgy has built-in Cloudwatch Alarms that will trigger and notify configured users through Slack or email
 of any exceptions encountered while Figgy performs its duties.

- Figgy's configuration & secret store is built on AWS Parameter Store which maintains its own versioned history for every stored value.

- Figgy maintains a complete historical log of all events that transpire in the Figgy ecosystem in its own `figgy-audit` 
DynamoDB Table.

- Figgy can be configured to log various critical events in the Figgy ecosystem to Slack. 

## Privacy & Confidentiality

- Figgy supports multi-factor authentication out of the box for all SSO deployment modes.

- Figgy enables secret owners to directly share their secrets with the applications that need
them and cut out the middle-man to reduce secret exposure.

- Figgy is designed from the ground up with a focus on the principal of least privilege. Figgy's default configurations 
follow these best practices. 

- Figgy enables organizations to create as many Figgy role types as desired. Each role type can be configured to have 
limited to access to any arbitrary section of the ParameterStore tree.

- Figgy supports creating and leveraging as many AWS KMS encryption keys as desired by organizations to protect and carve 
up sensitive data stored through Figgy.

- Figgy automatically encrypts all temporary secrets in its own local lockbox and stores long-lived sensitive user 
credentials in the default OS keychain for maximum protection.

