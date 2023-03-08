# Homelab

This is a special project that allows you to expose your containers through Cloudlflare Tunnels.

## How to use

1. You will need to create a tunnel and pick the respective token for the tunnel.

![This image shows a Cloudflare Tunnel homepage with a tunnel already configured.](/assets/images/cloudflare-tunnels-01.png "Cloudflare Tunnels Home page")

1. Add your tunnel token to `./.env` file as `CF_TUNNEL_TOKEN` key. Check `./.env.example` for an example.


3. Add `10.0.0.0/16` as private network to your tunnel which is set in `./docker-compose.yml` file.

![This image shows the Cloudflare Tunnel Private Network page with a private network already configured.](/assets/images/cloudflare-tunnels-02.png "Cloudflare Tunnels Private Network page")

4. Run `docker compose up -d` to start your service.

## How add services

Every service must be attached to the `homelab_private` network for allowing the tunnel connection.

After that, you will need to add a Public Hostname in your tunnel configuration.

![This image shows the Cloudflare Tunnel Public Hostname page](/assets/images/cloudflare-tunnels-03.png "Cloudflare Tunnels Public Hostname page")

In the public hostname section, you need to configure a full URL to be the tunnel public endpoint. 

In the service section, you will need to configure choose a protocol and the container address. You can use `docker container inspect` to check the container IP address or use the docker hostname resolution. Also, if you can define a custom hostname through [aliases](https://docs.docker.com/compose/compose-file/#aliases) or use the container name.:

![This image shows the Cloudflare Tunnel Public Hostname page](/assets/images/cloudflare-tunnels-04.png "Cloudflare Tunnels Public Hostname page")