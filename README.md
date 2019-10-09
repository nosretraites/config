# NGINX config

From `nginx` subfolder
```
rsync -r . root@static.reformedesretraites.fr:/etc/nginx/ && ssh root@vps698331.ovh.net "nginx -T && systemctl restart nginx.service"
```


# Fabric server

```
# Install
apt-get install python3-venv
cd server
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# Service
scp destinie.service root@reformedesretraites.fr:/etc/systemd/system/destinie.service
systemctl daemon-reload && systemctl restart destinie && systemctl status destinie

# Continuous deployment
ssh root@reformedesretraites.fr -C "cd Destinie-2 && git pull && systemctl reload destinie && systemctl status destinie"
```
