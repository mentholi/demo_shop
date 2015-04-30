# demo_shop
Demo shop for giosg Live. Contains some dummy pages and simple shopping cart.

# Development and local install
* Clone this repo
* Create virtualenv
* pip install -r requirements.txt
* Create local_settings.py file, see https://github.com/mentholi/demo_shop/blob/master/deploy/local_settings.py.template for reference.
* ./manage.py runserver
* Profit!

# Deployment to production
* Clone this repo
* Create virtualenv
* pip install -r requirements.txt
* pip install fabric
* Create local_settings.py file, see https://github.com/mentholi/demo_shop/blob/master/deploy/local_settings.py.template for reference.
* Make sure that your local_settings.py contains the FABRIC settings dict. See example below.
* run `fab all` to setup server and deploy new version of code. To deploy only new code run `fab deploy`. Run `fab` for list of all commands.
* Profit!

# Fabric settings example
```python
FABRIC = {
    "SSH_USER": "root", # SSH username
    "SSH_PASS":  "your secure ssh password, don't commmit this! :) ", # SSH password (consider key-based authentication)
    "HOSTS": ['123.123.123.123'], # List of hosts to deploy to
    "VIRTUALENV_HOME":  "/var/sites", # Absolute remote path for virtualenvs
    "PROJECT_NAME": "giosg_demo_shop", # Unique identifier for project
    "REQUIREMENTS_PATH": "requirements.txt", # Path to pip requirements, relative to project
    "GUNICORN_PORT": 8000, # Port gunicorn will listen on
    "LOCALE": "en_US.UTF-8", # Should end with ".UTF-8"
    "LIVE_HOSTNAME": "somedomain.com", # Host for public site.
    "REPO_URL": "https://github.com/mentholi/demo_shop.git", # Git or Mercurial remote repo URL for the project
    "DB_PASS": "Database password, don't commit this!", # Live database password
    "ADMIN_PASS": "Admin password for the app, don't commit this either! :) ", # Live admin user password
    "SECRET_KEY": 'super secret key, keep this private!',
    "NEVERCACHE_KEY": 'Never cache key',
}
```