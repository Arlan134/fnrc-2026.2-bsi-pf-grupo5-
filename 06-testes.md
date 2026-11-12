# 06 — Testes e validação (Grupo 5)

## 1. Ping entre as VMs

Cada VM testa as outras 7 usando **IP**, **apelido** e **FQDN**. Exemplo manual:

```bash
ping -c 3 192.168.26.83
ping -c 3 g5-pc2-vm1
ping -c 3 g5-pc2-vm1.grupo5.bsi-26-2.maceio.lab
```

Para testar todas de uma vez, em cada VM (a tentativa para a própria VM pode ser ignorada):

```bash
for n in 81 82 83 84 85 86 87 88; do ping -c 3 192.168.26.$n; done

for h in g5-pc1-vm1 g5-pc1-vm2 g5-pc2-vm1 g5-pc2-vm2 g5-pc3-vm1 g5-pc3-vm2 g5-pc4-vm1 g5-pc4-vm2; do
  ping -c 3 "$h"
  ping -c 3 "$h.grupo5.bsi-26-2.maceio.lab"
done
```

Saída obtida em g5-pc1-vm1:

<!--![Ping da g5-pc1-vm1 para as outras VMs](imagens/g5-pc1-vm1_ping.png)-->

Matriz de resultados:

| Origem \ Destino | pc1-vm1 | pc1-vm2 | pc2-vm1 | pc2-vm2 | pc3-vm1 | pc3-vm2 | pc4-vm1 | pc4-vm2 |
|:--|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| g5-pc1-vm1 | — | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] |
| g5-pc1-vm2 | [ ] | — | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] |
| g5-pc2-vm1 | [ ] | [ ] | — | [ ] | [ ] | [ ] | [ ] | [ ] |
| g5-pc2-vm2 | [ ] | [ ] | [ ] | — | [ ] | [ ] | [ ] | [ ] |
| g5-pc3-vm1 | [ ] | [ ] | [ ] | [ ] | — | [ ] | [ ] | [ ] |
| g5-pc3-vm2 | [ ] | [ ] | [ ] | [ ] | [ ] | — | [ ] | [ ] |
| g5-pc4-vm1 | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | — | [ ] |
| g5-pc4-vm2 | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | [ ] | — |

## 2. SSH entre VMs de PCs diferentes

Cada integrante acessa com o próprio usuário. Exemplo:

```bash
ssh sarah.santos@g5-pc3-vm2
hostname     # já dentro da sessão remota
w            # mostra a sessão aberta e o IP de origem
exit
```

| Usuário | Origem | Destino | Resultado |
|:--|:--|:--|:--:|
| sarah.amorim | g5-pc1-vm1 | g5-pc3-vm2 | [ ] |
| pedro.rocha | <VM> | <VM de outro PC> | [ ] |
| thiago.luiz | <VM> | <VM de outro PC> | [ ] |
| arlan.montilares | <VM> | <VM de outro PC> | [ ] |

Saída obtida:

<!--![SSH da g5-pc1-vm1 para a g5-pc3-vm2](imagens/g5-pc1-vm1_ssh_g5-pc3-vm2.png)-->

## 3. Resolução de nomes

```bash
getent hosts g5-pc4-vm2
```

Saída obtida:

<!--![Resolução de nomes](imagens/g5-pc1-vm1_getent_hosts.png)-->

## 4. Script de validação

Em cada VM, editada a seção *CONFIGURAÇÃO DO GRUPO* do `validacao-pf.sh` (grupo = 5 e usuários do grupo) e executado:

```bash
sudo bash validacao-pf.sh | tee validacao-$(hostname -s).txt
```

Resultado esperado: nenhum item com **FALHOU**. As 8 saídas estão em [validacao/](validacao/):

| VM | Arquivo | Sem FALHOU |
|:--|:--|:--:|
| g5-pc1-vm1 | [validacao-g5-pc1-vm1.txt](validacao/validacao-g5-pc1-vm1.txt) | [ ] |
| g5-pc1-vm2 | [validacao-g5-pc1-vm2.txt](validacao/validacao-g5-pc1-vm2.txt) | [ ] |
| g5-pc2-vm1 | [validacao-g5-pc2-vm1.txt](validacao/validacao-g5-pc2-vm1.txt) | [ ] |
| g5-pc2-vm2 | [validacao-g5-pc2-vm2.txt](validacao/validacao-g5-pc2-vm2.txt) | [ ] |
| g5-pc3-vm1 | [validacao-g5-pc3-vm1.txt](validacao/validacao-g5-pc3-vm1.txt) | [ ] |
| g5-pc3-vm2 | [validacao-g5-pc3-vm2.txt](validacao/validacao-g5-pc3-vm2.txt) | [ ] |
| g5-pc4-vm1 | [validacao-g5-pc4-vm1.txt](validacao/validacao-g5-pc4-vm1.txt) | [ ] |
| g5-pc4-vm2 | [validacao-g5-pc4-vm2.txt](validacao/validacao-g5-pc4-vm2.txt) | [ ] |
