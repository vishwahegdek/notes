Command to run odoo

```bash
sudo docker run -d -p 8069:8069 \
  -v /home/vishwa/projects/odoo:/mnt/extra-addons \
  -e HOST=127.0.0.1 \
  -e USER=odoo \
  -e PASSWORD=odoo \
  --name odoo \
  odoo:latest
```

```bash
sudo docker run -d -p 8069:8069 \
  -v /home/vishwa/projects/odoo:/mnt/extra-addons \
  -e HOST=host.docker.internal \
  -e USER=odoo \
  -e PASSWORD=odoo \
  --add-host=host.docker.internal:host-gateway \
  --name odoo1 \
  odoo:latest
```