### Instantiation of example
```bash
git clone https://github.com/jrokeach/crr.git
cd crr/docker/crpd_static_nftables/
docker compose up -d
```

### Example cRPD Configuration
```bash
docker exec -it rr-crpd-1 cli
```

```
request system license add terminal
# Paste license, CTRL+D

configure

set system services ssh root-login deny
set interfaces lo0 unit 0 family inet address 10.0.0.0/32
set routing-options autonomous-system 65000
set protocols bgp group RR-CLIENTS type internal
set protocols bgp group RR-CLIENTS cluster 10.0.0.0
set protocols bgp group RR-CLIENTS allow 0.0.0.0/0
set protocols ospf area 0.0.0.0 interface lo0.0 passive
set protocols ospf area 0.0.0.0 interface eth1 interface-type p2p
set protocols ospf area 0.0.0.0 interface eth0 interface-type p2p

commit and-quit
exit
```