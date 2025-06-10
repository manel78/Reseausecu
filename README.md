# 🔐 Projet Infrastructure Réseau Sécurisé avec pfSense

## 🎯 Objectif du projet

Mettre en place une infrastructure réseau sécurisée avec :

- Un pare-feu **pfSense**
- Un client Ubuntu (machine virtuelle)
- Connexion Internet via NAT
- Un réseau local avec filtrage, test de connectivité et tunnel VPN

---

## 🧩 Composants de l’infrastructure

| Nom                  | Rôle                      | OS/Version       | IP Adresse             | Remarques                                |
|----------------------|---------------------------|------------------|-------------------------|-------------------------------------------|
| **pfSense**          | Pare-feu, NAT, VPN        | pfSense 2.7.x    | WAN : 192.168.4.152<br>LAN : 192.168.1.1 | Accès Internet via NAT, filtrage LAN/WAN |
| **Web VM**           | Client web                | Ubuntu           | 192.168.1.100           | Poste client connecté au LAN             |

---

## 📊 Schéma réseau

Voici la topologie réseau :

![Schéma Réseau](captures/schema_reseau.png)

> *(Renomme ton image en `schema_reseau.png` et place-la dans un dossier `captures/` à la racine du dépôt)*

---

## 📁 Fichiers fournis

| Fichier                        | Description                                          |
|-------------------------------|------------------------------------------------------|
| `rapport_pfsense.docx`        | Rapport complet du projet                            |
| `script_test.sh`              | Script Bash de test de connectivité                  |
| `config_pfsense_backup.xml`   | Export de configuration pfSense                      |
| `captures/`                   | Captures d’écran (interface, règles firewall, etc.)  |

---

## 🔐 Services configurés

- Pare-feu (règles LAN sortantes vers Internet uniquement)
- Bloquage WAN → LAN par défaut
- Test DNS, ping, routage depuis le client Ubuntu
- VPN OpenVPN (configuration serveur et certificats)
- Sauvegarde et restauration de configuration pfSense

---

## ⚠️ Problèmes rencontrés

- Génération de certificat OpenVPN : échec → contourné par création manuelle
- Exportation de clients VPN : `openvpn-client-export` indisponible → méthode alternative utilisée
- Lenteurs sur pfSense : redémarrage de services nécessaire

---

## ✅ Résultats attendus (tests)

- ✅ Ping passerelle (192.168.1.1)
- ✅ Ping Internet (8.8.8.8)
- ✅ Résolution DNS : `dig google.com`
- ✅ Routage correct : `ip route`
- ✅ Connexion VPN fonctionnelle (test client)
