# Partie 10 : Leçons sur les agents IA et perspectives

## Récapitulatif rapide

Voici ce que nous avons couvert au cours des 9 dernières parties :

- **Partie 1 — Ce que sont les agents :** Pas seulement des chatbots qui génèrent du texte, mais des systèmes capables de décider et d'agir.
- **Partie 2 — Types d'agents :** Des agents à flux de travail étroitement contrôlés aux agents entièrement autonomes, selon le niveau de prise de décision que vous déléguez.
- **Parties 3–4 — Outils et RAG :** Le socle de l'action des agents et de l'ancrage des connaissances.
- **Partie 5 — MCP :** Une façon propre de structurer tout ce dont un agent a besoin (outils, mémoire, messages précédents) en un seul payload.
- **Partie 6 — Planification et modèles de raisonnement :** Pourquoi les LLM ordinaires ne suffisent pas pour les décisions complexes, et comment les modèles récents sont conçus pour les tâches en plusieurs étapes.
- **Partie 7 — Mémoire :** Mémoire à court terme vs. long terme, quoi stocker, comment récupérer, et pourquoi c'est crucial pour la continuité.
- **Partie 8 — Systèmes multi-agents :** Orchestration, collaboration pair-à-pair, et la complexité de la coordination.
- **Partie 9 — Systèmes réels :** Comment Perplexity, NotebookLM et DeepResearch utilisent probablement ces patterns de différentes façons.

Nous avons couvert les **composants mobiles** qui apparaissent dans les systèmes réels.  
Mais tout cela s'effondre si vous ne pensez pas à deux choses : l'**observabilité** et l'**évaluation**.

---

## Ce qui reste difficile

### Observabilité
L'observabilité signifie suivre ce que fait votre agent — à chaque étape. Vous voudrez :
- Des journaux d'appels d'outils, de décisions, de nouvelles tentatives
- Des métriques pour repérer les goulots d'étranglement de latence et de coût
- De la visibilité sur quand les choses déraillent
- Une traçabilité étape par étape pour le débogage

Des outils comme **Comet Opik** aident à cela.  
Concevez l'observabilité **dès le premier jour**, notamment pour les agents à haute autonomie.

---

### Évaluation
Les agents sont **non déterministes**.  
Vous avez besoin d'une **évaluation continue**, pas seulement de tests manuels.

Au minimum, suivez :
- Les taux d'achèvement des objectifs ou des tâches
- Le succès/échec des appels d'outils
- La qualité du RAG et les métriques d'hallucination
- Le surraisonnement ou l'inefficacité du modèle
- La latence et l'utilisation des tokens à chaque étape

L'évaluation est la façon dont vous **comprenez** et **améliorez** votre système.  
Trop d'équipes font des *vibe checks* au lieu de vraies évaluations — et se retrouvent coincées dans le **purgatoire du PoC**.

Considérez les évaluations + l'observabilité comme votre **pipeline de tests** — l'équivalent agentique de l'assurance qualité logicielle.  
Les métriques varieront selon le cas d'usage, mais la discipline est la même.

---

## Où va l'IA agentique

Cet espace est encore jeune, mais voici des tendances claires :

---

### 1. Protocoles > Prompts
<img width="800" height="800" alt="image" src="https://github.com/user-attachments/assets/13b78c2e-fc2b-41fd-a0e5-aa88c60187ea" />

_Source de l'image : post LinkedIn de Reuven_

À mesure que les systèmes grandissent, nous passerons des prompts artisanaux vers des **standards** partagés.

- **MCP** (Model Context Protocol) standardise la façon dont nous empaquetons le contexte structuré — outils, mémoire, RAG, instructions préalables.
- **A2A** (Agent-to-Agent), publié par Google, se concentre sur la communication entre agents sur différentes plateformes avec un schéma partagé.

Attendez-vous à des abstractions plus propres avec le temps — bien qu'il faudra du temps avant que quelque chose devienne aussi standard que HTTP.

---

### 2. Modèles de raisonnement hybrides
Les modèles de raisonnement évolueront vers une **planification sélective** — sachant quand planifier vs. agir vite.

Nous observons déjà cela avec **Claude 3.7** et d'autres.  
L'objectif : équilibrer intelligence et efficacité — sans surraisonner sur chaque tâche.

---

### 3. De meilleurs systèmes de mémoire
La mémoire actuelle est principalement **bricolée**.  
L'avenir : une mémoire qui sait **quoi rappeler, quand et pourquoi**.  
Attendez-vous à :
- Une mémoire limitée à la tâche
- Une mémoire limitée à la session
- Une mémoire spécifique à la persona

Et une **gestion plus facile**.

---

### 4. Maturité de l'écosystème d'outils
Aujourd'hui, tout le monde construit des outils/wrappers personnalisés. Avec le temps :
- Des API de confiance prêtes à l'emploi
- De meilleures couches d'abstraction
- Des pratiques de sécurité partagées

Tout comme les microservices ont mûri dans le logiciel traditionnel, les outils mûriront dans la **stack agentique**.

---

## Un mot final

Si vous avez suivi, vous avez vu le fil conducteur :

Nous n'avons pas commencé par l'**architecture**.  
Nous avons commencé par les **problèmes**.

C'est le vrai changement de mentalité :
> Ne courez pas après les agents pour le buzz.  
> Construisez-les quand ils rendent la résolution d'un problème plus facile, plus rapide ou plus intelligente.

**Commencez simplement. Mesurez tout. Montez en puissance si nécessaire.**  
La pensée agents-d'abord brise. La pensée problème-d'abord passe à l'échelle.

---

Merci d'avoir lu, partagé et réfléchi tout au long de ces 10 parties.  
Si vous ne retenez qu'une chose de cette série — que ce soit ceci :

> **Problème d'abord, toujours.**

Consultez le README pour plus de conférences et de sujets avancés. Si cela vous a été utile, n'hésitez pas à le transmettre à quelqu'un qui souhaite apprendre dans cet espace. Et si vous souhaitez approfondir, notre cours complet de 6 semaines couvre la conception de systèmes, les concepts agentiques appliqués et les workflows d'évaluation réels — le genre qui soutient les applications de niveau production. Le cours est conçu pour tous, que vous soyez Chef de Produit, Architecte, Directeur, dirigeant C-suite, ou quelqu'un explorant sérieusement l'IA agentique.

Notre prochaine cohorte commence bientôt. Les tarifs early bird sont en ligne : utilisez le code « GITHUB » pour obtenir 300 $ de réduction (valable uniquement pour août 2025) pour [vous inscrire ici](https://maven.com/aishwarya-kiriti/genai-system-design) !!
