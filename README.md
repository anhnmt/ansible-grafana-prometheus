# ansible-grafana-prometheus

### Install ansible
```bash
python3 -m pip install --user ansible
```

Or use docker

```bash
docker compose up -d
```

### Install ansible collection
```bash
ansible-galaxy collection install -r requirements.yml
```

### SSH & pre check
```bash
ansible-playbook -i inventory.ini ssh.yml
```

### Install node_exporter
```bash
ansible-playbook -i inventory.ini node_exporter.yml
```

### Install prometheus
```bash
ansible-playbook -i inventory.ini prometheus.yml
```

### Install grafana
```bash
ansible-playbook -i inventory.ini grafana.yml
```

### Add grafana dashboard
1. Go to http://localhost:3000/dashboards
2. Click `News` button, `Import` -> Type ID dashboard -> Load -> Import

Dashboard ID example:
```
1860 # Node Exporter Full

15172 # Node Exporter for Prometheus Dashboard based on 11074

14282 # cadvisor-exporter
```

### Clear prometheus data
```bash
sudo rm -rf /var/lib/prometheus/*

systemctl restart prometheus.service
systemctl status prometheus.service
```