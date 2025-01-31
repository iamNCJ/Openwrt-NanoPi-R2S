# Openwrt-NanoPi-R2S

Self Tuned Openwrt ([LEDE](https://github.com/coolsnowwolf/lede)) for NanoPi R2S

- SSR Plus
- Frp
- WireGaurd
- IPv6
- Docker
- other utilities

Please download the compiled binary in [release](https://github.com/iamNCJ/Openwrt-NanoPi-R2S/releases) or use the `.config` to compile one.

> The latest release enabled persistent `/var`, and to make all plugins work as expected, you have to run the following cmd:
> ```bash
> ln -s /var/etc/dnsmasq.conf.xxxxx /tmp/etc/dnsmasq.conf.xxxxx
> # xxxxx depends on the interface name of your network.
> ```
