# Partie 4 : La Génération Augmentée par Récupération (RAG) et l'essor du RAG Agentique

Dans la partie précédente, nous avons vu comment les outils permettent aux agents IA d'interagir avec des systèmes réels — envoyer des e-mails, créer des tickets, déclencher des API.

Mais et si le modèle n'a pas besoin d'agir ?  
Et s'il a simplement besoin d'accéder aux bonnes informations ?

C'est souvent le cas dans les environnements d'entreprise :
- Des documents internes dispersés entre les équipes
- Des PDF de politiques que personne ne se rappelle avoir écrits
- Des insights clients enfouis dans les notes CRM
- Des tableaux de bord et e-mails contenant du contexte utile

Les outils n'aideront pas ici. Le modèle a besoin de raisonner avec vos données.  
C'est là qu'intervient le **RAG**.

---

## C'est quoi le RAG ?

RAG signifie **Retrieval-Augmented Generation** (Génération Augmentée par Récupération).  
C'est une architecture système où le modèle récupère des informations pertinentes depuis vos propres données — juste avant de générer une réponse.

Au lieu de s'appuyer uniquement sur ce pour quoi le modèle a été entraîné, le RAG lui donne accès à des **informations vivantes et contextuelles** provenant de vos systèmes d'entreprise. Cela rend les réponses plus précises, mieux fondées et auditables.

Vous vous demandez peut-être :
> « Pourquoi ne pas simplement donner toutes les données au modèle directement ? »

Le problème est que :
- Les modèles ne peuvent traiter qu'une quantité limitée de texte à la fois.
- Même dans cette limite, ils peinent quand trop d'informations non pertinentes ou bruyantes sont incluses.
- Cela rend les réponses moins ciblées et plus sujettes aux erreurs.

---

## Le processus RAG (en bref)

<img width="1024" height="356" alt="image" src="https://github.com/user-attachments/assets/2e7c2384-a564-45c1-9a08-57cfb02ee435" />


Voici à quoi ça ressemble en pratique :

1. **Données** – Votre contenu interne (PDFs, e-mails, notes, wikis)
2. **Découpage** – Décomposé en parties plus petites pour un meilleur indexage
3. **Prompt + Contexte** – Au moment de la requête, le système récupère les extraits pertinents (phase de récupération)
4. **LLM** – Le modèle utilise ce contexte pour générer une réponse
5. **Sortie** – Le résultat est basé sur vos données, pas seulement sur ce que le modèle « sait »

_Source de l'image : https://hyperight.com/7-practical-applications-of-rag-models-and-their-impact-on-society/_

---

## Pourquoi le RAG est omniprésent dans l'IA d'entreprise

Ce chiffre revient souvent :
> D'après ce que j'ai observé auprès de clients et de systèmes, **70 % des cas d'usage GenAI en entreprise utilisent le RAG**.

Pourquoi le RAG est indispensable aux entreprises :
- Les connaissances d'entreprise changent fréquemment
- Le fine-tuning des modèles est coûteux et lent
- La récupération est plus rapide, plus sûre et plus facile à contrôler
- Elle apporte structure et traçabilité dans les systèmes LLM
- Elle fonctionne sur des données non structurées (documents) et semi-structurées (tableaux de bord, notes)

Ainsi, au lieu de demander :
> « Comment apprendre au modèle tout ce que nous savons ? »  
La plupart des équipes demandent :
> « Comment permettre au modèle de récupérer ce que nous avons déjà ? »

---

## RAG = LLM + Données récupérées supplémentaires

Le RAG est devenu le pattern dominant en 2024 pour une bonne raison :  
il a comblé le fossé entre les LLM polyvalents et les connaissances d'entreprise privées et spécifiques aux tâches.

Dans son essence, le RAG est simple :
- Vous prenez un LLM
- Vous lui fournissez des informations supplémentaires récupérées juste avant la génération

Cela rend le modèle plus précis, plus conscient du contexte et moins dépendant des faits mémorisés.  
C'est particulièrement utile pour des tâches comme les **questions-réponses, la synthèse et la consultation de politiques** — notamment dans des environnements riches en données comme le **secteur juridique, la finance et le support**.

Pas étonnant que 2024 ait été surnommée **« l'année du RAG ».**

---

## Mais nous entrons maintenant dans l'ère agentique

Le RAG ne disparaît pas, mais il évolue.

Les systèmes actuels ne récupèrent plus une seule fois pour générer une réponse.  
Dans les **flux de travail agentiques**, la récupération fait partie d'une boucle de raisonnement plus large et dynamique.

Les agents planifient, récupèrent, réfléchissent et récupèrent à nouveau — pas une seule fois, mais autant de fois que nécessaire tout au long d'une tâche.

C'est là qu'intervient le **RAG Agentique**.

---

## C'est quoi le RAG Agentique ?

<img width="1456" height="971" alt="image" src="https://github.com/user-attachments/assets/8a7347b0-2ead-4d56-9f33-ef57667d0f00" />


RAG traditionnel :
- Une requête
- Une récupération
- Une réponse

Il fonctionne bien pour des questions isolées comme :
> « Quelle est notre politique sur le report des congés payés ? »

Mais la plupart des flux de travail réels en entreprise ne sont pas en une seule passe.

---

**Exemple :**  
Imaginons que vous développez un assistant de gestion des affaires pour votre équipe commerciale.  
Dans une seule tâche, l'agent peut avoir besoin de :
- Récupérer l'historique CRM du client
- Obtenir la tarification actuelle pour son segment
- Consulter les conditions légales régionales
- Référencer les clauses contractuelles passées
- Générer une proposition personnalisée
- Vérifier les faits
- Journaliser l'interaction

---

Dans les **systèmes agentiques**, la récupération n'est pas qu'une étape de configuration.  
C'est ainsi que l'agent :
- Rassemble le contexte manquant
- Vérifie ses hypothèses
- S'adapte en cours de tâche

Cela signifie que le RAG devient :
- Un outil d'apprentissage en cours de tâche
- Une méthode de réduction des hallucinations
- Un mécanisme pour gérer les flux de travail dynamiques
- Un pont entre le raisonnement et les connaissances d'entreprise fondées

Le RAG Agentique transforme la récupération en une **boucle de prise de décision de premier plan** en utilisant la récupération dans le processus de réflexion du modèle.

---

## Le RAG comme outil

Si vous y réfléchissez, le RAG est aussi une sorte d'**outil**.  
Mais au lieu de déclencher une action, il aide l'agent à extraire les bonnes informations d'un grand volume de données.

En pratique, les agents combinent souvent :
- **RAG**
- **Outils**
- **Planification**

…pour accomplir des tâches complexes **de façon fiable et contextuelle**.

---

## Note sur la portée

Le RAG est un espace profond et en rapide évolution — honnêtement, il pourrait faire l'objet de son propre cours.  
Si vous souhaitez explorer davantage :
- J'ai constitué un **dépôt GitHub** des articles clés sur le RAG qui couvre bien le paysage
- J'ai aussi un **guide 101 sur le RAG Agentique**

Cela dit, toutes les optimisations RAG ne sont pas nécessaires pour chaque cas d'usage.  
Dans notre cours de 6 semaines, nous nous concentrons sur vous aider à comprendre **quand et où** chaque technique est pertinente, plutôt que de les appliquer aveuglément.

---

Dans la prochaine partie, nous plongerons dans l'un des concepts les plus discutés récemment : le **Model Context Protocol (MCP)**.

Pour en tirer le meilleur parti, nous vous recommandons de relire la **Partie 3 sur les outils**, car le MCP s'appuie directement sur ce concept !
