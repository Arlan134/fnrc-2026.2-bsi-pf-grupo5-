# 04 — Placa em Ponte e IP estático (Grupo 5)

## 1. Placa em Ponte no VirtualBox

Com a VM desligada: **Configurações → Rede → Adaptador 1 → Conectado a: Placa em Ponte**, selecionando a placa de rede física do PC.

<!--
![Bridge no PC1](imagens/pc1_virtualbox_bridge.png)

![Bridge no PC2](imagens/pc2_virtualbox_bridge.png)

![Bridge no PC3](imagens/pc3_virtualbox_bridge.png)

![Bridge no PC4](imagens/pc4_virtualbox_bridge.png)
-->

## 2. Netplan

Em cada VM:

```bash
ls /etc/netplan/
sudo nano /etc/netplan/00-installer-config.yaml   # nome do arquivo listado
```

A rede não tem gateway, então o arquivo não tem `routes` nem `nameservers`. Os arquivos de cada VM estão em [configs/netplan/](configs/netplan/).

| VM | IP / máscara | Arquivo |
|:--|:--|:--|
| g5-pc1-vm1 | 192.168.26.81/28 | [g5-pc1-vm1.yaml](configs/netplan/g5-pc1-vm1.yaml) |
| g5-pc1-vm2 | 192.168.26.82/28 | [g5-pc1-vm2.yaml](configs/netplan/g5-pc1-vm2.yaml) |
| g5-pc2-vm1 | 192.168.26.83/28 | [g5-pc2-vm1.yaml](configs/netplan/g5-pc2-vm1.yaml) |
| g5-pc2-vm2 | 192.168.26.84/28 | [g5-pc2-vm2.yaml](configs/netplan/g5-pc2-vm2.yaml) |
| g5-pc3-vm1 | 192.168.26.85/28 | [g5-pc3-vm1.yaml](configs/netplan/g5-pc3-vm1.yaml) |
| g5-pc3-vm2 | 192.168.26.86/28 | [g5-pc3-vm2.yaml](configs/netplan/g5-pc3-vm2.yaml) |
| g5-pc4-vm1 | 192.168.26.87/28 | [g5-pc4-vm1.yaml](configs/netplan/g5-pc4-vm1.yaml) |
| g5-pc4-vm2 | 192.168.26.88/28 | [g5-pc4-vm2.yaml](configs/netplan/g5-pc4-vm2.yaml) |

## 3. Aplicação e conferência

```bash
sudo netplan apply
ip -4 addr show enp0s3
ip route
```

Resultado esperado na VM1 do PC1: `192.168.26.81/28` em `enp0s3` e rota `192.168.26.80/28 dev enp0s3`.

Saída obtida em g5-pc1-vm1:

<!--
![IP da g5-pc1-vm1](imagens/g5-pc1-vm1_ip_addr.png)

![IP da g5-pc1-vm2](imagens/g5-pc1-vm2_ip_addr.png)

![IP da g5-pc2-vm1](imagens/g5-pc2-vm1_ip_addr.png)

![IP da g5-pc2-vm2](imagens/g5-pc2-vm2_ip_addr.png)

![IP da g5-pc3-vm1](imagens/g5-pc3-vm1_ip_addr.png)

![IP da g5-pc3-vm2](imagens/g5-pc3-vm2_ip_addr.png)

![IP da g5-pc4-vm1](imagens/g5-pc4-vm1_ip_addr.png)

![IP da g5-pc4-vm2](imagens/g5-pc4-vm2_ip_addr.png)
-->
