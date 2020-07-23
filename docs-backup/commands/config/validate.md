

## Validate

Validates the configurations defined in your `figgy.json` file exist in the targeted environment. The validate command
is ideal to use in your CICD pipline or as a pre-commit git hook to ensure users don't commit code without storing
their required configurations. 

This command is extra-useful when accompanied by the [--profile](/docs/commands/flags/profile/) flag during [CICD builds](/docs/user-guides/how-to/cicd-validation.html).


#### Successful Validation
<br/>![Validate](/docs/images/gifs/validate-success.gif)<br/>



#### Validation Failure
<br/>![Validate](/docs/images/gifs/validate-fail.gif)<br/>