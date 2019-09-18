# Logging

Logs are powerful and must be used not only as applications shout, but to know what the application is doing and useful information to make the runtime clear. We need to agree on some standards and practices to have a common logging data set.

**Standards**

1. Any application must follow the **bunyan** (npm package) standards
2. All log fields must be notated as `camelCase`
3. Common fields:
	1. Errors must be under the **error** property
	2. Requests must be under the **request** property
	2. Responses must be under the **response** property

**Unleash the distributed tracing**

Logs can be used to build graphs and graphs can lead to a powerful distributed tracing.

1. About jobs:
	1. Must be under the **jobs** property
	2. Each item must be an object and have the job's ID
	3. Always try to put the job's streams and consumer groups
2. About gRPC
	1. Always put **callid** on metadata
3. About errors:
	1. Must have an **errid** property