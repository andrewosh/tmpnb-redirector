# Redirector for tmpnb

A simple service that redirects to hosts running tmpnb,
with load-balancing based on their current availability.

Run the service:

    python redirector.py

Add hosts to be considered for redirection:

    curl -X POST -d '{"host": "https://tmpnb.org"}' http://127.0.0.1:9001/hosts

You can remove instances with a DELETE request:

    curl -X DELETE -d '{"host": "https://tmpnb.org"}' http://127.0.0.1:9001/hosts

The server can also be passed a user identifier, which should subsequently map to a single notebook instance. If that notebook is no longer available, a new one should be launched and that mapping should be updated. 
