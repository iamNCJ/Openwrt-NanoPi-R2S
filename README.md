# Openwrt-NanoPi-R2S

Self Tuned Openwrt from [LEDE]() for NanoPi R2S

- Tailscale
- Cloudflare
- Frp
- WireGaurd
- SSR Plus
- Passwall
- Zerotier

Please download the compiled binary in [release](https://github.com/iamNCJ/Openwrt-NanoPi-R2S/releases).

## Remarks

`luci-app-tailscale` has a bug when compiling (not sure the actual source). It's related to the uci config system, where the actual config instance was moved from 'tailscale' to 'tailscale.settings'. Thus you need the following patch to make the app work:

```patch
--- feeds/luci/applications/luci-app-tailscale/root/etc/init.d/tailscale        2025-05-11 22:34:58.434208593 +0800
+++ ../openwrt-custom/package/luci-app-tailscale/root/etc/init.d/tailscale      2025-05-10 19:20:59.567148689 +0800
@@ -209,8 +209,8 @@
 
 start_service() {
        config_load 'tailscale'
-       config_foreach start_instance 'settings'
-       config_foreach custom_instance 'settings'
+       config_foreach start_instance 'tailscale'
+       config_foreach custom_instance 'tailscale'
 }
 
 stop_instance() {
@@ -245,7 +245,7 @@
 
 stop_service() {
        config_load 'tailscale'
-       config_foreach stop_instance 'settings'
+       config_foreach stop_instance 'tailscale'
 }
 
 reload_service() {
```

And sometimes if the network instantce is still not created, you can ssh onto your router and execure the follow command (after setting up tailscale in LuCI):

```bash
/etc/init.d/tailscale start
```

It's recommended to use `sh -x /etc/init.d/tailscale start` to check if the command is executing as expected.

After that, you probably needs to move tailscale network interface from its original firewall zone to wan's zone.
