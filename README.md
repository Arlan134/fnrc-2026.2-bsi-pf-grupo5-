# Projeto Final — Fundamentos de Redes de Computadores (BSI 2026.02)

## Grupo 5 — Rede virtualizada com 8 VMs

Rede /28 com 8 máquinas virtuais Ubuntu Server distribuídas em 4 PCs do laboratório, com IP estático, nomes padronizados e os mesmos usuários em todas as VMs.

### Integrantes

| Integrante | Usuário nas VMs |
|:--|:--|
| Sarah Amorim dos Santos | sarah.amorim |
| Pedro Henrique Cavalcante Rocha | pedro.rocha |
| Arlan Montilares de Oliveira Silva | arlan.montilares |
| Thiago Luiz da Silva | thiago.luiz |

### Dados da rede

| Item | Valor |
|:--|:--|
| Rede | 192.168.26.80/28 |
| Máscara | 255.255.255.240 |
| Endereços das VMs | 192.168.26.81 a 192.168.26.88 |
| Broadcast | 192.168.26.95 |
| Domínio | grupo5.bsi-26-2.maceio.lab |

### Documentação

| Arquivo | Conteúdo |
|:--|:--|
| [01-planejamento.md](01-planejamento.md) | Endereçamento, nomes, usuários e topologia |
| [02-criacao-das-vms.md](02-criacao-das-vms.md) | Hardware das VMs e instalação do Ubuntu Server |
| [03-usuarios.md](03-usuarios.md) | Criação dos usuários |
| [04-rede-netplan.md](04-rede-netplan.md) | Placa em Ponte e IP estático |
| [05-hostname-e-hosts.md](05-hostname-e-hosts.md) | Hostname e `/etc/hosts` |
| [06-testes.md](06-testes.md) | Testes de `ping`, `ssh` e resolução de nomes |

### Arquivos de apoio

- [configs/hosts](configs/hosts): bloco do `/etc/hosts` usado nas 8 VMs
- [configs/netplan/](configs/netplan/): arquivo Netplan de cada VM
- [validacao/](validacao/): saída do script de validação em cada VM
- [imagens/](imagens/): capturas de tela de evidência
