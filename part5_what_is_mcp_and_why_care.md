# Partie 5 : C'est quoi le MCP et pourquoi s'y intéresser ?

---

## D'abord, un rapide récapitulatif

- **Partie 3 :** Nous avons appris que les outils permettent aux modèles de **faire des choses**.
- **Partie 4 :** Nous avons vu que le RAG aide les modèles à **trouver des informations pertinentes** avant de répondre.

Ce sont des **supports externes** — ils aident le modèle à agir plus intelligemment, mais la coordination reste en dehors du modèle.

Mais que se passerait-il si vous pouviez fournir **tout le contexte dont un modèle a besoin** — outils, données récupérées, mémoire, instructions — dans un format propre et structuré ?

C'est ce que le **Model Context Protocol (MCP)** cherche à résoudre.

---

## Alors, c'est quoi le MCP ?
<img width="737" height="452" alt="image" src="https://github.com/user-attachments/assets/2e17fcb6-ab35-4a4c-88b4-c74db165e4b8" />


Dans son essence, le **Model Context Protocol** est une façon standardisée de fournir à un LLM tout ce dont il a besoin pour raisonner et répondre.

Imaginez que vous embaliez :

- La tâche que vous souhaitez que le modèle accomplisse
- Les outils/API qu'il peut utiliser
- Les documents ou la mémoire dont il pourrait avoir besoin
- Les messages précédents de la conversation

…pour ensuite tout remettre d'un seul coup.

Ce **n'est pas** un outil, une bibliothèque ou un produit.  
C'est un **protocole** — une structure de communication entre le modèle et le monde extérieur.

Si vous êtes du monde tech, les équivalents seraient : **HTTP**, **TCP/IP** ou **SMTP**.  
Sinon, retenez simplement : les gens de la tech adorent la standardisation — elle facilite la réutilisation et l'interconnexion.

---

## Pourquoi est-ce important ?

Supposons que vous construisiez un agent.  
Vous jongiez probablement avec :

- L'envoi d'un prompt
- La transmission de documents récupérés
- L'enregistrement d'outils
- La gestion d'état
- Le suivi de ce qui s'est passé avant

MCP dit :
> « Standardisons la façon dont nous fournissons tout cela au modèle, pour ne pas réinventer la roue à chaque cas d'usage. »

Et pour les **entreprises**, c'est très important.  
À mesure que les agents deviennent plus complexes, coordonner **outils**, **RAG**, **mémoire** et **sorties** devient chaotique.

MCP rend cette orchestration **composable**, **modulaire** et plus facile à connecter à d'autres systèmes.

Si vous avez déjà travaillé avec des API, pensez au MCP comme un **schéma de requête bien défini**.  
Au lieu de tout mettre dans une longue chaîne de texte en espérant que le modèle s'y retrouve, le modèle voit toujours du texte — mais il est **structuré**, avec un **contexte, des options et des fondements clairs**.

---

## Pourquoi le MCP a-t-il été adopté si rapidement ?

Étant donné que le MCP n'est qu'un protocole, vous vous demandez peut-être :
> Ce qui le rend meilleur, et pourquoi tout le monde a-t-il sauté à bord ?

Voici ce qui a aidé :

1. **Natif IA** — Le MCP a été conçu pour les agents IA. Il fait de la place pour tout ce que les agents utilisent aujourd'hui : outils, prompts, mémoire, documents, et plus encore.
2. **Documentation et exemples solides** — Anthropic (créateurs du MCP) a publié non seulement la spécification, mais aussi des clients, des SDK, des outils de test et des démos réelles.
3. **Effet de réseau** — Publié discrètement en novembre 2024, la plupart des gens l'ont ignoré… jusqu'en 2025, où il a explosé. Des outils, des startups et même OpenAI ont commencé à le supporter.

---

## Idées reçues courantes

- **Le MCP n'est pas une nouvelle API ou un produit** — C'est juste un pattern, une façon propre de structurer ce qu'on envoie au modèle.
- **Il ne rend pas les modèles plus intelligents** — Il leur donne simplement un contexte meilleur et mieux structuré.
- **Il n'est pas réservé aux agents** — Même de simples assistants bénéficient d'une meilleure gestion du contexte.

---

## Alors… devriez-vous vous y intéresser ?

Si vous construisez des prompts de test ou des démos rapides — probablement pas (encore).

Mais si vous travaillez sur :

- Des agents de niveau entreprise
- Des flux de travail multi-outils
- Des LLM ayant besoin d'accéder à **mémoire + RAG + planification**
- Des systèmes où la **gestion du contexte** est un goulot d'étranglement

…alors **oui**, vous devriez vous y intéresser. Le MCP vise à mieux transmettre un contexte évolutif et structuré aux modèles.

Mais gardez à l'esprit : le MCP n'est qu'un protocole.  
Comme tous les standards, il ne fonctionne que s'il est largement adopté.  
Si quelque chose de mieux arrive avant que le MCP devienne « le HTTP des agents », l'écosystème pourrait changer à nouveau.

---

## Lectures et ressources complémentaires

- Nous avons publié un **[article complet](https://thenuancedperspective.substack.com/p/mcp-overhyped-misunderstood-and-actually)** sur le MCP, incluant clients, serveurs et cas d'usage réels (écrit par Kiriti Badam, OpenAI).
- Nous avons également organisé une **session live gratuite** — vous pouvez accéder à l'[enregistrement](https://maven.com/p/82345a) ici.

---

Dans la prochaine partie, nous découvrirons le composant de **planification** des systèmes agentiques et pourquoi il est crucial.

PS : Nous enseignons également un cours très apprécié sur la construction de systèmes IA dans cet environnement en rapide évolution, avec une approche orientée problème. Il est conçu pour les chefs de produit, les dirigeants, les ingénieurs, les décideurs, etc. travaillant dans des contraintes réelles. Les anciens élèves viennent de Google, Meta, Apple, Netflix, AWS, Spotify, Snapchat, Deloitte, et plus encore. Notre prochaine cohorte commence bientôt. Les tarifs early bird sont en ligne : utilisez le code « GITHUB » pour obtenir 300 $ de réduction (valable uniquement pour août 2025) pour [vous inscrire ici](https://maven.com/aishwarya-kiriti/genai-system-design) !!
