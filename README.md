Excelente ideia 👍
Assim fica fácil navegar entre as línguas no próprio GitHub.
Montei o README em **Markdown completo**, com **menu de navegação no topo** e **links de retorno ao menu no final de cada secção**.

---

```markdown
# primelist

![latest release](https://img.shields.io/github/release/source-saraiva/primelist) 
![license](https://img.shields.io/github/license/source-saraiva/primelist)  
![repo size](https://img.shields.io/github/repo-size/source-saraiva/primelist) 
![last commit](https://img.shields.io/github/last-commit/source-saraiva/primelist)

---

## 🌐 Navigation
[English](#-english) | [Português](#-português-pt) | [Français](#-français)

---

## 🇬🇧 English

**primelist** is a curated collection of **domains, IP addresses, and phone numbers** used to strengthen security against ads, tracking, malware, and malicious actors.  

### 📂 Contents
- **primelist_domains.txt** — main list of domains to block (ads + tracking + malware).  
- **primelist_domains_eval.txt** — evaluation list of domains under review before promotion to the main list.  
- **primelist_ips.txt** — main list of IP addresses identified as bad actors (brute force, abuse, etc.).  

### ⚙️ How It Works
- **Domains**: start with [StevenBlack/hosts](https://raw.githubusercontent.com/StevenBlack/hosts/master/hosts) as a base and extend with our own analysis. Domains are tested on our public DNS servers via the evaluation list before promotion.  
- **IPs**: collected from brute-force attempts detected on our own and participant servers (mainly via *Fail2Ban*). Published with a **90-day retention policy**.  

### 🚀 How to Use
- **Domains**  
  Add to Pi-hole or compatible blockers:  
```

[https://raw.githubusercontent.com/source-saraiva/primelist/refs/heads/main/primelist\_domains.txt](https://raw.githubusercontent.com/source-saraiva/primelist/refs/heads/main/primelist_domains.txt)

```
Evaluation list:  
```

[https://raw.githubusercontent.com/source-saraiva/primelist/refs/heads/main/primelist\_domains\_eval.txt](https://raw.githubusercontent.com/source-saraiva/primelist/refs/heads/main/primelist_domains_eval.txt)

````

- **IPs**  
Example for `firewalld`:  
```bash
URL="https://raw.githubusercontent.com/source-saraiva/primelist/refs/heads/main/primelist_ips.txt"
curl -s $URL -o /tmp/primelist_ips.txt

for ip in $(cat /tmp/primelist_ips.txt); do
  sudo firewall-cmd --permanent --zone=access-denied --add-source=$ip
done

sudo firewall-cmd --reload
````

### 🤝 Contributing

* Report new domains/IPs via issues.
* Flag false positives to improve accuracy.
* Submit pull requests with new lists.

[⬆️ Back to top](#-navigation)

---

## 🇵🇹 Português (PT)

**primelist** é uma colecção de **domínios, endereços IP e números de telefone** usada para reforçar a segurança contra anúncios, tracking, malware e actores maliciosos.

### 📂 Conteúdo

* **primelist\_domains.txt** — lista principal de domínios a bloquear (anúncios + tracking + malware).
* **primelist\_domains\_eval.txt** — lista de domínios em avaliação antes de serem promovidos.
* **primelist\_ips.txt** — lista principal de endereços IP considerados *bad actors* (ataques de força bruta, abuso, etc.).

### ⚙️ Como Funciona

* **Domínios**: base inicial em [StevenBlack/hosts](https://raw.githubusercontent.com/StevenBlack/hosts/master/hosts), estendida com análise própria. Os domínios passam pela lista de avaliação nos nossos servidores DNS públicos.
* **IPs**: recolhidos de ataques de força bruta detectados em servidores próprios e de participantes (maioritariamente via *Fail2Ban*). Publicados com **retenção de 90 dias**.

### 🚀 Como Usar

* **Domínios**
  Adicionar ao Pi-hole ou bloqueadores compatíveis:

  ```
  https://raw.githubusercontent.com/source-saraiva/primelist/refs/heads/main/primelist_domains.txt
  ```

  Lista de avaliação:

  ```
  https://raw.githubusercontent.com/source-saraiva/primelist/refs/heads/main/primelist_domains_eval.txt
  ```

* **IPs**
  Exemplo para `firewalld`:

  ```bash
  URL="https://raw.githubusercontent.com/source-saraiva/primelist/refs/heads/main/primelist_ips.txt"
  curl -s $URL -o /tmp/primelist_ips.txt

  for ip in $(cat /tmp/primelist_ips.txt); do
    sudo firewall-cmd --permanent --zone=access-denied --add-source=$ip
  done

  sudo firewall-cmd --reload
  ```

### 🤝 Contribuições

* Reportar novos domínios/IPs via issues.
* Indicar falsos positivos para reduzir bloqueios indevidos.
* Submeter *pull requests* com listas adicionais.

[⬆️ Voltar ao topo](#-navigation)

---

## 🇫🇷 Français

**primelist** est une collection de **domaines, adresses IP et numéros de téléphone** utilisée pour renforcer la sécurité contre les publicités, le tracking, les malwares et les acteurs malveillants.

### 📂 Contenu

* **primelist\_domains.txt** — liste principale des domaines à bloquer (publicités + tracking + malwares).
* **primelist\_domains\_eval.txt** — liste d’évaluation des domaines en cours de validation.
* **primelist\_ips.txt** — liste principale des adresses IP considérées comme *bad actors* (attaques par force brute, abus, etc.).

### ⚙️ Fonctionnement

* **Domaines** : base sur [StevenBlack/hosts](https://raw.githubusercontent.com/StevenBlack/hosts/master/hosts), enrichie par notre propre analyse. Les domaines passent par la liste d’évaluation testée sur nos serveurs DNS publics.
* **IPs** : collectées à partir d’attaques par force brute détectées sur nos serveurs et ceux des participants (principalement via *Fail2Ban*). Publiées avec une **politique de rétention de 90 jours**.

### 🚀 Utilisation

* **Domaines**
  À ajouter dans Pi-hole ou tout autre bloqueur compatible :

  ```
  https://raw.githubusercontent.com/source-saraiva/primelist/refs/heads/main/primelist_domains.txt
  ```

  Liste d’évaluation :

  ```
  https://raw.githubusercontent.com/source-saraiva/primelist/refs/heads/main/primelist_domains_eval.txt
  ```

* **IPs**
  Exemple pour `firewalld` :

  ```bash
  URL="https://raw.githubusercontent.com/source-saraiva/primelist/refs/heads/main/primelist_ips.txt"
  curl -s $URL -o /tmp/primelist_ips.txt

  for ip in $(cat /tmp/primelist_ips.txt); do
    sudo firewall-cmd --permanent --zone=access-denied --add-source=$ip
  done

  sudo firewall-cmd --reload
  ```

### 🤝 Contribuer

* Signaler de nouveaux domaines/IPs via issues.
* Rapporter les faux positifs pour améliorer la précision.
* Proposer des *pull requests* avec de nouvelles listes.

[⬆️ Retour en haut](#-navigation)

