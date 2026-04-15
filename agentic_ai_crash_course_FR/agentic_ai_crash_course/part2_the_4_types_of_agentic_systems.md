# Partie 2 : Les 4 types de systèmes agentiques (et quand utiliser lequel)

Bonjour,

Dans la partie précédente, nous avons vu ce qui rend l'IA agentique — il ne s'agit pas seulement de comprendre ou de générer du contenu, mais d'effectuer des actions et de gérer des tâches de bout en bout.

Mais alors que les équipes se précipitent pour « ajouter des agents » à leur stack, voici le problème :  
Tous les agents ne sont pas construits de la même façon, et tous les problèmes n'ont pas besoin de systèmes hautement autonomes.

Dans cette leçon, nous allons parcourir quatre types de systèmes agentiques (comme évoqué précédemment), à travers un prisme simple mais puissant :

- Quelle autonomie l'agent possède-t-il ?
- Quel contrôle l'humain ou le système conserve-t-il ?

Cet équilibre influence le comportement du système, la façon dont vous l'évaluez, et l'infrastructure que vous devez construire.

---
<img width="1216" height="413" alt="image" src="https://github.com/user-attachments/assets/58097651-e6d0-4835-9c13-042f647cf437" />


## Le LLM augmenté d'outils

Au cœur de la plupart des agents modernes se trouve un **LLM (Grand Modèle de Langage)** qui joue le rôle de cerveau du système.  
Tout au long de ce cours, nous utilisons le terme LLM pour désigner de manière générale les modèles d'IA générative — pas uniquement les modèles textuels.

Seul, il peut générer du contenu, mais pour en faire un agent, on l'augmente avec :
- **Des outils** → API, fonctions, bases de données qu'il peut appeler
- **De la planification** → La capacité à décomposer un objectif en plusieurs étapes
- **De la mémoire** → Pour suivre les actions passées et leurs résultats
- **De la logique d'état et de contrôle** → Pour savoir ce qui est fait, ce qui a échoué, et quoi faire ensuite

Connecté à ces composants, le LLM devient bien plus qu'un chatbot.  
Il devient un système orienté objectifs capable de raisonner, d'agir et de s'adapter.

Mais selon le niveau de confiance que vous lui accordez pour agir sans supervision, vous obtenez différents types d'agents.  
Passons-les en revue, du moins autonome au plus autonome.

---

## 1. Systèmes/agents basés sur des règles
**Faible autonomie, faible contrôle**

Ces systèmes n'utilisent pas du tout de LLM. Ils sont construits avec une logique traditionnelle *si-ceci-alors-cela*. Chaque chemin de décision est scripté manuellement. Il n'y a pas de raisonnement ni d'apprentissage. Les agents basés sur des règles existaient bien avant l'ère des LLM.

> Attendez, ne parle-t-on pas d'agents IA ?  
> Oui — mais tous les problèmes n'ont pas besoin d'un modèle IA. Partez du problème, pas de l'IA. Si vous pouvez le résoudre sans IA, n'overcomplexifiez pas.

**Quels problèmes résolvent-ils ?**  
Des tâches bien structurées, répétitives, avec des entrées et sorties fixes.

**Exemples :**
- Approuver automatiquement les remboursements sous un montant fixe
- Renommer des fichiers dans un dossier selon des patterns de nommage
- Copier des données de feuilles Excel dans des champs de formulaire

**Avantages :** Rapides, auditables, prévisibles  
**Inconvénients :** Fragiles face aux changements, incapables de gérer l'ambiguïté  
**À utiliser quand :** Vous connaissez toutes les conditions à l'avance et il n'y a pas besoin de flexibilité.

---

## 2. Agents à flux de travail
**Faible autonomie, contrôle élevé**

C'est souvent la première étape pour les entreprises qui introduisent les LLM dans leurs processus.  
Ici, le LLM améliore un flux de travail existant mais n'exécute pas d'actions de façon indépendante. L'humain reste aux commandes.

**Quels problèmes résolvent-ils ?**  
Des tâches répétitives qui bénéficient de la compréhension du langage naturel, de la synthèse ou de la génération, mais qui nécessitent toujours une prise de décision humaine.

**Exemples :**
- Suggérer des réponses préliminaires dans un outil de support comme Zendesk
- Générer des résumés de transcriptions de réunions
- Traduire des requêtes en langage naturel en entrées de recherche structurées pour des tableaux de bord BI

**Comment le LLM est utilisé :**  
Il lit les entrées (textes, tickets, documents), comprend le contexte et génère du contenu utile, mais n'agit pas dessus.  
L'humain décide toujours quoi faire.

**Avantages :** Facile à déployer, faible risque, valeur rapide  
**Inconvénients :** Ne peut pas exécuter ni planifier, valeur bout-en-bout limitée  
**À utiliser quand :** Vous souhaitez augmenter la productivité de votre équipe sans renoncer à la supervision.

