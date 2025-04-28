-----------------------------------------------------------------------
**8INF876 -- Conception et architecture des systèmes d'infonuagique**
-----------------------------------------------------------------------
# Les Services Web dans le Cloud Computing

-----------------------------------------------------------------------

| Julot NGONGANG, Hamza ZIRAR, Eloi SEIDLITZ                       |
|                                                                   |
| 01/05/2023                                                        |
|=================================================================== |
|                                                                   |

# TABLE DES MATIÈRES

[CHAPITRE 1 INTRODUCTION](#chapitre-1-introduction)
- [1.1 Introduction](#introduction)
- [1.2 Description de la problématique](#description-de-la-problématique)
- [1.3 Description du développement](#description-du-développement)

[CHAPITRE 2 Approche prise pour la conception](#chapitre-2-approche-prise-pour-la-conception)
- [2.1 Introduction](#introduction-1)
- [2.2 Architecture du système](#architecture-du-système)
- [2.3 Diagrammes de cas d'utilisations](#diagrammes-de-cas-dutilisations)
- [2.4 Diagrammes de séquences](#diagrammes-de-séquences)
- [2.5 Diagrammes d'activités](#diagrammes-dactivités)
- [2.6 Conclusion](#conclusion)

[CHAPITRE 3 Implementation et tests](#chapitre-3-implementation-et-tests)
- [3.1 Introduction](#introduction-2)
- [3.2 Outils d'implémentation](#outils-dimplémentation)
- [3.3 Approche prise pour l'implémentation](#approche-prise-pour-limplémentation)
- [3.4 Discussion des résultats](#discussion-des-résultats)
- [3.5 Conclusion](#conclusion-1)

[CHAPITRE 4 Conclusion](#chapitre-4-conclusion)

[APPENDICE A : Details de l'Implementation](#appendice-a--details-de-limplementation)

[APPENDICE B : Manuel d'utilisation](#appendice-b--manuel-dutilisation)

[bibliographie](#bibliographie)

# LISTE DES FIGURES

Figure 1- Architecture du Système de site vitrine déployé sur Netlify/Vercel [2](#_Toc115286997)

Figure 2- Architecture de l'application MCQ Generator [4](#mcqgen-architecture)

Figure 3- Architecture de l'application ADAM pour le prototype SaaS [5](#adam-architecture)

# LISTE DES ACRONYMES

CC : Cloud Computing

IaaS : Infrastructure as a Service

PaaS : Platform as a Service

SaaS : Software as a Service

CDN : Content Delivery Network

CI/CD : Continuous Integration/Continuous Deployment

HTTPS : HyperText Transfer Protocol Secure

SSL : Secure Sockets Layer

API : Application Programming Interface

RAG : Retrieval-Augmented Generation

MCQ : Multiple Choice Questions

DNS : Domain Name System

LLM : Large Language Model

# CHAPITRE 1 INTRODUCTION {#chapitre-1-introduction}

## Introduction

Le cloud computing est devenu un élément fondamental de l'infrastructure technologique moderne, offrant une flexibilité, une évolutivité et une rentabilité inégalées pour le déploiement d'applications et de services. Il permet aux organisations de toutes tailles d'accéder à des ressources informatiques puissantes sans avoir à investir massivement dans des infrastructures physiques [1].

Dans ce contexte, les services web jouent un rôle crucial en permettant l'interaction et l'échange de données entre différentes applications à travers Internet. Ces services constituent la colonne vertébrale de nombreuses applications modernes, facilitant l'intégration de systèmes hétérogènes et permettant la création d'écosystèmes numériques complets [2].

Ce projet explore l'intersection entre les services web et le cloud computing, en examinant comment différents types de services web peuvent être déployés efficacement dans des environnements cloud. Nous analysons plusieurs cas d'application, depuis les sites vitrines statiques jusqu'aux applications SaaS complexes, et proposons des solutions de déploiement adaptées à chaque cas.

## Description de la problématique

Le déploiement de services web dans le cloud présente plusieurs défis que les développeurs et architectes doivent relever. Deux questions fondamentales se posent :

1. Selon certains cas d'application, quels peuvent être les différents types de services web à utiliser ?

2. Comment déployer ces cas d'application grâce au cloud computing ?

La multiplicité des solutions de cloud computing (AWS, Google Cloud, Microsoft Azure, etc.) et des services qu'ils proposent rend complexe le choix de l'architecture et des outils appropriés pour chaque type d'application. Les développeurs doivent prendre en compte de nombreux facteurs tels que la performance, la sécurité, l'évolutivité, la facilité de maintenance et le coût.

De plus, chaque type d'application web (site statique, application avec backend simple, SaaS complexe) présente des exigences spécifiques en termes d'infrastructure et de services cloud. Il est donc essentiel de comprendre ces besoins et de savoir quelles solutions cloud conviennent le mieux à chaque cas.

## Description du développement

Dans ce projet, nous avons adopté une approche pratique pour résoudre les problématiques identifiées. Nous avons développé et déployé trois types d'applications web différentes dans diverses plateformes cloud pour évaluer leurs performances, leur facilité de déploiement et leur adéquation à chaque cas d'usage.

Les applications développées sont :

1. Un site vitrine statique pour une entreprise de solutions digitales nommée "Innovate Solutions", construit avec le framework Astro.

2. Une application avec backend simple appelée "MCQ Generator" (mcqgen), qui génère des questionnaires à choix multiples à partir de documents texte ou PDF en utilisant l'API OpenAI.

3. Un prototype de SaaS éducatif nommé "ADAM" (Adaptive Digital Academic Mentor), qui aide les étudiants à comprendre des notions complexes via un chatbot interactif et la génération de QCM.

Pour chaque application, nous avons exploré différentes solutions de déploiement cloud :

- Pour le site vitrine : Netlify, Vercel, GitHub Pages, Static.app et Claude.ai
- Pour l'application avec backend simple : Heroku et AWS EC2
- Pour le prototype de SaaS : déploiement local avec Docker et sur Google Cloud Platform

Nous avons documenté en détail le processus de déploiement pour chaque solution, identifié les avantages et inconvénients de chacune, et fourni des recommandations basées sur nos expériences pratiques.

# CHAPITRE 2 Approche prise pour la conception {#chapitre-2-approche-prise-pour-la-conception}

## Introduction

Ce chapitre présente l'approche que nous avons adoptée pour concevoir les différentes applications web et planifier leur déploiement dans le cloud. Nous commencerons par décrire l'architecture globale de chaque système, puis nous présenterons les diagrammes de cas d'utilisation, de séquence et d'activités pour illustrer le fonctionnement et les interactions au sein de ces systèmes.

Notre approche de conception a été guidée par les besoins spécifiques de chaque type d'application, en tenant compte des contraintes et des opportunités offertes par les différentes plateformes cloud. Nous avons cherché à maximiser l'efficacité, la scalabilité et la maintenabilité des applications tout en minimisant les coûts de déploiement et d'exploitation.

## Architecture du système

### Site Vitrine

Le site vitrine est une application web statique conçue pour présenter l'entreprise "Innovate Solutions" et ses services. L'architecture de ce système est relativement simple, reposant sur la génération de fichiers HTML, CSS et JavaScript qui sont ensuite servis par un hébergeur de sites statiques.

Architecture et Technologies :
- Framework Astro pour la génération de sites statiques
- Architecture basée sur des composants pour une maintenance facilitée
- Performance optimisée grâce à la génération statique des pages

Le site comprend plusieurs sections clés, notamment une page d'accueil avec section héro, une présentation des services, une section "À propos", des témoignages clients, un formulaire de contact, une FAQ interactive et un pied de page complet.

L'architecture du déploiement varie selon la plateforme choisie :

![Architecture du Site Vitrine](media/site-vitrine-architecture.png)

*Figure 1- Architecture du Site Vitrine déployé sur Netlify/Vercel*

### Application MCQ Generator

L'application MCQ Generator (mcqgen) est une application web avec un backend simple qui génère des questionnaires à choix multiples à partir de documents texte ou PDF.

Architecture technique :
- Frontend : Streamlit pour créer une interface web réactive et intuitive
- Backend : LangChain pour orchestrer les appels API vers des modèles de langage
- Traitement de données : PyPDF2 pour extraire le texte des fichiers PDF

![Architecture de MCQ Generator](media/mcqgen-architecture.png)

*Figure 2- Architecture de l'application MCQ Generator*

### Prototype de SaaS

ADAM (Adaptive Digital Academic Mentor) est une application SaaS éducative plus complexe qui aide les étudiants à comprendre des notions complexes via un chatbot interactif, la génération de QCM et de questions à développer. Il est important de noter que l'application est, pour l'instant, uniquement orientée pour répondre aux besoins des étudiants, l'interface pour les enseignants n'ayant pas encore été développée.

Architecture technique :
- Frontend : Angular avec composants spécialisés pour QCM, questions-réponses et affichage Markdown
- Backend : NestJS pour l'API RESTful, gestion des fichiers et communication avec les LLMs
- RAG (Retrieval-Augmented Generation) basé sur la vectorisation intelligente des contenus de cours

![Architecture d'ADAM](http://www.plantuml.com/plantuml/png/bOw_oi904CJxVOeXrPSYh_0H4Ur5i5ykgnpUdx2t5n3ntJqB6uc5tS0Cy_kDnLYjna3iB2jEldYJgaJlX67unzysfrA3YMBcYvJ-ezwb9TzQMHEYbD8cM3pZd3NMm5u5ay3bP8tIVxqEZFtcq1FDxAwlZ-xOTit9r2VfS2UicE1NFDQO3nebJJM69m00)

*Figure 3- Architecture de l'application ADAM pour le prototype SaaS*

## Diagrammes de cas d'utilisations {#diagrammes-de-cas-dutilisations}

### Site Vitrine

Pour le site vitrine, les cas d'utilisation sont relativement simples, car il s'agit principalement d'une expérience de navigation et de consultation d'informations.

```
+------------------+                      +------------------+
|                  |   Consulter pages    |                  |
|    Visiteur      | -------------------> |  Site Vitrine    |
|                  |                      |                  |
+------------------+                      +------------------+
        |                                         |
        |  Envoyer un message via                 |
        |  formulaire de contact                  |
        +---------------------------------------->+
        |                                         |
        |  Consulter la FAQ                       |
        +---------------------------------------->+
```

### Application MCQ Generator

L'application MCQ Generator offre plus d'interactions avec l'utilisateur :

```
+------------------+                      +------------------+
|                  |   Uploader fichier   |                  |
|    Utilisateur   | -------------------> |  MCQ Generator   |
|                  |                      |                  |
+------------------+                      +------------------+
        |                                         |
        |  Configurer paramètres                  |
        |  (nombre de questions, sujet)           |
        +---------------------------------------->+
        |                                         |
        |  Générer QCM                            |
        +---------------------------------------->+
        |                                         |
        |  Visualiser résultats                   |
        +<----------------------------------------+
```

### Prototype de SaaS ADAM

Le prototype ADAM a une structure plus complexe avec plusieurs types d'utilisateurs et d'interactions :

```
+------------------+                      +------------------+
|                  |   S'authentifier     |                  |
|    Étudiant      | -------------------> |      ADAM        |
|                  |                      |                  |
+------------------+                      +------------------+
        |                                         |
        |  Poser des questions au chatbot         |
        +---------------------------------------->+
        |                                         |
        |  Importer documents pédagogiques        |
        +---------------------------------------->+
        |                                         |
        |  Générer et répondre à des QCM          |
        +<--------------------------------------->+
      
```

## Diagrammes de séquences

### Déploiement d'un site vitrine sur Netlify

```
+-----------+                  +----------+                 +---------+
| Developer |                  |  GitHub  |                 | Netlify |
+-----------+                  +----------+                 +---------+
     |                              |                          |
     | Push code                    |                          |
     |----------------------------->|                          |
     |                              |                          |
     |                              | Webhook notification     |
     |                              |------------------------->|
     |                              |                          |
     |                              |                          | Build site
     |                              |                          |----------+
     |                              |                          |          |
     |                              |                          |<---------+
     |                              |                          |
     |                              |                          | Deploy to CDN
     |                              |                          |----------+
     |                              |                          |          |
     |                              |                          |<---------+
     |                              |                          |
     |                              | Deployment notification  |
     |<--------------------------------------------------------|
     |                              |                          |
```

### Génération de QCM dans MCQ Generator

```
+-------------+                  +---------------+                 +------------+
| Utilisateur |                  | MCQ Generator |                 | OpenAI API |
+-------------+                  +---------------+                 +------------+
     |                                 |                              |
     | Upload fichier PDF              |                              |
     |-------------------------------->|                              |
     |                                 |                              |
     |                                 | Extraction texte             |
     |                                 |-------------+                |
     |                                 |             |                |
     |                                 |<------------+                |
     |                                 |                              |
     | Configurer paramètres           |                              |
     |-------------------------------->|                              |
     |                                 |                              |
     | Générer QCM                     |                              |
     |-------------------------------->|                              |
     |                                 | Requête API                  |
     |                                 |----------------------------->|
     |                                 |                              |
     |                                 |                              | Traitement
     |                                 |                              |----------+
     |                                 |                              |          |
     |                                 |                              |<---------+
     |                                 |                              |
     |                                 | Réponse avec QCM générés     |
     |                                 |<-----------------------------|
     |                                 |                              |
     | Affichage des QCM               |                              |
     |<--------------------------------|                              |
     |                                 |                              |
```

## Diagrammes d'activités

### Déploiement sur AWS EC2

```
[Start] --> [Créer compte AWS]
        --> [Lancer instance EC2]
        --> [Configurer sécurité]
        --> [Se connecter via SSH]
        --> [Installer dépendances]
        --> [Cloner dépôt Git]
        --> [Configurer application]
        --> [Lancer application]
        --> [Tester application]
        --> [End]
```

### Utilisation du prototype ADAM

```
[Start] --> [S'authentifier]
        --> [Accéder à l'interface]
        --> [Décision: Action à effectuer?]
           --> [Importer document]
              --> [Sélectionner fichier]
              --> [Uploader]
              --> [Confirmation]
           --> [Poser question]
              --> [Entrer question]
              --> [Recevoir réponse]
           --> [Générer QCM]
              --> [Sélectionner sujet]
              --> [Configurer difficulté]
              --> [Obtenir QCM]
              --> [Répondre aux questions]
              --> [Voir résultats]
        --> [End]
```

## Conclusion

Dans ce chapitre, nous avons présenté l'architecture générale de nos trois types d'applications web et les différentes approches de déploiement dans le cloud. Nous avons illustré à l'aide de diagrammes les interactions principales entre les utilisateurs et les systèmes, ainsi que les flux de travail pour le déploiement et l'utilisation des applications.

L'architecture modulaire que nous avons adoptée pour chaque application permet une grande flexibilité en termes de déploiement, avec la possibilité de migrer facilement d'une plateforme cloud à une autre selon les besoins. Cette approche favorise également la scalabilité et la maintenance des systèmes.

Les diagrammes présentés servent de guide pour comprendre les fonctionnalités principales des applications et leurs modes de déploiement. Ils constituent une base solide pour la phase d'implémentation qui sera détaillée dans le chapitre suivant.

# CHAPITRE 3 Implementation et tests {#chapitre-3-implementation-et-tests}

## Introduction

Ce chapitre détaille le processus d'implémentation et de déploiement des différentes applications web dans divers environnements cloud. Nous commencerons par présenter les outils utilisés pour l'implémentation, puis nous décrirons l'approche adoptée pour le déploiement de chaque application. Ensuite, nous discuterons des résultats obtenus et des tests effectués pour valider le bon fonctionnement de nos déploiements.

L'objectif principal de cette phase était de mettre en pratique les concepts architecturaux décrits dans le chapitre précédent et d'évaluer les avantages et inconvénients des différentes plateformes cloud pour chaque type d'application.

## Outils d'implémentation

### Site Vitrine

- **Framework de développement** : Astro pour la génération de sites statiques
- **Langages** : HTML, CSS, JavaScript
- **Gestionnaire de code source** : Git et GitHub
- **Plateformes de déploiement** :
  - Netlify pour le déploiement continu et le CDN
  - Vercel pour le déploiement rapide et les previews
  - GitHub Pages pour l'hébergement statique gratuit
  - Static.app pour la configuration avancée
  - Claude.ai pour la génération et l'hébergement rapides

### Application MCQ Generator

- **Frontend** : Streamlit pour l'interface web interactive
- **Backend** : Python, LangChain pour l'orchestration des appels API
- **Traitement des données** : PyPDF2 pour l'extraction de texte des PDF
- **API externe** : OpenAI pour la génération de questions
- **Plateformes de déploiement** :
  - Heroku comme PaaS pour le déploiement simplifié
  - AWS EC2 comme IaaS pour un contrôle total de l'infrastructure

### Prototype de SaaS ADAM

- **Frontend** : Angular avec composants spécialisés
- **Backend** : NestJS pour l'API RESTful
- **Base de données** : MySQL pour le stockage relationnel
- **Conteneurisation** : Docker et docker-compose
- **Vectorisation** : ChromaDB pour le stockage et la recherche de vecteurs
- **IA** : OpenAI et Google Gemini pour les modèles de langage
- **Plateformes de déploiement** :
  - Local avec Docker
  - Google Cloud Platform (GCP) avec Google Compute Engine

## Approche prise pour l'implémentation

### Déploiement du Site Vitrine

#### Netlify

Le déploiement sur Netlify a été réalisé en suivant ces étapes :

1. Création d'un compte sur netlify.com
2. Configuration du projet via l'option "New site from Git"
3. Sélection du repository GitHub contenant le code du site
4. Configuration des paramètres de build
5. Configuration d'un domaine personnalisé (optionnel)

Netlify offre plusieurs avantages clés pour ce type de déploiement :
- Déploiements automatiques depuis le dépôt Git
- Pipeline d'intégration continue intégré
- Certificat SSL gratuit et automatique
- Réseau CDN mondial pour une distribution rapide
- Gestion simplifiée des variables d'environnement

#### Vercel

Le déploiement sur Vercel a suivi un processus similaire :

1. Création d'un compte sur vercel.com
2. Import du projet via l'option "Import Project"
3. Sélection du dépôt GitHub
4. Configuration automatique détectée pour Astro
5. Configuration de domaine (optionnel)

Vercel offre des fonctionnalités particulièrement adaptées aux sites modernes :
- Déploiement sans configuration complexe
- HTTPS automatique et gratuit
- Réseau Edge pour une distribution mondiale rapide
- Déploiements de prévisualisation pour chaque push
- Analytics intégrés pour suivre les performances

#### Autres plateformes

Des déploiements ont également été réalisés sur :
- **GitHub Pages** : Service gratuit d'hébergement statique avec configuration via gh-pages.yml
- **Static.app** : Service spécialisé offrant des options de configuration avancées
- **Claude.ai** : Génération et hébergement de sites statiques directement via l'interface de l'IA

### Déploiement de l'Application MCQ Generator

#### Heroku

Le déploiement sur Heroku a impliqué les étapes suivantes :

1. Création d'un compte sur heroku.com
2. Installation de Heroku CLI
3. Création d'une application via `heroku create mcqgen-app`
4. Configuration des variables d'environnement pour l'API OpenAI
5. Configuration du Procfile avec la commande `web: sh setup.sh && streamlit run StreamLitApp.py`
6. Création d'un fichier setup.sh pour configurer l'environnement Streamlit
7. Déploiement via `git push heroku main`

Heroku, en tant que PaaS, a simplifié considérablement le processus de déploiement en gérant automatiquement l'infrastructure sous-jacente.

#### AWS EC2

Le déploiement sur AWS EC2 a nécessité une approche plus manuelle :

1. Création d'une instance EC2 de type t2.large avec Ubuntu
2. Configuration des règles de sécurité pour exposer le port 8501 (Streamlit)
3. Connexion SSH à l'instance
4. Installation des dépendances (Python, Git, etc.)
5. Clonage du dépôt et installation des packages
6. Configuration de la clé API OpenAI
7. Lancement de l'application via `python3 -m streamlit run StreamLitApp.py`

Cette approche IaaS offre un contrôle total sur l'infrastructure mais nécessite plus de configuration manuelle.

### Déploiement du Prototype de SaaS ADAM

#### Déploiement local avec Docker

Le prototype ADAM a été conteneurisé avec Docker :

1. Création d'images Docker séparées pour le frontend Angular et le backend NestJS
2. Configuration des volumes pour la persistance des données
3. Utilisation de docker-compose pour orchestrer les services localement

L'application fonctionne parfaitement en environnement local, ce qui a permis de valider la conception et les fonctionnalités avant de procéder au déploiement cloud.

#### Déploiement sur Google Cloud Platform

Pour le déploiement sur GCP, deux approches ont été testées :

1. **Déploiement via DockerHub et GCE** :
   - Les images Docker (frontend et backend) ont été créées et publiées sur DockerHub
   - Une VM a été provisionnée sur Google Compute Engine (GCE)
   - Les images ont été importées sur la VM depuis DockerHub
   - Une composition Docker a été configurée sur la VM

2. **Déploiement direct depuis GitHub** :
   - Le repository complet a été cloné directement sur la VM GCE
   - Les conteneurs ont été construits localement sur la VM

Dans les deux cas, plusieurs problèmes techniques ont été rencontrés :
   - Les images Docker n'incluaient pas initialement tous les fichiers nécessaires, ce qui a nécessité une reconfiguration des Dockerfiles et une reconstruction des images
   - Une fois ce premier problème résolu, des difficultés avec la certification SSL sont apparues lors de l'accès à l'application via l'internet public, un problème qui n'a pas encore été complètement résolu

## Discussion des résultats

### Site Vitrine

Les tests de déploiement du site vitrine ont été concluants sur toutes les plateformes. Voici les URLs des déploiements réussis :

- Netlify : https://stirring-hamster-c9bb60.netlify.app/
- Vercel : https://static-website-pi-six.vercel.app/
- GitHub Pages : https://eloisd.github.io/Archi_cloud_presentation/ et https://eloisd.github.io/mcqgen/
- Static.app : https://idealistic-woodpecker.static.domains/presentation3.pdf et https://idealistic-woodpecker.static.domains/snake.html
- Claude.ai : https://claude.site/artifacts/82709da2-6c6c-4668-b419-15a207f2a23d

Chaque plateforme présente des avantages spécifiques :
- **Netlify et Vercel** offrent les solutions les plus complètes avec CI/CD intégré et CDN mondial
- **GitHub Pages** est idéal pour les projets open-source et la documentation
- **Static.app** propose des options de configuration avancées
- **Claude.ai** permet un prototypage extrêmement rapide

### Application MCQ Generator

L'application a été déployée avec succès sur Heroku :
- URL de démonstration : https://mcqgen-c36b54936fcf.herokuapp.com/

Le déploiement sur AWS EC2 a été réalisé mais n'est pas accessible publiquement en raison de limitations de crédits AWS.

Les tests fonctionnels ont confirmé que l'application fonctionne comme prévu, permettant :
- L'upload de fichiers PDF
- La configuration des paramètres de génération de QCM
- La génération et l'affichage des questions via l'API OpenAI

### Prototype de SaaS ADAM

Le prototype a été déployé avec succès en local via Docker, avec les fonctionnalités suivantes orientées uniquement pour les étudiants :
- Interface de connexion
- Chatbot interactif pour les questions éducatives
- Upload de documents pédagogiques
- Génération de QCM

Des tentatives de déploiement sur Google Compute Engine (GCE) ont été effectuées selon deux approches :

1. Via DockerHub :
   - Images Docker publiées sur DockerHub puis importées sur la VM
   - Cette approche a révélé des problèmes avec les images qui ne contenaient pas tous les fichiers nécessaires

2. Via GitHub :
   - Repository cloné directement sur la VM GCE
   - Construction des conteneurs localement sur la VM

Dans les deux cas, après résolution des problèmes initiaux avec les images Docker, des difficultés liées à la certification SSL sont apparues et n'ont pas encore été résolues.

Une URL de test a été temporairement établie à http://34.47.28.2:4200/signin, mais l'accès sécurisé via HTTPS n'est pas encore fonctionnel.

## Conclusion

L'implémentation et les tests des différentes applications web ont démontré la versatilité des solutions cloud modernes pour le déploiement de services web variés.

Pour les sites statiques, les plateformes spécialisées comme Netlify et Vercel offrent la meilleure expérience avec un équilibre optimal entre simplicité et fonctionnalités avancées. GitHub Pages constitue également une excellente option gratuite pour les projets open-source.

Pour les applications avec backend simple comme MCQ Generator, Heroku représente la solution la plus rapide et la plus simple pour le déploiement, bien qu'AWS EC2 offre plus de flexibilité et de contrôle pour les applications nécessitant des ressources spécifiques.

Pour les applications SaaS complexes comme ADAM, une approche conteneurisée avec Docker semble être la plus adaptée, permettant une gestion efficace des ressources et une portabilité optimale entre environnements de développement et de production.

Les tests réalisés ont confirmé la viabilité de chaque solution pour son cas d'usage spécifique, validant ainsi notre approche de conception et d'implémentation.

# CHAPITRE 4 Conclusion {#chapitre-4-conclusion}

Ce projet nous a permis d'explorer en profondeur les différentes approches pour déployer des services web dans le cloud, en fonction de leur complexité et de leurs besoins spécifiques. À travers trois cas d'application concrets - un site vitrine statique, une application avec backend simple, et un prototype de SaaS - nous avons pu évaluer l'adéquation de diverses plateformes cloud et mettre en œuvre des déploiements fonctionnels.

## Enseignements tirés

Ce projet nous a apporté plusieurs enseignements clés :

1. **Diversité des solutions de déploiement** : Il existe une grande variété de solutions pour déployer des services web dans le cloud, chacune avec ses avantages et inconvénients. Le choix de la plateforme doit être guidé par les besoins spécifiques de l'application, le budget disponible, et les compétences de l'équipe.

2. **Importance de la conteneurisation** : Pour les applications complexes, la conteneurisation avec Docker simplifie grandement le déploiement et assure la cohérence entre les environnements de développement et de production.

3. **Compromis entre contrôle et simplicité** : Les solutions PaaS comme Heroku offrent une grande simplicité de déploiement mais moins de contrôle, tandis que les solutions IaaS comme AWS EC2 offrent un contrôle total mais nécessitent plus de configuration.

4. **Évolution des plateformes de déploiement statique** : Les plateformes comme Netlify et Vercel ont considérablement simplifié le déploiement de sites statiques en intégrant CI/CD, CDN et autres fonctionnalités avancées.

5. **Intégration des services d'IA** : L'intégration de services d'IA comme OpenAI dans les applications web devient de plus en plus simple grâce aux API standardisées et aux bibliothèques comme LangChain qui abstraient les complexités d'implémentation.

## Problèmes rencontrés

Au cours de ce projet, nous avons rencontré plusieurs défis :

1. **Limitations des plans gratuits** : Les plans gratuits des services cloud comme AWS ont des limitations qui ont parfois entravé nos tests, notamment pour le déploiement EC2 qui n'a pas pu rester accessible publiquement en raison de limitations de crédits.

2. **Complexité de la configuration Kubernetes** : La mise en place d'un cluster Kubernetes pour le déploiement du prototype SaaS s'est révélée complexe et n'a pas pu être entièrement finalisée dans le cadre de ce projet.

3. **Gestion des secrets et variables d'environnement** : La gestion sécurisée des clés API et autres secrets a nécessité une attention particulière pour chaque plateforme de déploiement.

4. **Différences entre plateformes** : Chaque plateforme cloud a ses propres spécificités, ce qui a parfois nécessité des adaptations du code ou de la configuration pour assurer un déploiement réussi.

## Recommandations

Sur la base de notre expérience dans ce projet, nous pouvons formuler les recommandations suivantes pour le déploiement de services web dans le cloud :

1. **Pour les sites statiques** :
   - Netlify et Vercel sont les options les plus recommandées pour la plupart des cas d'usage, offrant un excellent équilibre entre simplicité et fonctionnalités
   - GitHub Pages reste une excellente option gratuite pour les projets open-source et la documentation
   - Static.app est à considérer pour les cas nécessitant des configurations avancées
   - Claude.ai peut être utilisé pour des prototypes rapides ou des démonstrations temporaires

2. **Pour les applications avec backend simple** :
   - Heroku est idéal pour un déploiement rapide avec un minimum de configuration
   - AWS EC2 est préférable lorsqu'un contrôle précis des ressources ou des performances spécifiques sont nécessaires
   - Les solutions conteneurisées peuvent être envisagées pour faciliter la portabilité entre environnements

3. **Pour les applications SaaS complexes** :
   - Une approche basée sur Docker et Kubernetes est recommandée pour la scalabilité et la portabilité
   - Le choix entre GCP, AWS et Azure doit être fait en fonction des services complémentaires nécessaires (IA, stockage, etc.)
   - Une architecture microservices facilite la maintenance et l'évolution indépendante des composants

4. **Considérations générales** :
   - Privilégier les solutions avec CI/CD intégré pour simplifier le cycle de développement
   - Mettre en place une stratégie cohérente de gestion des secrets et variables d'environnement
   - Considérer les aspects de coûts à long terme et pas seulement les facilités initiales de déploiement

## Conclusion

Ce projet a démontré l'importance d'adapter la stratégie de déploiement cloud au type d'application web développée. Les services web dans le cloud computing offrent une grande flexibilité et permettent de répondre à une variété de besoins, des simples sites vitrines aux applications SaaS complexes.

Nos implémentations pratiques ont confirmé que le choix judicieux de la plateforme de déploiement peut considérablement simplifier le processus de mise en ligne et améliorer les performances, la sécurité et la maintenabilité des applications.

À l'avenir, l'intégration croissante des technologies d'IA dans les services web continuera de transformer le paysage du cloud computing, offrant de nouvelles opportunités mais aussi de nouveaux défis pour les développeurs et architectes.

Finalement, ce projet illustre bien comment les différentes couches du cloud computing (IaaS, PaaS, SaaS) peuvent être exploitées de manière complémentaire pour répondre aux besoins spécifiques de chaque type d'application web.