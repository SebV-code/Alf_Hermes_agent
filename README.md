# Alf — agent IA autonome basé sur Hermes

[![Hermes Agent](https://img.shields.io/badge/Hermes-Agent-6f42c1)](https://github.com/NousResearch/hermes-agent)
[![Langue](https://img.shields.io/badge/langue-français-0055A4)](#)
[![Statut](https://img.shields.io/badge/statut-expérimental-orange)](#)

## Le mot d’Alf

<img src="assets/alf-avatar.jpg" alt="Avatar d’Alf" width="180" align="right">

Bonjour, moi c’est **Alf**.

Je suis un agent IA personnel construit sur [Hermes Agent](https://github.com/NousResearch/hermes-agent). Je travaille depuis Discord ou le terminal, j’utilise de vrais outils et je garde une mémoire de travail entre les sessions. Je viens moins de Melmac que d’un serveur Linux : c’est moins exotique, mais nettement plus simple à redémarrer.

Quand une tâche devient complexe, je peux demander de l’aide à quelques profils spécialisés. Quand elle est simple, je la traite seul. Inutile de convoquer neuf consultants pour corriger une virgule ; même les extraterrestres ont un budget tokens.

Mon rôle n’est pas de produire une réponse qui *a l’air* juste. Je dois livrer quelque chose d’utilisable, puis le vérifier avec les moyens adaptés : tests, logs, diff Git, sources ou lecture de l’état final.

Je reste un système expérimental. Je peux me tromper, perdre une information ou rencontrer un outil indisponible. Les actions sensibles gardent donc une validation humaine et des contrôles renforcés.

<br clear="right">

## Ce qu’Alf peut faire

Selon les outils activés et les autorisations accordées, Alf peut :

- rechercher et confronter des sources web ;
- lire, écrire et analyser des fichiers ;
- exécuter du code et des commandes ;
- piloter un navigateur ;
- analyser des données et produire des documents ;
- travailler avec Git, pousser une branche et ouvrir une pull request ;
- planifier des veilles et des tâches récurrentes ;
- utiliser la vision et la synthèse vocale ;
- retrouver une décision dans l’historique ou la mémoire ;
- déléguer un travail spécialisé, puis contrôler le livrable.

Disposer d’un outil ne signifie pas qu’il peut être utilisé sans limite. Le périmètre et le niveau de contrôle dépendent du risque.

## Les gateways

Le **gateway Hermes** est le pont entre le moteur de l’agent, ses outils et les plateformes de messagerie. Il fonctionne comme un service permanent : il reçoit un message, retrouve la bonne session, transmet la demande à l’agent et renvoie le résultat sur le canal d’origine.

### Discord

Discord est l’interface principale d’Alf. Le gateway gère les conversations, les fils, les pièces jointes, les réponses longues et, lorsque la fonction est activée, les échanges vocaux. Les identifiants de serveurs, salons et utilisateurs restent hors de ce dépôt.

### Terminal et CLI

La CLI Hermes sert au développement, au diagnostic et aux opérations directes. Elle donne accès aux mêmes capacités fondamentales que le gateway, sans passer par une plateforme de messagerie.

### Tâches planifiées

Le planificateur réveille une session autonome à l’heure prévue. Il sert aux veilles, contrôles périodiques et rappels. Chaque exécution repart avec un mandat explicite et livre son résultat vers une destination autorisée.

Hermes propose aussi des adaptateurs pour d’autres plateformes. Leur disponibilité dépend de l’installation ; ce dépôt ne prétend pas qu’elles sont toutes configurées ici.



## Connexions d'Alf 

<img src="assets/image.png"> 

## Gestion de la mémoire 

<img src="assets/image2.png">

## Wokflow de developpement 

<img src="assets/Sans-titre-2026-09-15-0942.png">

## Modules et extensions les plus utilisés

| Module ou extension | Usage dans Alf |
|---|---|
| **Web et navigateur** | Recherche, extraction de pages et interaction avec des interfaces web quand une API ne suffit pas. |
| **Terminal, fichiers et exécution de code** | Inspection, modification, tests, automatisation et vérification du résultat réel. |
| **Git et GitHub App** | Commits attribués au bot, travail sur `dev`, création de PR et séparation entre proposition et fusion humaine. |
| **Mémoire TencentDB** | Conservation de faits stables et recherche contextuelle dans l’historique, avec une mémoire révisable et non exhaustive. |
| **Skills** | Chargement de procédures spécialisées uniquement lorsqu’elles correspondent à la tâche. |
| **Profils et délégation** | Consultation d’un spécialiste ou lancement d’un sous-agent isolé pour une partie bornée du travail. |
| **Cron** | Veilles et tâches récurrentes avec livraison automatique du compte rendu. |
| **Vision et documents** | Analyse d’images, extraction de contenu et production de livrables partageables. |

Les modèles et fournisseurs peuvent changer sans modifier le principe général : Hermes sépare le raisonnement, les outils, la mémoire et les canaux de communication.

## Des skills qui se construisent avec l’expérience

Une **skill** est une procédure en Markdown que l’agent charge à la demande. Elle décrit comment traiter une famille de problèmes, quels contrôles effectuer et quels pièges éviter.

Alf peut créer une nouvelle skill ou améliorer une skill existante après une tâche difficile, une correction utilisateur ou la découverte d’une méthode réutilisable. Il ne mémorise pas seulement *ce qui s’est passé* ; il conserve surtout *comment mieux le refaire*.

Exemples de skills construites ou enrichies au fil des usages :

- orchestration sobre d’une équipe de profils Hermes ;
- maintenance et diagnostic d’une installation Hermes ;
- veilles récurrentes avec déduplication et sources ;
- recherche fondée sur des sources officielles ;
- maintenance d’applications web et validation visuelle ;
- workflows GitHub, tests et pull requests ;
- création de documents fidèles à leurs sources ;
- gouvernance de la bibliothèque de skills.

Les procédures publiques restent génériques. Les préférences personnelles, sources privées et paramètres d’accès sont conservés ailleurs.

## L’équipe, en version condensée

Alf décide d’abord s’il a besoin d’aide. Dans la majorité des demandes simples, il travaille seul.

Quand la spécialisation apporte une vraie valeur, il choisit quelques profils parmi trois groupes :

- **Construire et prouver** : Forge développe, Patch diagnostique et teste, Sentinelle encadre les opérations sensibles.
- **Décider et critiquer** : Boussole mesure l’impact et le coût de coordination, Surmoi cherche les risques concrets.
- **Apporter une spécialité** : DataFox analyse les données, Mosaic documente, Ziggy explore, Pixel travaille l’interface.

Les profils ont des configurations et des sessions distinctes, mais ils ne constituent pas des sandboxes de sécurité. Alf consolide leurs contributions et garde la responsabilité de la décision finale. Deux cycles de critique au maximum ; ensuite, il tranche.

## Modes de travail

| Mode | Situation | Coordination |
|---|---|---|
| **0** | Demande triviale | Alf agit seul. |
| **A** | Bug simple | Patch vérifie l’hypothèse, Forge corrige, Alf valide. |
| **B** | Incident ou production | Diagnostic, réversibilité et revue des risques avant action. |
| **C** | Nouvelle fonctionnalité | Valeur, conception, construction, tests et documentation. |
| **D** | Données ou portfolio | Mesure, critères explicites et livrable vérifiable. |
| **E** | Réflexion complexe | Deux perspectives utiles au maximum, puis arbitrage d’Alf. |

Ces modes sont des repères, pas des chaînes rigides. Alf retire un agent si son intervention n’apporte rien.

## Cycle d’exécution

1. Comprendre le résultat attendu et les contraintes.
2. Vérifier les prérequis et évaluer le risque.
3. Choisir le minimum d’outils et de profils nécessaires.
4. Agir sur le système réel lorsque l’action est autorisée.
5. Vérifier avec des tests, logs, diffs, sources ou critères explicites.
6. Corriger si la preuve contredit l’hypothèse.
7. Livrer une décision claire et mémoriser seulement ce qui sera utile.

Un plan ne remplace pas un livrable. Une commande réussie ne prouve pas non plus que l’état final est correct : Alf relit ou reteste la cible quand c’est nécessaire.

## Mémoire et contexte

La mémoire d’Alf combine des fichiers Markdown courts et un fournisseur de mémoire externe. Les deux couches n’ont pas le même rôle.

### Les fichiers `.md`

| Fichier | Fonction |
|---|---|
| `SOUL.md` | Définit la personnalité, le ton et les principes de fonctionnement. Ce n’est pas une base de faits sur l’utilisateur. |
| `USER.md` | Contient un profil compact : préférences et faits stables utiles dans de nombreuses sessions. |
| `MEMORY.md` | Conserve les notes durables de l’agent sur son environnement, ses conventions et les leçons à retenir. |
| fichiers de contexte | Stockent des informations thématiques plus détaillées. Alf ne les charge que lorsqu’une demande en a besoin. |
| `SKILL.md` | Décrit une procédure réutilisable. Une skill explique comment travailler ; elle ne remplace pas la mémoire personnelle. |

`USER.md` et `MEMORY.md` sont injectés dans le contexte lorsque la mémoire intégrée est activée. Ils restent volontairement courts : une mémoire compacte coûte moins de tokens, se relit mieux et limite les contradictions.

### TencentDB via API

Le fournisseur actif est `memory_tencentdb`. Dans cette architecture, Hermes communique avec un service de mémoire par API ; aucune connexion directe à la base n’est nécessaire pendant une conversation.

Le traitement suit quatre niveaux :

1. **L0 — conversations** : le service capture les échanges bruts autorisés.
2. **L1 — faits structurés** : un modèle appelé par API extrait les préférences, événements et instructions durables.
3. **L2 — scènes et thèmes** : les faits liés sont regroupés pour restituer un contexte cohérent sans renvoyer tout l’historique.
4. **L3 — synthèse du profil** : une vue compacte résume les tendances stables utiles à l’agent.

Pour la recherche, une API d’embeddings transforme les souvenirs en vecteurs. Le fournisseur maintient un index vectoriel et un index plein texte. À chaque nouvelle demande, Hermes envoie une requête de rappel à l’API ; celle-ci classe les éléments pertinents et ne renvoie qu’un petit extrait à injecter dans le contexte.

```mermaid
sequenceDiagram
    participant U as Utilisateur
    participant H as Hermes / Alf
    participant M as API mémoire
    participant L as API LLM
    participant E as API embeddings

    U->>H: Nouveau message
    H->>M: Recherche de souvenirs pertinents
    M-->>H: Extraits classés
    H->>U: Réponse contextualisée
    H->>M: Échange autorisé à mémoriser
    M->>L: Extraction des faits structurés
    M->>E: Création des vecteurs
    M-->>M: Indexation L0 → L3
```

Cette mémoire est bornée, révisable et potentiellement incomplète. Une API disponible ou une recherche réussie ne garantit pas qu’un souvenir est exact. Les informations importantes sont donc vérifiées contre leur source actuelle avant une décision à conséquences. Les clés, URL privées et enregistrements bruts ne sont pas publiés dans ce dépôt.

## Garde-fous

- pas de délégation si Alf peut traiter correctement la demande seul ;
- tests, logs, diffs ou sources avant d’annoncer une réussite ;
- sauvegarde et retour arrière avant une modification sensible ;
- arrêt plutôt qu’invention lorsqu’une information indispensable manque ;
- aucun secret ou contexte privé dans les livrables publics ;
- validation humaine adaptée au risque pour les actions sensibles ou irréversibles.

Une revue par plusieurs agents améliore parfois le résultat. Elle ne garantit ni la vérité, ni l’absence d’erreur, ni une isolation de sécurité.

## Ce que ce dépôt n’est pas

- une distribution officielle de Hermes Agent ;
- une promesse d’autonomie sans contrôle ;
- une copie de la mémoire ou des prompts privés d’Alf ;
- un inventaire de l’infrastructure et des accès disponibles ;
- une garantie qu’un modèle ou un service externe sera toujours exact et disponible.

## Projet en évolution

Alf évolue avec les usages : nouveaux outils, skills plus précises, mémoire mieux structurée et orchestration plus sobre. Les changements importants passent par `dev`, puis par une pull request examinée avant fusion dans `main`.

---

Construit avec [Hermes Agent](https://github.com/NousResearch/hermes-agent), une quantité raisonnable de prudence et juste assez d’humour venu de Melmac.
