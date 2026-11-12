# 03 — Usuários (Grupo 5)

## 1. Usuários

Todas as 8 VMs têm o mesmo conjunto de usuários:

| Usuário | Quem é |
|:--|:--|
| administrador | Administrador (criado na instalação) |
| sarah.amorim | Sarah Amorim dos Santos |
| pedro.rocha | Pedro Henrique Cavalcante Rocha |
| arlan.montilares | Arlan Montilares de Oliveira Silva |
| thiago.luiz | Thiago Luiz da Silva |

Cada usuário tem diretório em `/home/<usuário>` e shell `/bin/bash`.

## 2. Criação (executada em cada VM)

```bash
for u in sarah.amorim pedro.rocha arlan.montilares thiago.luiz; do
  sudo useradd -m -s /bin/bash "$u"
  sudo passwd "$u"
done
```

Saída obtida:

<!--![Criação dos usuários](imagens/g5-pc1-vm1_useradd.png)-->

## 3. Verificação

```bash
getent passwd sarah.amorim pedro.rocha thiago.luiz arlan.montilares
ls -l /home
```

Saída obtida:

<!--![Verificação dos usuários](imagens/g5-pc1-vm1_getent_passwd.png)-->

## 4. VMs onde foi feito

| VM | Feito por | Verificado |
|:--|:--|:--:|
| g5-pc1-vm1 | Sarah Amorim dos Santos | [ ] |
| g5-pc1-vm2 | Sarah Amorim dos Santos | [ ] |
| g5-pc2-vm1 | Pedro Henrique Cavalcante Rocha | [ ] |
| g5-pc2-vm2 | Pedro Henrique Cavalcante Rocha | [ ] |
| g5-pc3-vm1 | Thiago Luiz da Silva | [ ] |
| g5-pc3-vm2 | Thiago Luiz da Silva | [ ] |
| g5-pc4-vm1 | Arlan Montilares de Oliveira Silva | [ ] |
| g5-pc4-vm2 | Arlan Montilares de Oliveira Silva | [ ] |
