In docker-compose v3, there is a `depends-on` flag that states which service should run before another.

BUT it's important to note that this does NOT mean that the follow-up containers will wait until the higher up container is "ready". It just wait until it starts.

```
version: "2"
services:
  web:
    build: .
    ports:
      - "80:8000"
    depends_on:
      - "db"
  db:
    image: postgres
```
This doesn't guarantee that `web` will not run until `db` is ready to connect. This means `web` will start as soon as `db` has STARTED.


From the docs:

"You can control the order of service startup and shutdown with the depends_on option. Compose always starts and stops containers in dependency order, where dependencies are determined by depends_on, links, volumes_from, and network_mode: "service:...".

However, for startup Compose does not wait until a container is “ready” (whatever that means for your particular application) - only until it’s running. There’s a good reason for this."

The reason is that you might not want to depend on a few containers for the entire application to succeed. Workarounds are:

- Use a bash script to artificially force a container to wait until its dependencies are sucessfully running
- Control it at the application level


https://docs.docker.com/compose/startup-order/ 
