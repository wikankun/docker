# Choosing an image
https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html

# Define a local data directory
To fill `LOCAL_WORKING_DIR` in .env
Set permissions for the container:
```
sudo chown -R 1000 ${LOCAL_WORKING_DIR}
```

# Generate an access token
To fill `ACCESS_TOKEN` in .env
```
import IPython as IPython
hash = IPython.lib.passwd("S-E-C-R-E-T")
print(hash)
```
Or you can use the script `python3 generate_token.py -p S-E-C-R-E-T`

# Your jupyter notebook url (if you're using traefik)
To fill `JUPYTER_URL` in .env
