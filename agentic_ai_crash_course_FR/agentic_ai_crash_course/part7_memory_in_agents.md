# Partie 7 : La mémoire dans les agents

---

Au cours des dernières parties, nous avons exploré ce qui fait agir les agents — des **outils** et du **RAG**, au **MCP** et aux **modèles de raisonnement**.

Aujourd'hui, nous nous tournons vers ce qui détermine **à quel point** ils agissent bien dans le temps : la **mémoire**.

Car voici la réalité de base :  
Les modèles IA **n'ont pas de mémoire intrinsèquement**. Ils sont **sans état** par conception. Chaque entrée est traitée indépendamment sauf si vous **architecturez la mémoire dans le système**.

---

## Pourquoi la mémoire est importante
<img width="438" height="164" alt="image" src="https://github.com/user-attachments/assets/1d3fccea-8f9a-42b8-baa4-b3fe9f57dad1" />


_Source de l'image : https://arxiv.org/html/2502.12110v1_

Si un agent vous aide à rédiger des e-mails, résumer de longs fils de discussion ou gérer des flux de travail sur des jours ou des semaines — il doit se souvenir :
- Du format des e-mails
- Du nom de l'utilisateur
- Du ton à utiliser

Bien sûr, vous pourriez passer ces informations encore et encore à chaque prompt…  
Mais ne serait-il pas mieux que l'agent puisse récupérer les bonnes informations **par lui-même**, au bon moment, depuis une **base de données externe** ?

C'est exactement là qu'intervient la **mémoire**.

---

## « Attends… n'est-ce pas comme le RAG Agentique (Partie 4) ? »

Bonne question — et vous n'avez pas tort. La gestion de la mémoire ressemble souvent beaucoup à du RAG Agentique.

Vous :
1. Écrivez des souvenirs structurés ou non structurés (faits, journaux, sorties passées)
2. Les stockez avec des métadonnées, des tags ou des embeddings
3. Récupérez le bon extrait quand nécessaire
4. Fondez la prochaine action du modèle en utilisant ce contexte

**La différence :**
- **RAG** → Aide à répondre aux questions avec des connaissances.
- **Mémoire** → Aide les agents à se comporter de façon cohérente dans le temps.

---

## Deux types de mémoire dans les agents

Lors de la conception de systèmes agents réels, vous faites généralement face à **deux types de mémoire**.

<img width="571" height="372" alt="image" src="https://github.com/user-attachments/assets/7c2d9e58-a219-4cea-b9f0-6de091298d66" />


_Source de l'image : https://langchain-ai.github.io/langgraph/concepts/memory/#what-is-memory_

---

### 1. Mémoire à court terme

Limitée à une seule session ou tâche.

**Comprend :**
- La conversation jusqu'à présent
- Les outils utilisés
- Les réponses générées
- Les documents récupérés

Pensez-y comme un journal brut des conversations utilisateur-agent.

LangGraph, Autogen et autres frameworks similaires traitent cela comme faisant partie de l'**état** de l'agent.  
Mais l'état grossit vite, et la plupart des agents performent mal quand ils sont noyés sous un historique non pertinent.

**Stratégies pour gérer la mémoire à court terme :**
- Élaguer les messages périmés
- Résumer le passé en points clés
- Filtrer selon ce qui est encore pertinent

C'est un équilibre : **longueur de contexte vs clarté vs coût**.

---

### 2. Mémoire à long terme

Persiste entre les sessions, les jours, les semaines — voire indéfiniment.

**Aide les agents à se souvenir :**
- Qui est l'utilisateur
- Comment il préfère interagir
- Ce qui a déjà été fait
- Du contexte passé important

**Exemples :**
- « L'utilisateur préfère un ton neutre »
- « Le nom de l'utilisateur est X et il réside dans la ville Y »
- « La facture n°123 a déjà été escaladée »

Plus de données ≠ mieux par défaut — il s'agit de récupérer la bonne chose au bon moment.

---

## Types de mémoire à long terme à considérer

En s'inspirant des sciences cognitives :

- **Mémoire sémantique** → Faits et informations (objectives)  
  _« L'utilisateur parle anglais et préfère les fichiers Excel. »_

- **Mémoire épisodique** → Actions passées  
  _« L'agent a déjà généré un résumé hier. »_

- **Mémoire procédurale** → Préférences (subjectives)  
  _« Éviter la voix passive. Prioriser les actions. »_

---

**Exemples par cas d'usage :**

- **Chatbots orientés utilisateur** → Mémoire sémantique pour la personnalisation
- **Agents d'automatisation de processus** → Mémoire épisodique pour éviter les réessais ou les boucles
- **Assistants adaptatifs** → Mémoire procédurale pour ajuster les prompts en fonction des retours

---

## Questions clés de conception

Avant de dire « nous avons besoin de mémoire », demandez-vous :
- **Quel type ?**
- **Pourquoi est-elle nécessaire ?**
- **Comment sera-t-elle stockée, récupérée et maintenue à jour ?**

---

## Gérer la mémoire en pratique

Gérer la mémoire ressemble souvent à gérer du RAG.  
La partie difficile ? Décider **quoi stocker** et **quoi récupérer**.

Bourrer l'entrée de l'agent de plus de texte aide rarement — cela **nuit souvent aux performances**.

Vous devez concevoir la mémoire intentionnellement, en fonction de :
- Le rôle de l'agent
- Ce qu'il doit se rappeler
- Quand il doit le rappeler
- Comment le maintenir utile dans le temps

---

## Quelques exemples en entreprise

**Agent de support client**
- Besoins : historique récent du support, bugs connus, sentiment de l'utilisateur
- Types de mémoire : épisodique + sémantique

**Copilote commercial**
- Besoins : présentations précédentes, objections des utilisateurs, statut de clôture
- Types de mémoire : sémantique + procédurale

**Agent auditeur de conformité**
- Besoins : éléments signalés, exceptions passées, changements de politique
- Types de mémoire : épisodique

---

Dans tous les cas, il ne s'agit pas de **combien** de données vous stockez — il s'agit de **leur pertinence et leur structure**.

Et oui, je l'ai dit de nombreuses fois, mais je le répète :
> **Problème d'abord, toujours.** La stratégie mémoire, comme les outils ou la planification, dépend entièrement du problème que vous résolvez.

---

## À suivre

Dans la prochaine partie, nous parlerons des **systèmes multi-agents** — ce qu'ils sont, comment ils se coordonnent, et si vous avez vraiment besoin de plus d'un agent.
