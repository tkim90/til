# Web Service vs Http

Both `web service` and `http` are protocols for computers to communicate.

A `protocol` is a set of rules that people agreed to that two entities will need to talk to each other.

### Web Service
- Helps two `machines` communicate `over a network`.
- Any service that uses SOAP implementation.
- Uses XML as the payload format.
- "A Web service is merely an API wrapped in HTTP" (https://medium.com/@programmerasi/difference-between-api-and-web-service-73c873573c9d)

### HTTP
- Helps two `applications` communicate `over a network`, which might or might not be different machines.
- Any service that uses HTTP implementation. 
- Uses JSON as the payload format.
- APIs use HTTP, which is not always web based (example: App A using API from App B, but both sit in the same machine).
