# gRPC

Any error response will be folllowed by metadata with two fields:

* **errno** - The error's code.
* **errid** - Any "traceable" error thrown by the endpoint will have this field and clients can use to ask for the error tracing, normally this field will appear on internal errors.