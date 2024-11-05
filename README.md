# Aperçu d'AutoRptFR

AutoRptFR crée des répertoires de travail uniques à partir de ces modèles. Si vous repassez un cours ou un examen de certification, le nouveau répertoire sera distinct du précédent.

```
templates
├── oscp
├── osda
├── osed
├── osee
├── osep
├── osmr
├── oswa
├── oswe
├── oswp
├── pnpt
└── training
    ├── bugbounty
    ├── exp-301-lab
    ├── exp-312-lab
    ├── exp-401-lab
    ├── pen-200-lab
    ├── pen-210-lab
    ├── pen-300-lab
    ├── plain
    ├── soc-200-lab
    ├── web-200-lab
    └── web-300-lab
```

AutoRptFR impose un flux de travail cohérent et fiable pour la prise de notes et la rédaction de rapports lors d'engagements. Il gère une structure de répertoire de base avec des modèles de notes et de rapports, le tout encapsulé dans un menu au style rétro des années 1980. Le flux de travail est adapté au terminal pour garder votre concentration sur l'engagement sans jongler entre différentes interfaces.

L'objectif principal est de simplifier le processus associé aux examens de certification en sécurité informatique tels que l'OSCP ou le PNPT, bien que de nombreux autres soient pris en charge. Il couvre également les formations et les CTF sur des plateformes de sécurité comme Hack the Box, Try Hack Me, ou Proving Grounds, pour ne citer qu'elles. La chasse aux bugs et les tests d'intrusion sont également des options d'utilisation, bien que toujours en développement.

