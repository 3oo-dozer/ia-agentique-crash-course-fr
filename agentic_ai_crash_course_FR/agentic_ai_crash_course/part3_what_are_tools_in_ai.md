# Partie 3 : C'est quoi les outils en IA ?

Dans la partie précédente, nous avons parlé des différents types d'agents, des systèmes basés sur des règles aux agents entièrement autonomes, et comment le bon niveau d'autonomie dépend du problème à résoudre.

Mais voici un trait commun à tous les types d'agents, aussi simples ou complexes soient-ils :

> **Ils s'appuient sur des outils pour effectuer des actions.**

---

## Que sont les « outils » en IA ?

Dans le contexte de l'IA agentique, les outils sont des capacités externes que le LLM peut invoquer, comme :
- Des API
- Des requêtes en base de données
- Des services internes
- Des systèmes tiers
- Des fonctions internes écrites en code

Ils transforment le LLM d'un système qui se contente de **parler** en un système capable d'**agir**.

Rappelons-le, les LLM sont par nature **sans état**, n'ont **pas accès aux systèmes en temps réel** et **ne peuvent pas prendre d'action**.

---

## Mais donnez-leur des outils, et ils peuvent :
- Récupérer des données de vos systèmes internes
- Déclencher des événements (ex. : envoyer un e-mail, créer un ticket JIRA)
- Accéder à des données structurées comme des calendriers, des tableaux de bord ou des CRM
- Exécuter une logique prédéfinie basée sur des règles métier

C'est ainsi que **la génération se transforme en exécution**.

---

## Pourquoi les outils sont importants

1. **Ils débloquent l'exécution**  
   Sans outils, votre agent n'est qu'un assistant qui fait des suggestions.  
   Avec des outils, il peut accomplir des flux de travail de bout en bout.

2. **Ils augmentent la précision**  
   Plutôt que d'halluciner, le LLM peut interroger directement le bon système —  
   « Quel est le statut réel de la commande ? » plutôt que d'inventer une raison de retard.

3. **Ils vous permettent de contrôler le risque**  
   Vous définissez ce qui est exposé. Le LLM ne peut rien faire en dehors des outils que vous enregistrez.

4. **Ils permettent la composabilité**  
   Si vous voulez combiner votre CRM, votre calendrier et votre stack e-mail dans un seul assistant,  
   vous pouvez exposer chacun d'eux comme des outils et laisser le LLM les orchestrer.

---

## Exemple pas à pas : tâche complète d'un agent utilisant des outils

**Tâche :**
> « Informer un client que sa commande est retardée et proposer un nouveau délai de livraison. »

**Voici comment le système fonctionne avec des outils :**

**Entrée** — Un humain écrit :  
_« Hé, pouvez-vous prévenir John que sa commande est retardée et la reprogrammer pour demain ? »_

**Planification** — Le LLM décompose la tâche :
- Vérifier le statut de la commande
- Si retardée, vérifier les créneaux de livraison disponibles
- Rédiger un e-mail
- Envoyer l'e-mail
- Journaliser l'interaction

**Appels d'outils :**
```text
get_order_status(order_id=12345)
get_available_slots(date=today+1)
send_email(to=john@example.com, content=...)
log_event(event_type="reprogrammation", status="terminé")
```

**Génération de texte** — Le LLM compose le message :  
_« Bonjour John, je vous informe que votre commande a été retardée. Nous l'avons reprogrammée pour demain. Merci de votre patience. »_

**Exécution** — Le système exécute les actions, journalise la sortie et envoie optionnellement une mise à jour de statut à un tableau de bord.

---

## Comment ça fonctionne (visuel)
<img width="808" height="357" alt="image" src="https://github.com/user-attachments/assets/f7ce3097-873f-4519-b7ba-30b80785deae" />


Voici ce qui se passe :

1. L'utilisateur pose une question ou donne une tâche.
2. Le LLM comprend ce qui doit être fait et planifie sa prochaine étape.
3. Un parseur convertit l'idée du LLM en un format structuré (comme `get_order_status(order_id=12345)`).
4. L'agent appelle le bon outil — API, requête de base de données ou fonction interne.
5. L'outil retourne un résultat — c'est ce qu'on appelle une **observation**.
6. Le LLM examine le résultat, décide ce qui manque ou ce qui vient ensuite.
7. Cette boucle continue jusqu'à ce qu'il ait assez pour générer la réponse finale ou accomplir la tâche.

Le LLM utilise le résultat de chaque outil pour guider sa prochaine décision.

---

**Rappel clé :**  
Le LLM lui-même ne fait que générer du texte.  
Ce texte est structuré en appels d'outils, exécuté en externe, et les résultats sont réinjectés dans le LLM — créant une boucle de raisonnement, d'action et de réflexion (**a.k.a. un agent**).

Cette structure est utilisée par des frameworks comme **LangChain**, **CrewAI**, **AutoGen**, et même des orchestrations personnalisées en production.

---

## Qu'est-ce qui rend un outil utilisable par un LLM ?

Pour enregistrer un outil dans un système agent, vous définissez généralement :
- **Nom** (ex. : `create_meeting`)
- **Description** (pour que le modèle sache quand l'utiliser)
- **Paramètres d'entrée** (et leurs types)
- **Structure de sortie** (pour que le modèle puisse utiliser le résultat)

Ces métadonnées permettent au LLM de raisonner sur quel outil utiliser et comment.

---

## Note sur le parsing et les sorties structurées

Le parseur joue un rôle clé dans la conversion de la réponse du LLM en un appel d'outil structuré — quelque chose que le système peut exécuter de façon fiable (comme `get_order_status(order_id=12345)`).

Mais dans de nombreuses configurations modernes, vous n'avez pas toujours besoin d'un parseur séparé.  
La plupart des LLM populaires, notamment ceux conçus pour l'utilisation d'outils, peuvent directement produire des sorties structurées — comme du JSON ou des appels de fonctions — directement consommables par votre backend.

De même, les outils bien conçus retournent des données structurées, ce qui facilite le raisonnement du LLM sur la prochaine étape.

**La structure des deux côtés** (entrée et sortie) est ce qui rend les boucles agent **robustes, traçables et adaptées à la production**.

---

## La conclusion à retenir

Tout cela vous semblera familier si vous avez déjà construit ou travaillé avec des API.  
Mais si ce n'est pas votre monde, ne vous perdez pas dans les détails techniques.

Retenez simplement ceci :
> Les modèles IA seuls peuvent **comprendre** et **générer**.  
> Quand ils sont connectés à des logiciels, des outils, des API et des systèmes internes — ils peuvent vraiment **faire des choses**.

---

Dans la prochaine partie, nous découvrirons la **Génération Augmentée par Récupération (RAG)** — ce que c'est, quand l'utiliser, et comment elle s'intègre naturellement dans les pipelines agentiques en tant que couche de mémoire ou de contexte.
