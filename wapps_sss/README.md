## Sss Service

The sss service (i.e. Minio) auto-generates a set of access and secret keys. These can be found in the logs after starting the service. Once logged in to the web interface with these credentials, you can set your own keys.

To view the logs you have at least the following two options:

* Execute ``$ sudo docker logs sss_minio_1`` via comand line
* Browse to the logs of the ``sss_minio_1`` container in the dckr service (i.e. Portainer)
