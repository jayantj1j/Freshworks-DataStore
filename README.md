# Freshworks-DataStore
Built  a file based key value datastore in python for CRD operations
This data store is meant to be used as a local storage for one single process on one
op. The data store must be exposed as a library to clients that can instantiate a class and work
with the data store.
The data store will support the following functional requirements.

1. It can be initialized using an optional file path. If one is not provided, it will reliably
create itself in a reasonable location on the laptop.
A new key-value pair can be added to the data store using the Create operation. The key
is always a string - capped at 32chars. The value is always a JSON object - capped at
16KB.
If Create is invoked for an existing key, an appropriate ensur must be returned.
A Read operation on a key can be performed by providing the key, and receiving the
value in response, as a JSON object.
A Delete operation can be performed by providing the key.
Every key supports setting a Time-To-Live property when it is created. This property is
cional. If provided, it will be evaluated as an integer defining the number of seconds
the key must be retained in the data store. Once the Time-To-Live for a key has expired,
the key will no longer be available for Read or Delete operations.
Appropriate error responses must always be returned to a client if it uses the data store in
unexpected ways or breaches any limits.

The data store will also support the following non-functional requirements.
The size of the file storing data must never exceed 1GB.
More than one client process cannot be allowed to use the same file as a data store at amy
given time.
A client process is allowed to access the data sto

The data store must therefore be thread-safe.
The client will bear as little memory costs as possible to use this data store, while
deriving maximum performance with respect to response times for accessing the data
store
