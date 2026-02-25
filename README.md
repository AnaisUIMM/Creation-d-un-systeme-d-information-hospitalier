# 🏥 Projet Réseau Hospitalier — Architecture & Sécurisation  

Ce dépôt contient l’ensemble du travail réalisé dans le cadre du projet de conception d’un **système d’information hospitalier complet**, incluant l’architecture réseau, la sécurisation, la segmentation, la DMZ, le SOC, les plans d’adressage, ainsi que les configurations des équipements.

---

## 📌 Objectifs du projet
- Concevoir une **architecture réseau robuste**, segmentée et scalable.  
- Garantir la **haute disponibilité** des services critiques hospitaliers.  
- Mettre en place une **sécurisation avancée** : VLAN, ACL, firewall, bastion, PAW, SOC.  
- Documenter l’ensemble du SI : schémas, matrices de flux, configurations, plan d’adressage.  
- Implémenter une **infrastructure réaliste** dans Packet Tracer.

---

## 🏗️ Architecture du Système d’Information

### 🔹 Répartition des équipements
Chaque bâtiment (Urgences, Bloc, Hospitalisation, Technique, Administration) dispose d’un nombre d’équipements adapté à son activité :  
- Moniteurs biomédicaux  
- Postes fixes & mobiles  
- Téléphonie VoIP  
- Caméras  
- Contrôle d’accès  
- Pompes, scanners, ECG/EEG  

---

### 🔹 Architecture logique
Chaque bâtiment repose sur :
- 1 **switch L3** (routage inter‑VLAN + DHCP relay)  
- 1 **routeur backbone** vers le cœur de réseau  
- 1 **switch L2 par étage**  
- 1 ou plusieurs **switchs 24 ports** pour les équipements  

L’ensemble est homogène pour simplifier la maintenance.

---

### 🔹 Plan d’adressage
- Segmentation par VLAN selon les types d’équipements  
- Sous‑réseaux CIDR dimensionnés avec marge  
- PVLAN activés (sauf VoIP et serveurs spécifiques)  
- Plans d’adressage séparés pour :  
  - bâtiments  
  - serveurs  
  - DMZ  
  - SOC  
  - cœur de réseau  

👉 Voir `plan_adressage.ods`.

---

### 🔹 Cœur de réseau
- Cluster de routeurs CORE redondants  
- Routage **OSPF area 0**  
- Pare‑feu en bordure de DMZ  
- Backbone fibré inter‑bâtiments  

---

### 🔹 Liens Internet
- Triple opérateurs 
- Routeurs EDGE en cluster  
- Basculement automatique  
- DMZ Web reliée aux EDGE  

---

### 🔹 DMZ & Serveurs
Serveurs principaux :
- AD01 / AD02  
- DHCP_DNS  
- FILE_SERVER / FILE_BACKUP  
- APP01 / APP02  
- BASTION_T1  
- FIREWALL_SERVER  
- PAW  

---

### 🔹 Wi‑Fi
- Bornes Cisco WR1300N  
- WPA2‑PSK (WPA2‑Enterprise prévu mais non implémenté)  
- Authentification centralisée via AD/RADIUS (prévue)

---

## 🔐 Sécurisation du SI

### 🔹 Segmentation
- VLAN par type d’équipement  
- Réduction des domaines de broadcast  
- Contrôle strict des flux inter‑VLAN  

---

### 🔹 SOC
Le SOC comprend :
- Switch central dédié  
- Bastion SOC  
- Cluster XDR‑SIEM  
- Postes analystes  
- Pare‑feu Cisco 5506‑X  

---

### 🔹 Bastion & PAW
- Bastion pour administrer la DMZ  
- PAW pour administrer l’AD  
- Tiering T0/T1/T2 appliqué  
- Comptes admins dédiés  

---

### 🔹 ACL & Firewall
- Politique **deny all / allow by exception**  
- ACL entre DMZ / LAN / SOC  
- Filtrage des flux d’administration  
- NAT & inspection sur les pare‑feu EDGE  

---

## 🚀 Évolutions possibles
### 🔹 Lien 5G de secours
- Ajout d’un lien 5G (ISP3) pour résilience  
- Basculement automatique en cas de catastrophe  
- Maintien de la téléphonie & services externes  

---

## 🛠️ Technologies & Protocoles
- Cisco Packet Tracer  
- VLAN / PVLAN  
- OSPF  
- DHCP Relay  
- ACL  
- NAT  
- WPA2  
- DMZ  
- Bastion / PAW  
- XDR / SIEM  

---

## 📜 Licence
Projet académique — reproduction autorisée pour usage pédagogique.
- ou même un **README orienté portfolio** pour valoriser ton travail.

Tu veux une version plus **technique**, plus **design**, ou plus **professionnelle** ?
