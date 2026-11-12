# 05 — Hostname e /etc/hosts (Grupo 5)

## 1. Hostname

Em cada VM, configurado o FQDN completo (exemplo na VM1 do PC1):

```bash
sudo hostnamectl set-hostname g5-pc1-vm1.grupo5.bsi-26-2.maceio.lab
hostname
cat /etc/hostname
```

| VM | FQDN configurado |
|:--|:--|
| g5-pc1-vm1 | g5-pc1-vm1.grupo5.bsi-26-2.maceio.lab |
| g5-pc1-vm2 | g5-pc1-vm2.grupo5.bsi-26-2.maceio.lab |
| g5-pc2-vm1 | g5-pc2-vm1.grupo5.bsi-26-2.maceio.lab |
| g5-pc2-vm2 | g5-pc2-vm2.grupo5.bsi-26-2.maceio.lab |
| g5-pc3-vm1 | g5-pc3-vm1.grupo5.bsi-26-2.maceio.lab |
| g5-pc3-vm2 | g5-pc3-vm2.grupo5.bsi-26-2.maceio.lab |
| g5-pc4-vm1 | g5-pc4-vm1.grupo5.bsi-26-2.maceio.lab |
| g5-pc4-vm2 | g5-pc4-vm2.grupo5.bsi-26-2.maceio.lab |

Saída obtida em g5-pc1-vm1:

<!--![Hostname da g5-pc1-vm1](imagens/g5-pc1-vm1_hostname.png)-->

## 2. /etc/hosts

Como a rede não tem servidor DNS, a resolução é local. O bloco abaixo (também em [configs/hosts](configs/hosts)) está no `/etc/hosts` das 8 VMs:

```text
# Grupo 5 - bsi-26-2 - grupo5.bsi-26-2.maceio.lab
192.168.26.81    g5-pc1-vm1.grupo5.bsi-26-2.maceio.lab    g5-pc1-vm1
192.168.26.82    g5-pc1-vm2.grupo5.bsi-26-2.maceio.lab    g5-pc1-vm2
192.168.26.83    g5-pc2-vm1.grupo5.bsi-26-2.maceio.lab    g5-pc2-vm1
192.168.26.84    g5-pc2-vm2.grupo5.bsi-26-2.maceio.lab    g5-pc2-vm2
192.168.26.85    g5-pc3-vm1.grupo5.bsi-26-2.maceio.lab    g5-pc3-vm1
192.168.26.86    g5-pc3-vm2.grupo5.bsi-26-2.maceio.lab    g5-pc3-vm2
192.168.26.87    g5-pc4-vm1.grupo5.bsi-26-2.maceio.lab    g5-pc4-vm1
192.168.26.88    g5-pc4-vm2.grupo5.bsi-26-2.maceio.lab    g5-pc4-vm2
```

## 3. Linha 127.0.1.1

Em cada VM, a linha `127.0.1.1` aponta para o nome da própria máquina. Exemplo na g5-pc1-vm1:

```text
127.0.1.1    g5-pc1-vm1.grupo5.bsi-26-2.maceio.lab    g5-pc1-vm1
```

## 4. Conferência

```bash
cat /etc/hosts
getent hosts g5-pc4-vm2
```

Saída obtida:

<!--![/etc/hosts da g5-pc1-vm1](imagens/g5-pc1-vm1_etc_hosts.png)-->
