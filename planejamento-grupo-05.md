# Planejamento (Grupo 5)

**INSTITUTO FEDERAL DE EDUCAÇÃO, CIÊNCIA E TECNOLOGIA DE ALAGOAS (IFAL) — Campus Maceió**

- **Curso:** Bacharelado em Sistemas de Informação (BSI)
- **Disciplina:** Fundamentos de Redes de Computadores
- **Professor:** Alaelson de Castro Jatobá Neto
- **Turma:** bsi-26-2 · **Grupo:** 5
- **Apresentação:** /12/2026
- **Data deste relatório:** 12/11/2026

## 1. Identificação do grupo

| Integrante | Usuário nas VMs | PC / VMs de responsabilidade |
|:--|:--|:--|
| Sarah Amorim dos Santos | sarah.santos | 1 |
| Pedro Henrique Cavalcante Rocha | pedro.rocha> | 2 |
| Thiago Luiz | thiago.luiz> | 3 |
| Arlan Montilares | arlan.montilares> | 4 |

Cada VM também tem o usuário `administrador`.

## 2. Cálculo da sub-rede

O Grupo X usa a sub-rede `192.168.26.(16 × X)/28`. Para X = 5: 16 × 5 = 80.

| Item | Valor |
|:--|:--|
| Rede | 192.168.26.80/28 |
| Máscara | 255.255.255.240 |
| Endereço de rede | 192.168.26.80 |
| Primeiro endereço útil | 192.168.26.81 |
| Último endereço útil | 192.168.26.94 |
| Broadcast | 192.168.26.95 |
| Total de endereços | 16 (2⁴, pois 32 − 28 = 4 bits de host) |
| Endereços úteis | 14 (16 − rede − broadcast) |
| Usados pelas VMs | 8 (.81 a .88) |
| Livres | 6 (.89 a .94) |
| Gateway | Não há (rede isolada) |

## 3. Domínio e nomes

- Domínio: `grupo5.bsi-26-2.maceio.lab`
- Hostname curto: `g5-pcY-vmZ`
- FQDN: `g5-pcY-vmZ.grupo5.bsi-26-2.maceio.lab`

## 4. Tabela de endereçamento

| VM | PC | Hostname | Interface / modo | IP / máscara | FQDN |
|:--:|:--:|:--|:--|:--|:--|
| VM1 | PC1 | g5-pc1-vm1 | enp0s3 · Bridge | 192.168.26.81/28 | g5-pc1-vm1.grupo5.bsi-26-2.maceio.lab |
| VM2 | PC1 | g5-pc1-vm2 | enp0s3 · Bridge | 192.168.26.82/28 | g5-pc1-vm2.grupo5.bsi-26-2.maceio.lab |
| VM3 | PC2 | g5-pc2-vm1 | enp0s3 · Bridge | 192.168.26.83/28 | g5-pc2-vm1.grupo5.bsi-26-2.maceio.lab |
| VM4 | PC2 | g5-pc2-vm2 | enp0s3 · Bridge | 192.168.26.84/28 | g5-pc2-vm2.grupo5.bsi-26-2.maceio.lab |
| VM5 | PC3 | g5-pc3-vm1 | enp0s3 · Bridge | 192.168.26.85/28 | g5-pc3-vm1.grupo5.bsi-26-2.maceio.lab |
| VM6 | PC3 | g5-pc3-vm2 | enp0s3 · Bridge | 192.168.26.86/28 | g5-pc3-vm2.grupo5.bsi-26-2.maceio.lab |
| VM7 | PC4 | g5-pc4-vm1 | enp0s3 · Bridge | 192.168.26.87/28 | g5-pc4-vm1.grupo5.bsi-26-2.maceio.lab |
| VM8 | PC4 | g5-pc4-vm2 | enp0s3 · Bridge | 192.168.26.88/28 | g5-pc4-vm2.grupo5.bsi-26-2.maceio.lab |

## 5. Bloco do `/etc/hosts` (igual nas 8 VMs)

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

Em cada VM, a linha `127.0.1.1` aponta para a própria máquina. Exemplo na VM1:

```text
127.0.1.1    g5-pc1-vm1.grupo5.bsi-26-2.maceio.lab    g5-pc1-vm1
```

## 6. Netplan (modelo)

Exemplo para a VM1 (`g5-pc1-vm1`). Em cada VM, só muda o endereço em `addresses`, conforme a tabela da seção 4.

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: false
      addresses:
        - 192.168.26.81/28
```

A rede não tem gateway, por isso não há `routes` nem `nameservers`.

## 7. Usuários

Criados da mesma forma nas 8 VMs:

```bash
for u in sarah.santos <usuario2> <usuario3> <usuario4>; do
  sudo useradd -m -s /bin/bash "$u"
  sudo passwd "$u"
done
```

## 8. Topologia

### Topologia física

4 PCs do laboratório, cada um com 2 VMs ligadas ao switch pelo modo Placa em Ponte.

<!--![Topologia física do Grupo 5](imagens/topologia-fisica-grupo5.png)-->

### Topologia lógica

As 8 VMs estão no mesmo segmento 192.168.26.80/28 e se encontram pelo nome via `/etc/hosts`.

<!--![Topologia lógica do Grupo 5](imagens/topologia-logica-grupo5.png)-->

```text
Switch do laboratório (172.20.20.0/22)
 ├── PC1 ── g5-pc1-vm1 (.81)   g5-pc1-vm2 (.82)
 ├── PC2 ── g5-pc2-vm1 (.83)   g5-pc2-vm2 (.84)
 ├── PC3 ── g5-pc3-vm1 (.85)   g5-pc3-vm2 (.86)
 └── PC4 ── g5-pc4-vm1 (.87)   g5-pc4-vm2 (.88)
```
