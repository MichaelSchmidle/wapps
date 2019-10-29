# About Ipam Wapp

The ipam wapp is based on [NetBox](https://github.com/netbox-community/netbox/)

# Notes

After deploying this wapp, you need to create a new user via the containers command line. Inside Portainer, select the container ``${NAME}_netbox_1``. Connect to the container's console, execute the following command and fill in the required pieces of info (username, email address and password):

``python3 manage.py createsuperuser``
