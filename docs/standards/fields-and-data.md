# Fields and Data

Here we define some standards for data structures and common fields.

## IDs

Keep simple, distributed systems cannot handle incremental IDs, so you can use both patterns explained bellow:

1. `UNIX_TIME_STAMP_SECONDS-RANDOM_STRING`
2. UUIDv4, UUIDv5

## Error Handling

1. Always put an **errid** on every generated error