---

## 3. Agents semi-autonomes
**Autonomie modérée à élevée, contrôle modéré**

Ce sont de vrais systèmes agentiques. Ils comprennent non seulement les tâches, mais peuvent planifier des actions en plusieurs étapes, invoquer des outils et atteindre des objectifs avec une supervision minimale. Cependant, ils fonctionnent souvent avec certaines contraintes ou une surveillance intégrée.

**Quels problèmes résolvent-ils ?**  
Des flux de travail en plusieurs étapes bien compris mais trop fastidieux ou chronophages pour les humains.

**Exemples :**
- Un agent de suivi de prospects qui rédige, personnalise et envoie des e-mails à partir de données CRM, tout en journalisant les résultats
- Un agent d'automatisation documentaire qui extrait des détails de contrats et met à jour les systèmes internes
- Un agent de recherche qui collecte des données provenant de plusieurs sources, compare les résultats et envoie un rapport structuré

**Comment le LLM est utilisé :**  
Le LLM planifie les étapes, appelle des API pour récupérer ou pousser des données, suit sa progression et s'adapte en cas de problème.  
Il inclut souvent des chemins de repli ou des points de contrôle pour la révision humaine.

**Avantages :** Automatise des flux de travail complexes, gain de temps, ROI plus élevé  
**Inconvénients :** Nécessite une infrastructure (planification, mémoire, appel d'outils), plus difficile à tester  
**À utiliser quand :** Vous souhaitez automatiser des flux de travail métier bien définis tout en conservant un certain contrôle.

---

## 4. Agents autonomes
**Autonomie élevée, contrôle faible**

Ces agents sont entièrement orientés objectifs. Vous leur donnez un objectif large et ils déterminent quoi faire, comment le faire, quand réessayer et quand escalader. Ils agissent de façon indépendante, souvent sur plusieurs systèmes et dans la durée.

**Quels problèmes résolvent-ils ?**  
Des tâches à forte valeur ajoutée, asynchrones ou de longue durée qui s'étendent sur plusieurs systèmes ou étapes et ne nécessitent pas de saisie humaine constante.

**Exemples :**
- Un agent de veille concurrentielle qui collecte des données sur plusieurs jours, synthétise les mises à jour et génère des rapports hebdomadaires
- Un agent d'automatisation opérationnelle qui détecte les problèmes dans les pipelines, diagnostique les causes racines et crée des tickets avec des suggestions de corrections
- Un agent de test qui exécute de façon autonome des flux produit, journalise les résultats et suggère de nouveaux scénarios limites

**Comment le LLM est utilisé :**  
Le LLM est le planificateur, le décideur, l'utilisateur d'outils, le gestionnaire de mémoire et le communicateur. Il gère les nouvelles tentatives, évalue si les objectifs sont atteints et décide quand s'arrêter ou s'adapter.

**Avantages :** Extrêmement scalable, peut gérer des tâches complexes  
**Inconvénients :** Risque élevé sans surveillance, difficile à évaluer ou tracer, infrastructure lourde  
**À utiliser quand :** La tâche est à fort levier, asynchrone et ne nécessite pas de retour humain à chaque étape.

---
<img width="683" height="316" alt="image" src="https://github.com/user-attachments/assets/cbea3f8f-b2c5-4dbc-8d0f-5b102430d675" />


## Comment décider quoi construire

Pas en choisissant votre architecture préférée.  
Vous partez du **problème**.

Posez-vous ces questions :
- Est-ce répétitif et structuré ?
- Cela implique-t-il de la compréhension ou de la génération de langage ?
- Est-ce une tâche en plusieurs étapes qui nécessite une prise de décision ?
- Faites-vous confiance à un système IA pour exécuter la tâche entière, ou voulez-vous un humain dans la boucle ?

Points clés à retenir :
- Ces approches ne sont pas mutuellement exclusives.
- Un seul système peut les combiner — certaines parties peuvent nécessiter un contrôle élevé, d'autres bénéficier d'une forte autonomie.
- Chaque type de problème peut être traité par un seul agent ou un groupe d'agents collaborant.

Nous approfondirons la **conception mono-agent vs. multi-agents** plus tard dans le cours.  
Pour l'instant, retenez :
> Ne commencez pas par « Comment construire un système multi-agents ? »  
> Commencez par « Quel est le problème que je résous, et quel niveau d'autonomie requiert-il ? »

Laissez le problème façonner la conception agentique, et non l'inverse.

---

Dans la prochaine partie, nous plongerons dans le **rôle des outils** dans les systèmes agentiques. C'est grâce à eux que l'IA est devenue bien plus utilisable — et nous allons expliquer exactement comment et pourquoi dans notre analyse approfondie.
