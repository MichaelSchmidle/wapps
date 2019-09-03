## Ipam-beta App

After running ``sudo docker-compose up -d``, you need to create a new user via the containers command line. Log in to your dckr app and select the container ``wapps_ipam-beta_netbox_1``. Connect to the container's console, execute the following command and fill in the required pieces of info (username, email address and password):

``python3 manage.py createsuperuser``
