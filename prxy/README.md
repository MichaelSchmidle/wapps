# Prxy App

In case you want to use this app to also reverse-proxy or load-balance apps *outside this Docker host*, make use of the file provider:

* Inside the file ``traefik.toml``, uncomment the lines inside the section ``[file]`` near the bottom of the file
* Copy the file ``rules.toml.default`` to ``rules.toml``
* Follow the instructions given inside the copied file
