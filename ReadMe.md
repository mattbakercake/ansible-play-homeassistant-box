# Ansible play to provision Homeassistant server

## Notes
* make sure ansible is up to date - community.docker at least v3.9.0 for docker_compose_v2 `ansible-galaxy collection list`
* update inventory file to point to correct host for installation
* determine device port zigbee coordinator is plugged into (see zigbee2mqtt docs) and update group_vars `zigbee_serial_device_port`
* run the play `ansible-playbook run.yaml --ask-vault-pass`
* there will be additional steps required on the host within th applications e.g. 
* * adding the node-red-contrib-home-assistant-websocket node to nodered pallette
* * install homeassistant mqtt integration and configure
* * install homeassistant sonoff integration and configure
* * install homeassistant Nodered integration
* * Configure the homeassistant HACS integration

## extra info
play pulls down roles from github to local ansible host before execting them on the target machine. steps of this play are:
* create self signed certificate  (for mqtt TLS)
* install docker
* provision homeassistant container
* provision eclipse-mosquitto mqtt container
* provision nodered container
* provision zigbee2mqtt container
