## Лабораторная номер 2
# Конфигурация clab

Для работы был написан yaml файл, который задет конфигурацию пк и роутеров

```                                                        
name: lab2
mgmt:
    network: mgmt-net
    ipv4-subnet: 192.168.100.0/24
topology:
    kinds:
        vr-ros:
            image: vrnetlab/vr-routeros:6.47.9
        linux:
            image: ghcr.io/hellt/network-multitool
    nodes:
        R01_msk:
            kind: vr-ros
            mgmt-ipv4: 192.168.100.2
        R02_brl:
            kind: vr-ros
            mgmt-ipv4: 192.168.100.3
        R03_frt:
            kind: vr-ros
            mgmt-ipv4: 192.168.100.4
        PC1:
            kind: linux
            mgmt-ipv4: 192.168.100.5
        PC2:
            kind: linux
            mgmt-ipv4: 192.168.100.6
        PC3:
            kind: linux
            mgmt-ipv4: 192.168.100.7
    links:
        - endpoints: ["R01_msk:eth2", "R02_brl:eth2"]
        - endpoints: ["R01_msk:eth3", "R03_frt:eth3"]
        - endpoints: ["R01_msk:eth4", "PC1:eth2"]
        - endpoints: ["R02_brl:eth3", "R03_frt:eth2"]
        - endpoints: ["R02_brl:eth4", "PC2:eth4"]
        - endpoints: ["R03_frt:eth4", "PC3:eth2"]
```