:trophy: Un grand merci et respect à [noraj pour le "Modèle de Rapport d'Examen Offensive Security en Markdown"](https://github.com/noraj/OSCP-Exam-Report-Template-Markdown). Certaines parties de ce dépôt sont incluses dans AutoRptFR.

:warning: Il est de votre responsabilité de vous assurer que le rapport final, l'archive et tous les produits de travail sont complets et précis avant toute soumission. Bien que chaque effort ait été fait pour réduire les bugs, ils sont malheureusement possibles.

![startup](https://github.com/BenAcord/wiki-images/raw/main/AutoRpt/2-startup-1.jpeg "Capture d'écran de démarrage d'AutoRptFR pour un essai d'examen OSCP")

La structure de répertoire suivante avec des fichiers de modèles prédéfinis est créée après avoir terminé les invites dans `autorpt startup`.
![startup2](https://github.com/BenAcord/wiki-images/raw/main/AutoRpt/2-startup-2.jpeg "Structure de répertoire résultante")

Ce répertoire peut être ouvert en tant que coffre-fort Obsidian. Les fichiers prédéfinis sont des modèles pour guider votre prise de notes et le processus de rédaction de rapports. Les balises standard sont automatiquement remplacées lors de la création du fichier de rapport final.
![startup](https://github.com/BenAcord/wiki-images/raw/main/AutoRptFR/20-obsidian-0.jpeg "Utilisation d'Obsidian pour rédiger votre rapport avec des fichiers prédéfinis")

---

# Table des Matières

* [Aperçu](#AutoRptFR)
* [Installation](#Install)
* [Utilisation](#Usage)
* [Contribution](#Contributing)

---

## Mise à jour
Si vous disposez d'un clone existant ou d'une version antérieure à v1.1.3, suivez ces deux étapes pour mettre à jour le fichier config.toml de votre répertoire personnel avec les dernières valeurs.

0. Assurez-vous que votre OS est à jour avec `sudo apt-get update -y && sudo apt-get upgrade -y`.
1. Exécutez `git pull` pour obtenir le dernier code.
2. Exécutez `autorpt upgrade` après avoir tiré la dernière version du dépôt.

## Installation

Un script shell en cours de développement est inclus pour automatiser l'installation des dépendances et la configuration. L'exemple ici utilise /opt comme répertoire d'installation d'AutoRptFR.

### Dépendances et Mises en garde
AutoRptFR n'a été testé que sur Kali Linux et Ubuntu 22.04. Une liste des dépendances applicatives est disponible dans le script setup.sh. Les dépendances Python sont listées dans le fichier pyproject.toml.

Hautement recommandé :
:hammer_and_wrench: [AutoRecon](https://github.com/Tib3rius/AutoRecon)
:hammer_and_wrench: [Flameshot](https://flameshot.org/)
:hammer_and_wrench: [Obsidian](https://obsidian.md/)

### 0. Mise à jour des dépôts et mise à niveau
```Bash
sudo apt-get update -y && sudo apt-get upgrade -y
```

### 1. Clonez le dépôt
```Bash
cd /opt
sudo mkdir AutoRptFR
# Définissez votre utilisateur et groupe comme propriétaire.
sudo chown kali:kali AutoRptFR
# Clonez
git clone https://github.com/Retr0Lovelace/AutoRptFR.git
```

### 2. Exécutez la configuration
```Bash
cd AutoRptFR
./setup.sh
```

### 3. Vérifiez l'installation réussie
```Bash
autorpt help
```

### 4. Personnalisez les Paramètres
```Bash
autorpt
# Suivez ces paramètres, un par un.
Sélectionnez l'option 6 # Choisissez 6 pour les Paramètres
Sélectionnez l'option 1 # pour les paramètres au niveau de l'application
Sélectionnez l'option 2 # pour définir votre nom complet, suivez les invites
Sélectionnez l'option 3 # si vous avez un identifiant étudiant universel
Sélectionnez l'option 4 # pour définir votre adresse e-mail. Laissez vide si vous utilisez des comptes différents (ex. bug bounty, formation)
Sélectionnez l'option 5 # pour définir le format de rapport préféré (ex. pdf, pdf+7z, GitHub Markdown)
```

## Utilisation
`autorpt.py [ help | settings | active | startup | vuln [list] | ports | sitrep [message] | addtarget [Adresse IP] | addtemplate | sitrep [list] | finalize | list | whathaveidone | upgrade ]`

AutoRptFR applique une organisation de la structure des répertoires et de la prise de notes cohérente pour faciliter un processus de rédaction de rapports fluide. Pour plus de détails sur la fonctionnalité de chaque paramètre, veuillez consulter le [wiki](https://github.com/BenAcord/AutoRpt/wiki).

### Exemple de Parcours de Travail
1. `autorpt.py startup` Avant de commencer un examen ou une formation, startup crée une structure de répertoire de base et y place un modèle de rapport en markdown. Exécutez ceci bien avant le début de l'examen. Pendant l'examen ou la formation, modifiez les fichiers markdown pour les cibles.

Startup est requis avant d'utiliser les autres paramètres, à l'exception de l'aide et des paramètres. Ceci est nécessaire car startup crée le répertoire de travail de l'engagement et enregistre la session. Tous les autres paramètres se réfèrent à la session d'engagement active.

2. `autorpt.py ports` Scanne rapidement pour les sorties de nmap des outils de reconnaissance connus et affiche un résumé des ports et services. Crée également un fichier tableur avec un onglet pour chaque cible et ses ports.

3. `autorpt.py vuln` Un sous-menu pour enregistrer les vulnérabilités confirmées, assigner un score CVSS 3 et indiquer la tactique et technique MITRE ATT&CK. Les vulnérabilités sont stockées dans un fichier vulns.csv et automatiquement intégrées dans le rapport final sous forme de tableau.

Si vous prenez une pause prolongée et oubliez votre progression, pas de souci, utilisez `autorpt active` pour afficher les informations du dernier engagement.
![active](https://github.com/BenAcord/wiki-images/raw/main/AutoRpt/6-active.jpeg "Engagement actif")

4. `autorpt.py sitrep` Suivez votre statut et activité tout au long de l'engagement. Ajoutez rapidement un statut ou consultez le journal pour voir l'historique des activités.

5. `autorpt.py finalize` Pendant la fenêtre de soumission de l'examen, AutoRptFR génère un rapport final en PDF et archive 7z à partir de vos fichiers markdown. D'autres formats de fichiers sont pris en charge : Jira, odt, docx et markdown courant.
![startup](https://github.com/BenAcord/wiki-images/raw/main/AutoRpt/7-finalize-0.jpg "Finalisation d'un rapport")
![startup](https://github.com/BenAcord/wiki-images/raw/main/AutoRpt/7-finalize-1.jpg "Rapport final")

6. `autorpt.py settings` peut être exécuté à tout moment pour configurer les valeurs de session et de niveau applicatif. Si startup n’a pas encore été exécuté, ses fonctionnalités d’engagement seront limitées.

7. `autorpt.py whathaveidone` liste l'état de tous les engagements enregistrés à ce jour. Un moyen pratique de suivre vos accomplissements au fil du temps.
![startup](https://github.com/BenAcord/wiki-images/raw/main/AutoRpt/whathaveidone-00.jpg "Résumé de l'audit")

## Contribuer
Créez un problème ici sur GitHub si vous trouvez un bug ou avez une idée d'amélioration.
