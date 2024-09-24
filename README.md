# cRR Examples

This repository provides examples for how to achieve different outcomes targeted at containerized route reflector ("cRR") use cases. Examples contained herein do not construe recommendations but are available means to construct bespoke solutions for the particular requirements of various environments.

## Examples

### Using Kubernetes

* [Juniper/meshrr](https://github.com/Juniper/meshrr/tree/main?tab=readme-ov-file#examples)
  * Scaling to many route reflectors organized hierarchically and/or in mesh groups

### Using Docker

* [jrokeach/crr/docker/crpd_persistent_nftables](docker/crpd_persistent_nftables)
  * Juniper cRPD
  * `nftables` for container-level firewall
    * Configured via `docker compose` `volume` `bind` mount of file in same directory
    * `nftables` changes in running container can be saved to persistent storage, with limitations
  * `docker compose` style initialization
  * Layer 2 connectivity to physical network via dedicated interfaces from host VM/BMS
* [jrokeach/crr/docker/crpd_static_nftables](docker/crpd_static_nftables)
  * Juniper cRPD
  * `nftables` for container-level firewall
    * Configured via `docker compose` `config` stanza
    * No means of persisting an `nftables` change from the running container to persistent storage
  * `docker compose` style initialization
  * Layer 2 connectivity to physical network via dedicated interfaces from host VM/BMS

