# home-network-config

Configuration for my home network.

## Home Assistant

The Compose file in `docker/` runs Home Assistant Container. The old vTuner and
nginx services are in the opt-in `legacy` profile.

From the repository root:

```sh
mkdir -p docker/config
chmod 700 docker/config
docker compose -f docker/docker-compose.yml config --quiet
docker compose -f docker/docker-compose.yml up -d homeassistant
```

Open `http://<host LAN address>:8123` and complete onboarding. Check
**Settings > Devices & services** for integrations found on the local network.
The `docker/config` directory is ignored by Git because Home Assistant stores
credentials and state there. Back it up privately.

The container uses host networking for local discovery, so port 8123 is
reachable on the host's network interfaces. Do not forward it from the router
without planning remote access and authentication. Home Assistant Container
does not include Supervisor or add-ons; run any required supporting service in
its own container. Update the pinned image tag deliberately after backing up
`docker/config`.
