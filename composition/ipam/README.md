# About Ipam Wapp

The ipam wapp is based on [NetBox](https://github.com/netbox-community/netbox/)

# Notes

After deploying this wapp, you need to create a new user via the containers command line. Log in to your Portainer instance and select the container ``wapps_ipam_netbox_1``. Connect to the container's console, execute the following command and fill in the required pieces of info (username, email address and password):

``python3 manage.py createsuperuser``
