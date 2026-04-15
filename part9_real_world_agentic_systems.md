# Partie 9 : Les systèmes agentiques en conditions réelles (sous le capot)

---

Jusqu'à présent, nous avons couvert tous les ingrédients qui composent un agent :  
**outils**, **planification**, **RAG**, **mémoire**, **structure** et **coordination** dans des configurations multi-agents.

Mais vous vous demandez peut-être :
> « Où tout cela apparaît-il vraiment dans le monde réel ? »

Parcourons quelques systèmes publics qui présentent un **comportement agentique** — dans la mesure où nous pouvons le déterminer.

⚠️ **Note :**  
Ce ne sont pas des systèmes open source. Nous ne connaissons pas leurs détails internes exacts.  
Ce qui suit est une simplification éclairée basée sur leur comportement externe — juste assez pour comprendre comment la stack agentique peut se manifester en pratique.

---

## **NotebookLM (Google) : Recherche agentique sur vos propres données**

NotebookLM de Google fonctionne comme un assistant de recherche personnel. Vous téléchargez vos fichiers et il vous aide à travailler avec eux — en résumant, répondant aux questions, ou générant des versions audio ou des guides d'étude.

**Focus principal :** Questions-réponses sur votre contenu — essentiellement un système RAG personnel à grande échelle.

**Comment ça fonctionne probablement :**
1. **L'utilisateur télécharge des fichiers** (PDFs, notes, diapositives, etc.)
2. **Prétraitement** — Les stocke pour la récupération ultérieure.
3. **L'utilisateur pose une question** — ex. : _« Quels étaient les points clés de mon deck stratégique T2 ? »_
4. **Planification** — Interprète le type de tâche (résumé, Q&R, comparaison ?), identifie les documents/sections pertinents.
5. **RAG** — Récupère les extraits de documents les plus pertinents.
6. **Génération LLM** — Répond clairement, ancré dans votre contenu.
7. **Mémoire** —
   - Court terme : Suit la conversation.
   - Long terme : Probablement minimal ou inexistant.
8. **Outils** — Possiblement des visionneuses de fichiers, des modules de synthèse.

**Ce qui le rend agentique :** Interprète les objectifs, recherche dans vos données et compose des réponses — pas de simples sorties statiques.

---

## **Perplexity : Recherche agentique sur le web ouvert**

Perplexity vous donne une réponse directe avec des sources — plutôt qu'une page de liens.

**Comment ça fonctionne probablement :**
1. **L'utilisateur pose une question** — ex. : _« Quelles sont les dernières recherches sur les traitements de la maladie d'Alzheimer ? »_
2. **Planification** — Interprète l'intention (« dernières », « crédibles »), décide de l'approche de recherche.
3. **Utilisation d'outils** — Émet des requêtes via des API web.
4. **RAG** — Récupère des extraits de pages pertinents.
5. **Réponse LLM** — Synthétise une réponse avec des citations.
6. **Mémoire** —
   - Court terme : Contexte de session.
   - Long terme : Peut stocker des préférences (ex. : « toujours utiliser WSJ pour les actualités »).

**Ce qui le rend agentique :** Récupère des informations, décide quoi utiliser et construit une réponse dans une boucle en plusieurs étapes.

---

## **DeepResearch (OpenAI) : Flux de travail agentiques approfondis**

DeepResearch s'attaque à des **tâches de recherche ouvertes et complexes** — ex. : analyses de marché, cartographies concurrentielles, approfondissements techniques.

**Comment ça fonctionne probablement :**
1. **L'utilisateur soumet une tâche large** — ex. : _« Analysez le paysage de l'IA générative pour les startups de l'éducation. »_
2. **Planification** — Décompose en sous-tâches (financement, tendances, entreprises, risques), forme un plan d'exécution.
3. **Outils** — Inclut probablement :
   - Recherche web
   - Lecteurs de documents (PDFs)
   - Outils de données (tableurs, graphiques)
   - Modules de génération de rapports
4. **RAG Agentique** — Pas de récupération en une seule passe — récupère, réfléchit, récupère à nouveau selon l'évolution de la tâche.
5. **Mémoire** —
   - Épisodique : Suit quelles parties sont terminées.
   - Sémantique : Stocke les faits/noms clés.
6. **Raisonnement en plusieurs étapes** — Boucles : planifier → récupérer → lire → repenser → générer → affiner → répéter.

**Ce qui le rend agentique :** Planification intensive, utilisation itérative des outils, progression auto-dirigée.

---

## **Retour sur la Partie 2 : Niveaux d'autonomie**
<img width="694" height="370" alt="image" src="https://github.com/user-attachments/assets/48812496-309d-42cd-9c86-8ef3cb345ec2" />
<img width="969" height="231" alt="image" src="https://github.com/user-attachments/assets/12489209-a75b-4a31-853e-33dda02e1aaa" />


**NotebookLM** — Entre le Niveau 2 et le Niveau 3.
- Agent à flux de travail à contrôle élevé.
- Récupération forte, prise de décision autonome limitée.

**Perplexity** — Niveau 3 (frôlant peut-être le Niveau 4).
- Planifie les requêtes, organise les sources, élabore des réponses.

**DeepResearch** — Niveau 4 prononcé.
- Prend des objectifs de haut niveau, décompose les tâches, travaille de façon itérative avec une guidance minimale.

---

## Essayez par vous-même

Ils ont tous des versions gratuites — expérimentez et observez :
- Quel niveau de **contrôle** vous avez
- Combien le **système décide** par lui-même

C'est un excellent moyen d'affiner votre instinct pour la conception d'agents.

---

## À suivre

Dans la prochaine partie, nous conclurons la série :
- Résumer ce que nous avons appris
- Partager les bonnes pratiques
- Jeter un coup d'œil rapide sur l'avenir de l'**IA agentique**
