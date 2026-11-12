# 02 — Criação das VMs (Grupo 5)

## 1. Hardware de cada VM

| Item | Valor |
|:--|:--|
| Sistema | Ubuntu Server 22.04.5 LTS (`ubuntu-22.04.5-live-server-amd64.iso`) |
| CPU | 1 |
| RAM na instalação |  MB |
| RAM após a instalação e a primeira atualização |  MB |
| Disco | 32 GB, VDI, alocação dinâmica |
| Placa de rede na instalação | NAT |
| Pasta da ISO (Windows) | `C:\2026.2\BSI\VM\original` |
| Pasta das VMs (Windows) | `C:\2026.2\BSI\VM\grupo05` |

## 2. VMs do grupo

| PC | VM no VirtualBox / hostname | Criada por |
|:--:|:--|:--|
| PC1 | g5-pc1-vm1 | Sarah Amorim dos Santos |
| PC1 | g5-pc1-vm2 | Sarah Amorim dos Santos |
| PC2 | g5-pc2-vm1 | Pedro Henrique Rocha Cavalcante |
| PC2 | g5-pc2-vm2 | Pedro Henrique Rocha Cavalcante |
| PC3 | g5-pc3-vm1 | Thiago Luiz da Silva |
| PC3 | g5-pc3-vm2 | Thiago Luiz da Silva |
| PC4 | g5-pc4-vm1 | Arlan Montilares de Oliveira da Slva |
| PC4 | g5-pc4-vm2 | Arlan Montilares de Oliveira da Slva |

## 3. Instalação do Ubuntu Server

Seguindo o Roteiro 01, com estes ajustes:

- Nome da VM no VirtualBox e **Your server's name** no instalador: o hostname curto (ex.: `g5-pc1-vm1`).
- Usuário administrador: `administrador`, com a senha padrão do laboratório.
- **Install OpenSSH Server** marcado.
- Placa de rede em **NAT** durante toda a instalação.

<!--![Configuração da VM no VirtualBox](imagens/g5-pc1-vm1_virtualbox_config.png)-->

<!--![Instalador com OpenSSH marcado](imagens/g5-pc1-vm1_instalador_openssh.png)-->

## 4. Atualização e utilitários (ainda em NAT)

```bash
sudo apt update
sudo apt install -y net-tools traceroute
```

Saída obtida:
<!---->

<!--![Atualização e instalação dos utilitários](imagens/g5-pc1-vm1_apt.png)-->

## 5. Script de validação

```bash
wget https://raw.githubusercontent.com/alaelson/fnrc_bsi_2026.2/main/projeto-final/validacao-pf.sh
ls -l validacao-pf.sh
```

Saída obtida:

<!---->

## 6. Redução de memória

Com a VM desligada, após a primeira atualização, a RAM foi reduzida de 1536 MB para 512 MB (Configurações → Sistema → Memória Básica).

<!--![RAM reduzida para 512 MB](imagens/g5-pc1-vm1_ram_512.png)-->

## 7. Clonagem

<!--<Se alguma VM foi clonada, registre aqui qual foi e que a opção de gerar novos endereços MAC foi marcada. Se não houve clonagem, escreva "Nenhuma VM foi clonada" e apague as linhas de instrução.>-->
