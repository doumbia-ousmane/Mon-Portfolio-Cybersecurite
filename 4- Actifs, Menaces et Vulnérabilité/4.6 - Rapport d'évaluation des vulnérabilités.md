# Rapport d'Évaluation de la Vulnérabilité

## Scénario 
Vous êtes un analyste en cybersécurité nouvellement embauché dans une entreprise de commerce électronique. L'entreprise stocke ses informations sur un serveur de base de données distant, car de nombreux employés travaillent à distance depuis différents endroits du monde. Ces employés consultent régulièrement le serveur pour identifier des clients potentiels. La base de données est accessible au public depuis la création de l'entreprise il y a trois ans. En tant que professionnel de la cybersécurité, vous êtes conscient que le maintien de ce serveur ouvert constitue une grave vulnérabilité. Une évaluation des vulnérabilités vous permettra de communiquer les risques potentiels aux décideurs de l'entreprise. Vous devez rédiger un rapport expliquant clairement en quoi ce serveur vulnérable représente un risque pour les opérations commerciales et comment le sécuriser.

## Rapport
**Date :** 14 janvier 2024  
**Analyste :** Analyste en Cybersécurité  
**Objet :** Sécurisation du serveur de base de données MySQL

---


## 1. Description du Système
Le serveur de base de données constitue le cœur informationnel de l'entreprise. 

* **Système d'exploitation :** Debian Linux
* **Matériel :** 1 To de mémoire vive (RAM), processeur haute performance.
* **Service :** Système de gestion de bases de données (SGBD) MySQL.
* **Réseau :** Connectivité IPv4 accessible publiquement.
* **Sécurité actuelle :** Chiffrement via SSL (obsolète).

---

## 2. Portée et Méthodologie
Le présent rapport se concentre sur les **contrôles d'accès** et l'exposition réseau du système. 

* **Période d'évaluation :** Du 14 novembre 2023 au 14 janvier 2024.
* **Référentiel :** L'analyse des risques est basée sur la norme **NIST SP 800-30**, garantissant une approche rigoureuse et standardisée de l'identification des menaces.

---

## 3. But de l'Évaluation
La base de données héberge des actifs critiques :
* Données clients (RGPD/Confidentialité).
* Campagnes marketing et analyses de performance.
* Données stratégiques de personnalisation.

La protection contre les accès non autorisés est impérative pour maintenir l'avantage concurrentiel et la conformité légale de l'entreprise.

---

## 4. Évaluation des Risques
L'analyse suivante quantifie le risque selon la formule : Probabilité x Gravité = Risque.

| Source de la menace | Événement menaçant | Probabilité (1-3) | Gravité (1-3) | Score de Risque |
| :--- | :--- | :---: | :---: | :---: |
| **Hackers** | Exfiltration et divulgation publique d'informations sensibles. | 3 | 3 | **9** |
| **Anciens employés** | Vente de données confidentielles à la concurrence. | 2 | 3 | **6** |
| **Employés actuels** | Perturbation accidentelle ou malveillante des activités. | 2 | 3 | **6** |
| **Clients** | Modification non autorisée des informations. | 1 | 3 | **3** |



---

## 5. Approche de l'Analyse
L'exposition publique du serveur depuis trois ans crée une surface d'attaque critique. 
* **Urgence :** Le risque lié aux hackers est maximal (9) car le serveur est visible sur l'internet mondial sans filtrage IP. 
* **Historique :** Un incident passé impliquant un ancien employé confirme que les privilèges d'accès ne sont pas révoqués assez rapidement.
* **Impact :** Une compromission pourrait entraîner une perte de réputation irréparable et des sanctions juridiques.

---

## 6. Stratégie de Remédiation
Pour atténuer ces risques, les mesures suivantes doivent être déployées immédiatement :

### A. Sécurisation Réseau et Chiffrement
1.  **Privatisation du serveur :** Retirer l'adresse IP publique et placer le serveur derrière un VPN ou un Firewall avec filtrage IP (Whitelisting).
2.  **Mise à niveau du chiffrement :** Migrer de **SSL vers TLS (v1.2 ou v1.3)** pour corriger les vulnérabilités de transport de données.

### B. Contrôle des Accès (IAM)
* **RBAC (Role-Based Access Control) :** Implémenter le contrôle d'accès basé sur les rôles. Chaque employé n'accède qu'aux données strictement nécessaires à sa mission.
* **Cycle de vie AAA :** Renforcer l'**A**uthentification, l'**A**utorisation et l'**A**udit (traçabilité complète des actions).
* **MFA (Authentification Multifacteurs) :** Exiger un second facteur de validation (SMS, e-mail, application d'authentification ou carte d'employé) pour toute connexion.

---
> **Note de l'analyste :** La mise en œuvre de ces recommandations réduira le score de risque global de plus de 70%.
