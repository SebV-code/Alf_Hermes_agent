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

Le but a été de trouver un équilibre entre la taille de la mémoire injectée et la consommation en token du contexte.
Le soul.md qui est injecté à chaque requête doit rester sobre.
La mémoire vectorisée proposé par le plugin tencent memory db est un très bon compromis, puisqu'elle vectorise toutes les conversations à l'aide de petits appels api à des modèles légers d'embeddings. Cette gestion de la memory a été game changer dans l'utilisation d'Alf

<img src="assets/image3.png">


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
...

## L’équipe de subagents :

Avec Alf nous avons définit une équipe de sous-agents aux personas complémentaires, inspiré des études scientifiques en psychologie du travail et du management, et aux missions adaptés à nos besoins :

| Forge | Développer un code simple et maintenable. |
| Patch | Diagnostiquer les bug |
| Surmoi | Revue critique, sécurité, secrets |
| Ziggy | Idéation, angles inattendus |
| Pixel | UI/UX, sites et interfaces web |
| DataFox | Data, SQL, Python, Sheets
| Mosaic | Documentation, synthèses, plans, décisions et mémoire collective. |
| Sentinelle | VPS, Caddy, service
| Boussole | Stratégie produit/carrière, arbitrage impact-effort, priorisation. |


Alf décide d’abord s’il a besoin d’aide. Dans la majorité des demandes simples, il travaille seul.

Quand la spécialisation apporte une vraie valeur, il choisit quelques profils parmi trois groupes :

- **Construire et prouver** : Forge développe, Patch diagnostique et teste, Sentinelle encadre les opérations sensibles.
- **Décider et critiquer** : Boussole mesure l’impact et le coût de coordination, Surmoi cherche les risques concrets.
- **Apporter une spécialité** : DataFox analyse les données, Mosaic documente, Ziggy explore, Pixel travaille l’interface.

Les profils ont des configurations et des sessions distinctes. Alf consolide leurs contributions et garde la responsabilité de la décision finale. Deux cycles de critique au maximum ; ensuite, il tranche.

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


## Garde-fous

- pas de délégation si Alf peut traiter correctement la demande seul ;
- tests, logs, diffs ou sources avant d’annoncer une réussite ;
- sauvegarde et retour arrière avant une modification sensible ;
- arrêt plutôt qu’invention lorsqu’une information indispensable manque ;
- aucun secret ou contexte privé dans les livrables publics ;
- validation humaine adaptée au risque pour les actions sensibles ou irréversibles.

## Wokflow de developpement 
Workflow adapté au développement avec un agent IA, serveurs de dev et de production sont physiquement séparés.
L'agent est maitre de son serveur de dev mais n'a pas de droit en écriture sur le serveur de production.
L'agent pousse son code sur la branche dev du projet et fait des Pull Request, qui sont analysés et mergés si OK

<img src="assets/Sans-titre-2026-09-15-0942.png">

---

Construit avec [Hermes Agent](https://github.com/NousResearch/hermes-agent), une quantité raisonnable de prudence et juste assez d’humour venu de Melmac.
