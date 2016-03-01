# prototype-cjdns-pi2

Prototype for cjdns on Raspberry Pi 2 forming a mesh network

This repository will track progress and hold documentation, scripts, benchmarking results and other findings along the way.

## Proposed setup

### Phase 1: Connect

- [ ] Flash two [Raspberry Pi 2's with OpenWrt 15.05](https://wiki.openwrt.org/toh/raspberry_pi_foundation/raspberry_pi)
- [ ] Install [MeshBox](https://github.com/SeattleMeshnet/meshbox) with `opkg update && opkg install luci-app-cjdns`
- [ ] Attach a [Pi 2](http://elinux.org/RPi_USB_Wi-Fi_Adapters) + [OpenWrt](https://forum.openwrt.org/viewtopic.php?id=37331) + [802.11s](http://devel.open80211s.narkive.com/8olWVgz9/802-11s-and-raspberry-pi)-compatible USB WiFi adapter (e.g. TL-WN722N) and [install firmware](https://wiki.debian.org/ath9k_htc)
- [ ] Configure network interface to run 802.11s [manually](https://wiki.openwrt.org/doc/howto/mesh.80211s) or through the MeshBox UI

### Phase 2: Range

- [ ] Swap out the N connector antenna on the radio to a directional antenna for range (e.g. TL-ANT2424B)
- [ ] Attach [long-range point-to-point antenna](https://www.ubnt.com/products/) (e.g. NanoStation M5)

### Phase 3: Hyperboria

- [ ] Connect one Pi 2 to the internet through the Ethernet port
- [ ] Through the MeshBox UI, peer the Pi 2 into [Hyperboria](https://www.fc00.org) by configuring a VPN tunnel with the cjdns UDP interface
- [ ] Make the Pi 2 a [gateway node to the internet](https://github.com/hyperboria/cjdns/blob/master/doc/tunnel.md)

### Phase 4: Access

- [ ] Set up the other Pi 2 as a [IPv6-only router and NAT gateway](https://github.com/hyperboria/cjdns/blob/master/doc/nat-gateway.md) for devices to connect and access both Hyperboria and internet resources (the latter over the point-to-point link, through the first Pi 2's internet gateway)
- [ ] Allow IPv4-only devices to connect by [tunneling IPv4 traffic through the IPv6 cjdns link](https://en.wikipedia.org/wiki/4in6)

## Relevant links

* https://github.com/openwrt-routing/packages
* http://raspberrypihq.com/how-to-turn-a-raspberry-pi-into-a-wifi-router/
* https://www.wifipineapple.com/

## Credits

* [The cjdns community](https://github.com/hyperboria)
* [The Layer 8 Network](http://layer8.network)
