# Openwrt-NanoPi-R2S

Self Tuned Openwrt ([LEDE](https://github.com/coolsnowwolf/lede)) for NanoPi R2S

- Tailscale
- Zerotire
- Cloudflare
- Frp
- WireGaurd
- IPv6
- Docker
- other utilities

Please download the compiled binary in [release](https://github.com/iamNCJ/Openwrt-NanoPi-R2S/releases) or use the `.config` to compile one.

> The latest release needs to run the following cmd to make all plugins work as expected:
> ```bash
> ln -s /var/etc/dnsmasq.conf.xxxxx /tmp/etc/dnsmasq.conf.xxxxx
> # xxxxx depends on the interface name of your network.
> ```
>
> An easier way is to add this in the boot script:
> ```bash
> if [ ! -d /tmp/etc ]; then
>     mkdir -p /tmp/etc
> fi
> if [ ! -e /tmp/etc/dnsmasq.conf.cfg01411c ]; then
>     ln -s /var/etc/dnsmasq.conf.cfg01411c /tmp/etc/dnsmasq.conf.cfg01411c
> fi
> ```
> 
