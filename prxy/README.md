# Prxy App

By default, all apps in this repository are reverse-proxied through this app. Additional configuration is only necessary in case you want to use this app to also reverse-proxy or load-balance apps *outside this Docker instance*. For this scenario, please make use of the file provider:

* Inside the file ``traefik.toml``, uncomment the lines inside the section ``[file]`` near the bottom of the file
* Copy the file ``rules.toml.default`` to ``rules.toml``
* Follow the instructions given inside the copied file

Note: Even with ``watch = true`` (which should instruct Traefik to reload on the fly as soon as the file ``rules.toml`` changes), Traefik does not reload automatically after file changes. Make sure to execute ``sudo docker-compose restart``.
