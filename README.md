

# Primelist

![latest release](https://img.shields.io/github/release/source-saraiva/primelist) 
![license](https://img.shields.io/github/license/source-saraiva/primelist)  
![repo size](https://img.shields.io/github/repo-size/source-saraiva/primelist) 
![last commit](https://img.shields.io/github/last-commit/source-saraiva/primelist)

---

## 🌐 Navigation
[English](#-english) | [Português](#-português-pt) | [Français](#-français)

---

## 🌍 English

**Primelists** é uma colecção de listas de **domínios, endereços IP e números de telefone** usados para reforçar a segurança contra anúncios, tracking, malware e actores maliciosos.

Este repositório disponibiliza listas curadas que podem ser usadas em soluções como **Pi-hole**, firewalls (`firewalld`, `iptables`), sistemas de deteção de intrusões e outros ambientes de filtragem.

---

## Conteúdo

* **primelist\_domains.txt**
  Lista principal de domínios a bloquear (anúncios, tracking e malware).

* **primelist\_domains\_eval.txt**
  Lista de domínios em fase de avaliação. Estes são testados nos nossos servidores DNS públicos antes de serem promovidos para a lista principal, reduzindo falsos positivos.

* **primelist\_ips.txt**
  Lista principal de endereços IP considerados actores maliciosos, usada para proteger contra ataques de força bruta e outras ameaças de rede.

---

## Como Funciona

### Domínios

* Base inicial: [StevenBlack/hosts](https://raw.githubusercontent.com/StevenBlack/hosts/master/hosts).
* A lista é estendida com base na nossa própria identificação e análise.
* Os domínios passam pela lista de **avaliação** antes de integrarem a lista principal.

### IPs

* Recolha feita a partir de ataques de força bruta detectados em servidores próprios e de participantes, maioritariamente via **Fail2Ban**.
* Os IPs são publicados com **política de retenção de 90 dias**.
* O objectivo é partilhar inteligência de ameaças para reforçar a defesa colectiva.

---

## Como Usar

### Bloqueio de Domínios

Adicionar a seguinte lista ao Pi-hole ou outro bloqueador compatível:

* Lista principal:

  ```
  https://raw.githubusercontent.com/source-saraiva/primelists/refs/heads/main/primelist_domains.txt
  ```

  **Comentário sugerido:** `source-saraiva`

* Lista de avaliação:

  ```
  https://raw.githubusercontent.com/source-saraiva/primelists/refs/heads/main/primelist_domains_eval.txt
  ```

### Bloqueio de IPs

Para integrar os IPs na firewall, pode criar um script com `curl` ou `wget` que corre em `cron` e actualiza regularmente:

```bash
# Exemplo para firewalld
URL="https://raw.githubusercontent.com/source-saraiva/primelists/refs/heads/main/primelist_ips.txt"
curl -s $URL -o /tmp/primelist_ips.txt

# Aplica à zona access-denied
for ip in $(cat /tmp/primelist_ips.txt); do
  sudo firewall-cmd --permanent --zone=access-denied --add-source=$ip
done

sudo firewall-cmd --reload
```

---

## Notas

* Use estas listas com cuidado: listas demasiado agressivas podem bloquear tráfego legítimo.
* É recomendada a manutenção de uma *whitelist* para IPs/domínios confiáveis.
* A participação de mais utilizadores aumenta a precisão e reduz falsos positivos.

---

## Contribuições

Se quiser contribuir:

1. Submeta issues com sugestões de novos domínios/IPs.
2. Partilhe relatórios de falsos positivos para melhorar a curadoria.
3. Pode também propor *pull requests* com listas adicionais.

---
