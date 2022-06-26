# Run Code-Server on IPv6 VPS Hax.co.id

## Set WARP on IPv6 VPS

	$ wget -N https://raw.githubusercontents.com/fscarmen/warp/main/menu.sh && bash menu.sh

for more futher step, you can access https://wiki.hax.co.id/ipv6-servers/how-to-install-warp-on-ipv6-vps-for-enable-ipv4-access/

## Install Code-Server

	$ curl -fsSL https://code-server.dev/install.sh | sh

	$ code-server

if you want run as service

	$ systemctl enable --now code-server@$USER
	$ systemctl start code-server@$USER

```code-server``` will run to http://127.0.0.1:8080

Your password is in ```~/.config/code-server/config.yaml```

	$ cat ~/.config/code-server/config.yaml

## Deploy Code-Server to Cloudflare Tunnel

	$ wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb && dpkg -i cloudflared-linux-amd64.deb

	$ cloudflared tunnel --url http://127.0.0.1:8080

the output website will appears (https://xxx-xxx-xxx-xxx.trycloudflare.com) 

if you want ```cloudflared``` run in the background, you can use nohup command

	$ nohup cloudflared tunnel --url http://127.0.0.1:8080 &

the output of log will added to the ```nohup.out``` file, you can open with:

	$ cat nohup.out
