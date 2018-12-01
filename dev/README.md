## Dev App

After deploying the app with ``docker-compose up -d``, retrieve the administrator credentials by executing the following command:

    $ docker exec -ti <container_name> cat /data/root/.tuleap_passwd
