# Partie 8 : Les systèmes multi-agents

---

Jusqu'à présent, nous avons beaucoup parlé de ce qui fait agir un **agent unique** — des **outils** et du **RAG** à la **mémoire** et la **planification**.

Mais que faire si votre pipeline agentique doit :
- Paralléliser les tâches pour accélérer les choses
- Utiliser différentes personnalités d'agents pour différentes parties d'une tâche
- Répartir la complexité entre des unités spécialisées, comme dans une équipe

C'est là qu'interviennent les **systèmes multi-agents**.

---

## Pourquoi utiliser des systèmes multi-agents ?

Parfois, un seul agent ne suffit pas car le problème exige de l'**échelle**, de la **spécialisation** ou une **réflexion parallèle**.

**Exemples :**
- Générer une stratégie marketing nécessitant des **insights marché**, une **révision juridique** et des **suggestions créatives**.
- Développer un assistant de conformité devant **extraire des informations**, **signaler des risques** et **vérifier des politiques**.
- Automatiser un processus commercial où **un agent** parle à l'utilisateur, **un autre** enrichit les données, et **un troisième** gère les suivis.

Pourrait-on faire tout ça avec un seul agent costaud ?  
**Peut-être.**

Mais diviser en **plusieurs agents spécialisés** peut permettre :
- **La parallélisation** → Les agents travaillent simultanément sur des parties d'une tâche
- **La spécialisation** → Un agent est expert en langage juridique, un autre en rédaction d'e-mails
- **L'indépendance des outils** → Chaque agent peut avoir ses propres outils et sa mémoire

---

## Coordination plate vs hiérarchique des agents

Tous les systèmes multi-agents ont besoin d'un moyen de **coordonner**.  
Deux patterns de communication courants :
<img width="1144" height="626" alt="image" src="https://github.com/user-attachments/assets/c6e2c1c0-bb92-48c8-ba53-dfbfdc6e3926" />


---

### 1. Patterns hiérarchiques (plus contrôlables)

Un **agent orchestrateur** délègue des sous-tâches aux autres.  
Il voit l'ensemble du tableau et contrôle le flux.

**À utiliser quand :**
- Les tâches peuvent être clairement décomposées
- Vous souhaitez un contrôle étroit
- Vous avez des rôles d'agents connus (ex. : synthétiseur, générateur, vérificateur)

**Idéal pour :** les flux de travail d'entreprise, les suites d'outils, les pipelines parallèles.

---

### 2. Patterns plats (plus dynamiques)

Les agents se parlent en tant que **pairs** — sans hiérarchie.

**À utiliser quand :**
- Les tâches nécessitent de la créativité ou du débat
- Vous souhaitez que les agents s'évaluent mutuellement
- Il n'y a pas de chemin de réponse « correct »

**Idéal pour :** le brainstorming, le classement d'options, le raisonnement multi-points de vue.

---

## Ce que personne ne vous dit : les systèmes multi-agents sont une galère

Sur le papier, ça a l'air formidable.  
Et oui, vous pouvez construire rapidement des prototypes multi-agents et vous amuser avec eux.

Mais pour les cas d'usage **clients/entreprise**… c'est douloureux.

La plupart des gens lisent un article sur les systèmes multi-agents et s'enthousiasment pour la modularité —
> « C'est comme des microservices ! » disent-ils.

Mais **les agents IA ne sont pas des microservices**.

Contrairement au code, les modèles IA sont **non déterministes**. Ils ne se comportent pas toujours de la même façon.  
Ajouter plus d'agents signifie :
- Plus de **non-déterminisme** (variation entre les agents, pas seulement au sein d'un seul)
- Plus de **complexité de mémoire et d'état** (qui sait quoi, et quand ?)
- Plus de **latence** et de **coûts**
- Plus de **bugs de coordination** et de points de défaillance
- Plus de **collusion**, où les agents s'accordent alors qu'ils ne le devraient pas (cela arrive plus souvent qu'on ne le croit)

Honnêtement, je pourrais écrire un livre sur la difficulté de faire fonctionner des systèmes multi-agents de façon fiable.

---

## Alors… devriez-vous les utiliser ?

Ma règle personnelle :
> **En entreprise, ne commencez pas avec des multi-agents. Commencez avec un seul.**

Laissez cet **agent unique** échouer — empiriquement (via des métriques d'évaluation) ou opérationnellement — avant de monter en puissance.

D'après mon expérience, **plus de 70 % des cas d'usage en entreprise** fonctionnent très bien avec un seul agent bien conçu — qui utilise **outils**, **mémoire**, **RAG** et **planification**.

---

### Les systèmes multi-agents brillent quand :
- La tâche est assez grande pour nécessiter une **exécution parallèle**
- Vous avez besoin d'une **spécialisation claire**
- Vous souhaitez un **débat créatif**, une évaluation ou une prise de décision distribuée

Même dans ce cas, vous avez besoin d'une **conception solide** — notamment autour de la **mémoire**, de l'**état** et des **protocoles de communication**.

---

## Mot final : problème d'abord, toujours

C'est notre mantra depuis le Jour 1 :
> Ne construisez pas un système multi-agents parce que ça sonne « agentique ».  
> Construisez-en un si — et seulement si — votre problème en a besoin.

La seule façon de le savoir ?
- Avoir les bonnes **métriques**
- Tester
- Laisser les systèmes plus simples échouer d'abord

---

## À suivre

Dans la prochaine partie, nous parlerons des **agents en conditions réelles** et de leur fonctionnement.
