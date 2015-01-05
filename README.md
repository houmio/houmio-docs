# Transitioning from Houm.io 1.0

First, set your site recovery email address by editing the name of your site. Then, from this email address, request a migration of your site data to the new system. Send an email to help@houm.io and request for a migration.

Log in to your Houm.io bridge.

Upgrade your supervisord, let the installer overwrite your supervisor.conf:

    echo "deb http://http.debian.net/debian wheezy-backports main" | sudo tee -a /etc/apt/sources.list
    sudo apt-get update
    sudo apt-get -t wheezy-backports install "supervisor"

Replace your `/etc/supervisor/supervisord.conf` with this [supervisord.conf](supervisord.conf).

Add [houmio.conf](houmio.conf) to `/home/pi`. Replace `HOUMIO_SITEKEY` dummy value with your siteKey.

Install `houmio-bridge` and `houmio-driver-enocean`:

    cd
    npm install houmio/houmio-bridge
    npm install houmio/houmio-driver-enocean

Restart supervisor:

    sudo service supervisor restart

Your API prefix is `https://houmi.herokuapp.com/api/site/yoursecretsitekey`.