# Partie 6 : La planification dans les agents + les modèles de raisonnement

---

## Nous sommes à plus de la moitié du cours !

Au cours des dernières parties, nous avons parlé de ce que les agents peuvent faire :
- Utiliser des outils
- Récupérer des informations via le RAG
- Tout transmettre dans un format propre grâce au MCP

Mais tout cela présuppose quelque chose de fondamental :  
**Que l'agent sait réellement quoi faire ensuite.**  
Et c'est souvent là que ça coince.

Aujourd'hui, nous déplaçons notre attention des outils et des entrées vers **comment les agents pensent** — plus précisément, comment les modèles modernes commencent à planifier et pourquoi cela change la façon dont nous concevons des systèmes réels.

---

## Pourquoi la planification est importante dans les systèmes agentiques

Voici quelques exemples pour commencer.

Si vous demandez à un agent :
> « Combien font 13 multiplié par 47 ? »  
…il peut soit le résoudre directement, soit appeler une calculatrice. C'est une tâche en une seule étape — pas vraiment besoin de planification.

Imaginez maintenant demander :
> « Trouvez tous nos clients du T1 dans le secteur de la santé, vérifiez lesquels ont des paiements en retard, et rédigez des e-mails personnalisés avec de nouveaux liens de paiement. »

Dans ce cas, l'agent doit :
- Comprendre l'instruction
- La décomposer en parties gérables
- Récupérer les bonnes données
- Choisir les outils
- Effectuer les étapes dans l'ordre
- Gérer les exceptions
- Savoir quand la tâche est terminée

Cette boucle d'interprétation, de séquençage et d'action, c'est la **planification**.

L'agent (c'est-à-dire le modèle) est censé comprendre tout cela par lui-même — y compris quels outils utiliser et comment appliquer les informations disponibles.

---

## Pourquoi les LLM traditionnels peinent avec la planification

La plupart des LLM polyvalents n'ont jamais été entraînés pour ça.

Ils sont entraînés à **prédire le prochain token** en fonction du contexte précédent — rien de plus.  
Ils excellent dans :
- La continuation de phrases
- La génération de résumés
- La réponse à des questions directes

…mais ils se comportent davantage comme des **générateurs à courte vue**.  
Ils complètent ce qui est devant eux mais ne sont pas câblés pour anticiper.

Lorsqu'on leur demande d'agir comme agents dans des tâches de prise de décision en plusieurs étapes, ils ont tendance à :
- Sauter des étapes
- Répéter des actions
- Surcomplexifier des choses simples
- Perdre le fil à mi-chemin

---

## Les premières tentatives pour améliorer le raisonnement

Pour combler ce manque, les développeurs ont expérimenté des techniques de prompting pour encourager un comportement de planification.

Un exemple populaire : le **prompting par chaîne de pensée** (Chain-of-Thought) — ajouter « Réfléchissons étape par étape » pour décomposer les tâches en phases.

Cela fonctionnait pour les puzzles logiques et les Q&R structurées, mais s'avérait insuffisant pour les **vrais agents** travaillant avec :
- Des outils
- Des entrées imprévisibles
- Un état changeant

Car en dessous, ces modèles n'étaient toujours pas entraînés pour la planification — ils répondaient simplement à des **astuces de prompt**.

---

## Puis sont arrivés les modèles de raisonnement

Le prochain tournant : entraîner les modèles à planifier **par conception**.

C'est ainsi qu'ont émergé les **Grands Modèles de Raisonnement (LRM)**.
<img width="743" height="663" alt="image" src="https://github.com/user-attachments/assets/ce4d8d91-b539-4003-adfc-1fa6dcfd3631" />

**LLM :**  
entrée → LLM → énoncé de sortie

**LRM :**  
entrée → LRM → étape de plan + énoncé de sortie

Tout est encore du texte, mais les LRM sont encouragés lors de l'entraînement à **penser avant d'agir**.

---

**Exemples :**
- La **série o d'OpenAI** (o1, o3) — premiers exemples publics
- **DeepSeek-R1 de DeepSeek** — optimisé pour le raisonnement et la planification augmentés par outils
- Les **modèles de réflexion Gemini de Google**
- Le **mode de raisonnement Claude 3.7 d'Anthropic**

Certains activent même le raisonnement **uniquement si nécessaire**.

---

## Comment ils s'intègrent dans la conception agentique

La principale valeur des modèles de raisonnement réside dans l'amélioration du **composant de planification** — la partie qui demande :
> « Que dois-je faire ensuite, et pourquoi ? »

Dans les cas d'usage en entreprise, **la planification est là où les agents échouent souvent**.  
Les modèles de raisonnement peuvent aider, mais ils ne sont pas magiques.

---

## À utiliser avec précaution

Les modèles de raisonnement sont encore **nouveaux** et comportent des compromis :
- Surraisonnent sur des tâches simples
- Génèrent des sorties plus longues
- Augmentent la latence et les coûts
- Peuvent halluciner des plans logiquement cohérents mais incorrects

**Règle empirique :**
- Ne commencez pas avec un modèle de raisonnement.
- Commencez avec un modèle de base de taille moyenne.
- Passez à un modèle de raisonnement uniquement si vous observez des échecs de planification évidents — et même alors, évaluez l'impact réel.

---

## À suivre

Dans la prochaine partie, nous aborderons un autre **composant fondamental des agents** : la **mémoire** — comment les agents peuvent se souvenir efficacement et pourquoi c'est crucial.
