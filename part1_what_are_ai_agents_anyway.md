# Partie 1 : C'est quoi les agents IA ?

Bonjour,

Ces jours-ci, tout le monde semble se précipiter pour « développer des agents », mais arrêtons-nous un instant.  
C'est quoi exactement un agent IA ? Et pourquoi le monde entier en est-il soudainement obsédé ?

À vrai dire, il n'existe pas de définition universellement acceptée.  
Mais voici une définition simple et utile pour notre propos :

> L'IA générative excelle dans la compréhension et la génération de contenu.  
> **L'IA agentique va plus loin — elle comprend, génère du contenu et effectue des actions.**

<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/3bf03a13-eb32-487f-9ddb-2c97919f1e80" />

---

## Un rapide retour en arrière

En 2022, ChatGPT a tout bouleversé car, pour la première fois, l'IA semblait conversationnelle.  
Pas besoin d'écrire du code ou d'entraîner des modèles — on pouvait simplement lui parler.

Comparons :
- **Programmation traditionnelle** → Nécessitait du code pour fonctionner
- **ML traditionnel** → Nécessitait de l'ingénierie de features
- **Deep learning** → Nécessitait un entraînement spécifique à chaque tâche
- **ChatGPT** → Pouvait raisonner sur diverses tâches et répondre sans entraînement préalable

C'est ce qu'on appelle l'**apprentissage zéro-shot** (sans exemples) ou l'**apprentissage en contexte** (comprend les tâches à partir des seules instructions).

---

## En 2024, les gens en voulaient davantage

Dialoguer avec l'IA, c'était bien — mais et si elle pouvait vraiment faire des choses ?

Par exemple :
- Au lieu de simplement vous donner une liste de prospects, pourrait-elle leur envoyer un e-mail ?
- Au lieu de résumer un document, pourrait-elle le classer dans le bon dossier et créer une tâche dans votre flux de travail ?
- Au lieu de suggérer un produit à un utilisateur, pourrait-elle personnaliser automatiquement la page d'atterrissage ?

C'est là qu'arrivent les **agents**.

---

## Comment les agents passent-ils à l'action ?

La magie réside dans les **outils**.

La plupart des agents sont couplés à des API, des appels de fonctions ou des plugins qui leur permettent d'interagir avec des systèmes externes.  
Le LLM ne se contente pas de répondre en texte — il produit des commandes structurées comme :
- `Appeler la fonction send_email() avec les paramètres suivants…`
- `Récupérer les enregistrements du CRM via cette requête…`
- `Planifier une réunion mardi à 14h…`

Cela fonctionne grâce à un mécanisme appelé **utilisation d'outils** (ou **function calling**).  
L'agent est informé des outils disponibles et détermine quand et comment les utiliser — soit directement, soit via un mécanisme de planification.

---

## Les agents plus avancés incluent :
- **La mémoire** → Pour se souvenir des étapes passées ou du contexte
- **Des modules de planification** → Pour décider quoi faire ensuite, notamment pour les tâches en plusieurs étapes
- **La gestion d'état** → Pour que l'agent puisse suivre sa progression et éviter les boucles ou les échecs

Pensez au LLM comme au **cerveau**, et aux outils comme aux **mains**.  
Sans outils, un agent ne fait que parler. Avec des outils, il agit.

<img width="1216" height="413" alt="image" src="https://github.com/user-attachments/assets/9cd7fa10-21a0-42a3-95fb-3bf081e10af1" />

---

## Deux façons de définir les agents

**Vue technique** → Agents = LLM + Outils + Planification + Mémoire (et les composants ci-dessus)  
**Vue métier** → Agents = Systèmes qui accomplissent des tâches de bout en bout

**Important :** Les agents d'aujourd'hui ne sont pas des innovations en IA.  
Ce sont des **enveloppes d'ingénierie** autour de modèles IA. L'intelligence sous-jacente provient toujours des modèles IA — l'agent aide simplement à mettre cette intelligence en action.

---

## Comment construire concrètement des applications IA agentiques

Voici où la plupart des gens se trompent :  
Ils commencent par « Construisons un agent ! » au lieu de « Quel problème réel cherchons-nous à résoudre ? »

Inversez la logique.  
Partez des **problèmes concrets en entreprise**, comme :
- Une équipe support noyée sous des requêtes répétitives
- Un analyste qui jongle entre différents tableaux de bord pour trouver des insights
- Une équipe commerciale qui saisit et suit manuellement les activités clients

Ce cours se concentre sur la construction d'agents qui fonctionnent dans le monde réel — pas seulement des démos.  
Bien sûr, vous pouvez créer rapidement des agents personnels ou des prototypes sans trop de structure, mais lorsque vous construisez pour l'entreprise, **les choix de conception comptent**.

---

## Un modèle mental utile : Autonomie vs. Contrôle

Une fois le problème identifié, la décision suivante est :  
**Quel degré d'autonomie accorder à votre agent ?**

Pensez-y comme un compromis :
- Quelle autonomie accordez-vous à l'agent
- contre
- Quel niveau de contrôle souhaitez-vous conserver côté humain

Ce n'est pas une décision universelle — c'est contextuel.  
Différents problèmes exigent différents niveaux d'implication de l'agent.

---

Dans la prochaine partie, nous approfondirons ce compromis autonomie-contrôle et verrons comment concevoir des agents en fonction du niveau d'autonomie que votre cas d'usage requiert réellement.
