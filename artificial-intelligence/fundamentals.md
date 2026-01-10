---
title: Les Fondamentaux
description: 
published: true
date: 2026-01-10T21:55:33.268Z
tags: 
editor: markdown
dateCreated: 2025-12-27T12:34:46.295Z
---

# Les Fondamentaux

> 🎯 **Objectifs de ce chapitre**
> 
> À la fin de ce chapitre, tu seras capable de :
> - Comprendre ce qu'est réellement l'IA (et ce qu'elle n'est pas !)
> - Différencier IA, Machine Learning et Deep Learning
> - Expliquer comment fonctionne un LLM comme ChatGPT à tes collègues
> - Retracer les grandes étapes de l'histoire de l'IA
> - Choisir le bon modèle pour tes projets
   
![ai-ml-ds.png](/ai_ml/ai-ml-ds.png "Infographie par Jen Looper de Microsoft"){.align-center}
   
Tu as sûrement entendu parler d'Intelligence Artificielle partout ces derniers temps. À la télé, sur les réseaux sociaux, au bureau... Tout le monde en parle, mais combien de personnes savent vraiment ce que c'est ?

   Bonne nouvelle : à la fin de ce cours, **toi**, tu sauras. Et tu pourras même l'expliquer à ta grand-mère (enfin, si elle est curieuse 😄).


## Qu'est ce que l'IA ?


> Imaginons que tu veuilles créer un robot qui range ta chambre. Tu pourrais écrire des milliers de lignes de code pour chaque situation possible : "si chaussette par terre, alors ramasser et mettre dans panier". Fastidieux, non ?
> 
>    L'**Intelligence Artificielle**, c'est justement l'idée de créer des programmes capables de **s'adapter** et de **résoudre des problèmes** sans qu'on ait besoin de tout leur expliquer dans les moindres détails.
{.is-info}


> 💡 **Définition simple**
> L'Intelligence Artificielle (IA), c'est la capacité d'une machine ou d'un programme à imiter l'intelligence humaine pour réaliser des tâches complexes.
{.is-success}


>  En gros, au lieu de dire à l'ordinateur exactement quoi faire dans chaque cas, on lui donne les moyens d'**apprendre** et de **s'adapter**. C'est un changement de philosophie radical !
{.is-info}


## Qu'est ce que le Machine Learning ?

> OK, l'IA c'est bien joli, mais concrètement, comment on fait pour qu'une machine "apprenne" ?
> 
>    C'est là qu'entre en scène le **Machine Learning** (ou Apprentissage Automatique en bon français).
{.is-info}


> 💡 **Définition simple**
> Le **"Machine Learning"** (Apprentissage Automatique) est un sous-domaine de l'IA où la machine apprend à résoudre des tâches en analysant des données, plutôt qu'en suivant des règles dictées ligne par ligne par un développeur.
{.is-success}

### Une analogie pour bien comprendre

   Imagine que tu veuilles apprendre à un enfant à reconnaître un chat. Tu as deux options :

   **Option 1 : La méthode classique (programmation traditionnelle)**
   Tu lui donnes une liste de règles :
   - "Un chat a 4 pattes"
   - "Un chat a des moustaches"
   - "Un chat fait miaou"
   - "Un chat a une queue"
   - ...

   Le problème ? Un chien aussi a 4 pattes et une queue. Et certains chats n'ont pas de queue (comme le Manx). Ta liste de règles va vite devenir un cauchemar à maintenir !

   **Option 2 : La méthode Machine Learning**
   Tu montres à l'enfant des **milliers de photos de chats** en lui disant "ça, c'est un chat". À force, son cerveau va naturellement repérer les patterns qui font qu'un chat est un chat.

   Le Machine Learning, c'est exactement ça : on montre des **tonnes d'exemples** à la machine, et elle apprend toute seule à reconnaître les patterns.

   > ℹ️ **Bon à savoir**
   > 
   > Le Machine Learning nécessite beaucoup de données pour fonctionner. C'est pour ça qu'on parle souvent de "Big Data" dans le même souffle. Plus tu as de données de qualité, meilleur sera ton modèle !

## Qu'est ce que le Deep Learning ?

> 💡 **Définition simple**
> Le **Deep Learning** (Apprentissage Profond) est une sous-catégorie du Machine Learning qui s'inspire de la structure du cerveau humain. Il utilise des "réseaux de neurones artificiels" composés de nombreuses couches superposées pour apprendre des données très complexes (images, son, texte).
{.is-success}

### Pourquoi "Deep" (Profond) ?

   Le mot "profond" fait référence au nombre de **couches** dans le réseau de neurones. Plus il y a de couches, plus le réseau est "profond", et plus il peut apprendre des choses complexes.

   Pense à une usine avec plusieurs étages :
   - **Étage 1** : On détecte des formes simples (lignes, courbes)
   - **Étage 2** : On combine ces formes en motifs (yeux, oreilles)
   - **Étage 3** : On assemble les motifs en concepts (visage de chat)
   - **Étage 4** : On reconnaît l'objet final ("C'est Félix le chat !")

   Chaque couche apprend quelque chose de plus abstrait que la précédente. C'est cette profondeur qui permet au Deep Learning de comprendre des choses aussi complexes que le langage humain ou la reconnaissance faciale.


## Qu'est ce qu'un LLM ?

   Maintenant qu'on a posé les bases, parlons de ce qui fait le buzz : les **LLM** (Large Language Models, ou Grands Modèles de Langage).

   ChatGPT, Claude, Gemini, Mistral... Tous ces assistants IA que tu utilises peut-être déjà sont des LLM.

> 💡 **Définition simple**
> Un **LLM** (Large Language Model) est un modèle de langage capable de générer du texte à partir d'un prompt donné. Il est basé sur du Deep Learning et entraîné sur une immense partie d'Internet, avec pour objectif principal de prédire le mot suivant le plus probable dans une phrase.
{.is-success}

### Attends... "Prédire le mot suivant" ? C'est tout ?

Eh oui ! Aussi impressionnants qu'ils paraissent, les LLM sont fondamentalement des **machines à prédire le mot suivant**. C'est leur seule mission dans la vie.

Mais attention, ne sous-estime pas cette tâche apparemment simple. Pour prédire correctement le mot suivant, le modèle doit comprendre :
   - La grammaire
   - Le contexte
   - Les concepts
   - Les relations logiques
   - Et bien plus encore...


### Comment ça marche concrètement ?
![ai.fundamentals.token-guessing.jpg](/ai_ml/ai.fundamentals.token-guessing.jpg){.align-center}




![ai.fundamentals.tokenization.jpg](/ai_ml/ai.fundamentals.tokenization.jpg){.align-center}

> Le Modèle ne voit pas vraiment des "mots". Il voit des séquences de **tokens** (des morceaux de mots). Mais pour simplifier, restons avec les mots.
{.is-success}


Prenons l'exemple du Prompt : 
> Le chat mange → [Le], [chat], [mange]

Le modèle calcule les probabilités du mot suivant (Token) :
   | Mot suivant | Probabilité |
   |-------------|-------------|
   | des croquettes | 42% ✅ |
   | une souris | 25% |
   | du poisson | 15% |
   | sa pâtée | 10% |
   | une pizza | 0.01% 🍕 |

Le modèle choisit généralement le mot le plus probable ("des croquettes"). Et ensuite ? Il recommence ! Il prend "Le chat mange des croquettes" et prédit le mot suivant. Et ainsi de suite... c'est ce que l'on appelle l'**Auto-régression**.

> ⚠️ **Attention !**
> 
> Un LLM est une **machine statistique**, pas une encyclopédie. Il cherche le "probable", pas le "vrai". C'est pour ça qu'il peut parfois inventer des informations avec un aplomb déconcertant !
> 
> Ce phénomène s'appelle l'**hallucination**. Le modèle ne "sait" pas qu'il dit des bêtises. Il génère simplement la suite de texte la plus probable selon ses calculs. Si cette suite probable est fausse... tant pis pour lui (et pour toi si tu ne vérifies pas) !
{.is-warning}

>  Tu as peut-être entendu parler de la **température** dans le contexte des LLM. C'est un paramètre qui contrôle le niveau de "prise de risque" du modèle.

   | Température | Comportement |
   |-------------|--------------|
   | **0** (basse) | Le modèle choisit toujours le mot le plus probable. Réponses prévisibles et "sûres". |
   | **0.7-0.8** (moyenne) | Un bon équilibre entre créativité et cohérence. |
   | **1.0+** (haute) | Le modèle prend des risques, peut choisir des mots moins probables. Plus créatif, mais aussi plus susceptible de partir dans tous les sens ! |

Pour reprendre notre exemple du chat :
- Si la température est à 0, l'IA choisira toujours "des croquettes" (le plus probable).
- Si la température est élevée (ex: 0.8), l'IA prendra des risques et pourra choisir "sa pâtée" ou même "le canapé" pour être plus créative.


    
## Histoire de l'IA

> L'IA n'est pas née avec ChatGPT en 2022. Son histoire remonte à plus de 70 ans, avec des hauts spectaculaires et des bas tout aussi impressionnants.
{.is-info}


![ai.history_1.png](/ai_ml/ai.history_1.png)
![ai.history_2.png](/ai_ml/ai.history_2.png)

### 1950 : Des machines qui pensent

Tout commence avec un génie britannique : **Alan Turing**.
> 
> 💡 **Qui est Alan Turing ?**
> 
> Élu scientifique du 20ème siècle en 2019, Alan Turing est considéré comme le père de l'IA et de l'informatique théorique. Il a formalisé le concept d'algorithme avec sa "Machine de Turing" (1936) et joué un rôle crucial dans le décryptage de la machine Enigma pendant la Seconde Guerre Mondiale.
{.is-success}


> En 1950, Turing publie un article fondateur où il pose une question révolutionnaire : **"Les machines peuvent-elles penser ?"**
> 
> Pour y répondre, il propose le fameux **Test de Turing** (aussi appelé "Jeu de l'imitation") :
> 
>    1. Un humain discute par écrit avec deux interlocuteurs cachés
>    2. L'un est un humain, l'autre une machine
>    3. Si l'humain n'arrive pas à distinguer la machine de l'humain, alors la machine "pense"
> 
> Ce test reste aujourd'hui une référence, même si on sait qu'il a ses limites !
{.is-info}


Source : Test de turing


### 1956 : La Conférence de Dartmouth

L'été 1956 marque un tournant historique. À la **Conférence de Dartmouth**, quatre pionniers (dont John McCarthy et Marvin Minsky) inventent officiellement le terme **"Intelligence Artificielle"**.

   Leur hypothèse de départ était audacieuse :

   > *"Tout aspect de l'apprentissage ou de l'intelligence peut être décrit si précisément qu'une machine peut le simuler."*



### 1956 - 1974 : "Les années dorées"

C'est l'euphorie ! Les financements (notamment gouvernementaux) pleuvent, l'optimisme est à son comble. En 1967, Marvin Minsky déclare même :

> *"Dans une génération... le problème de la création de l'intelligence artificielle sera substantiellement résolu."*

> **Spoiler alert :** il se trompait.
{.is-danger}

Les chercheurs se concentrent sur des "micro-mondes" : des environnements simplifiés où l'IA peut raisonner sans la complexité du monde réel. C'est l'essor des premiers algorithmes de résolution de problèmes et du Traitement du Langage Naturel (NLP). Trois projets marquent cette époque :
   
   
  
#### ELIZA (1966) - Le premier chatbot

![ai.eliza.png](/ai_ml/ai.eliza.png){.align-center}

> ELIZA simulait un psychothérapeute en reformulant simplement les phrases de l'utilisateur. Malgré sa simplicité, les gens étaient bluffés et se confiaient à "elle" !

#### SHRDLU et le Blocks World

![ai.blocks_world.jpg](/ai_ml/ai.blocks_world.jpg){.align-center}

> Un programme capable de manipuler des blocs virtuels en comprenant des ordres en langage naturel. "Pose le cube rouge sur le bloc bleu" ? Pas de problème !

#### Shakey le robot (1972)

![ai.shakey_robot.jpg](/ai_ml/ai.shakey_robot.jpg){.align-center}

> Le premier robot mobile capable de percevoir son environnement et de planifier ses déplacements. Un ancêtre des robots aspirateurs d'aujourd'hui !


### 1974 - 1980 : "Hiver de l'IA" - La désillusion

Après l'euphorie, la douche froide. Les financeurs réalisent que les promesses étaient... comment dire... un peu exagérées.

   Le **Rapport Lighthill** (1973) assène le coup de grâce en Grande-Bretagne : les fonds sont coupés.

   **Pourquoi cet échec ?**

   Trois murs techniques ont stoppé net les recherches :

   1. **Puissance de calcul insuffisante** : Les ordinateurs de l'époque étaient tout simplement trop faibles pour les ambitions de l'IA.

   2. **L'explosion combinatoire** : Résoudre un problème simple, OK. Mais dès qu'on augmente la complexité, le temps de calcul explose de façon exponentielle. Impossible à gérer !

   3. **Manque de données** : Pas de Big Data à l'époque. Comment apprendre sans exemples ?

   En 1980, le philosophe **John Searle** enfonce le clou avec son expérience de pensée de la **"Chambre Chinoise"** : il démontre qu'une machine peut donner les bonnes réponses sans rien comprendre à ce qu'elle dit. Elle maîtrise la **syntaxe** mais pas la **sémantique**.

   > ℹ️ **L'expérience de la Chambre Chinoise**
   > 
   > Imagine-toi enfermé dans une pièce avec un livre de règles. Des Chinois te passent des questions en chinois sous la porte. Tu suis les règles du livre pour écrire des réponses en chinois. De l'extérieur, tu sembles parler chinois... mais tu n'as rien compris ! Tu manipules des symboles sans en saisir le sens.


### Années 1980 : L'ère des Systèmes Experts 


> L'IA sort des laboratoires (on parle d'IA symbolique) pour entrer dans les entreprises. C'est la première grande réussite commerciale de la discipline grâce aux Systèmes Experts. Ces logiciels visent à reproduire le raisonnement d'un spécialiste humain (un médecin, un garagiste).
> 
> Leur fonctionnement est simple et repose sur deux piliers :
>
> - La Base de règles (Le Savoir) : Une liste immense d'instructions de type "Si... Alors..." (Ex: Si le moteur chauffe, alors vérifier le radiateur).
>
> - Le Moteur d'inférence (La Logique) : Le logiciel qui parcourt ces règles pour trouver la solution à un problème donné.
>
> Note : En parallèle, la recherche sur les réseaux de neurones (Deep Learning) commence discrètement à renaître.
{.is-success}


### 1987 - 1993 : Le deuxième "Hiver de l'IA" (La chute du Hardware)


> La bulle des Systèmes Experts éclate. Le problème ? Ces logiciels tournaient sur des ordinateurs ultra-coûteux et spécialisés (les "Lisp Machines").
> 
> Soudain, les PC et les Mac deviennent assez puissants... et beaucoup moins chers. Pourquoi investir des fortunes dans du matériel spécialisé ?
> 
> Nouvel hiver budgétaire. Mais cette fois, quelque chose de crucial se met en place : la **démocratisation des ordinateurs personnels**. Des millions de machines vont bientôt générer des tonnes de données...
{.is-success}


### 1993 - 2011 : Le triomphe de la Data (L'IA probabiliste)


Trois facteurs vont relancer la machine :

   **1. La Loi de Moore**
   La puissance de calcul double tous les 18 mois environ. Ce qui était impossible hier devient trivial demain.

   **2. Le Big Data**
   Internet explose. Le smartphone arrive (2007). Soudain, on génère des **quantités astronomiques de données**.

   **3. L'apprentissage statistique**
   Changement de philosophie : on arrête d'essayer de coder des règles parfaites. On laisse les algorithmes **apprendre des probabilités** à partir des données.

   L'IA devient enfin une discipline scientifique mature et rigoureuse.


### Aujourd'hui : L'Ère de l'Ubiquité et de l'Éthique

L'IA est partout. Dans ton téléphone, tes réseaux sociaux, ta banque, ta voiture...

La question n'est plus "Est-ce que ça marche ?" mais **"Est-ce que c'est juste ?"**

   > ⚠️ **Les nouveaux défis**
   > 
   > - **Biais algorithmiques** : Une IA entraînée sur des données biaisées reproduit ces biais
   > - **Protection de la vie privée** : Qui a accès à tes données ?
   > - **Manipulation de l'opinion** : Fake news, deepfakes...
   > - **Impact environnemental** : Entraîner un gros modèle consomme énormément d'énergie

Comme le dit Brad Smith de Microsoft : la technologie touche désormais aux droits humains fondamentaux. L'enjeu actuel est la **régulation** et la création d'une **IA éthique et explicable**.

## Quickstart : L'IA en action


**Objectif** : Observer comment l'IA se "perçoit" et tester sa capacité à structurer une réponse complexe.

**Consigne** : Rends-toi sur une IA de ton choix (ChatGPT, Claude, Mistral, Gemini...) et entre le prompt suivant :

```text
Agis comme un formateur en IA expliquant les LLM à un apprenant curieux. Structure ta réponse en 4 couches :  
1. **Auto-description littérale** : "Je suis un Grand Modèle de Langage (LLM), ce qui signifie..."  
2. **Analogie** : Compare un LLM à une « **poupée russe de savoir humain compressé** » (explique les symboles : couches de la poupée = couches du modèle, compression = entraînement).  
3. **Auto-dissection** : Décris le *processus de génération* de *cette phrase même* :  
   - Tokenisation → Embeddings → Attention → Prédiction → Décodage  
4. **Métacognition** : "Pourquoi cette explication en couches fonctionne-t-elle ? Parce que les LLM apprennent le savoir *hiérarchiquement* – reflétant la manière dont je viens de vous l'enseigner."  
```

> 💡 **Analyse tes résultats**
> 
> Compare les réponses de différentes IA. Tu remarqueras qu'elles sont capables de "métacognition simulée" (expliquer leur propre fonctionnement). C'est une excellente démonstration de leurs capacités de synthèse !
> 
> Mais rappelle-toi : elles ne "comprennent" pas vraiment. Elles génèrent la suite de texte la plus probable. Nuance importante !
{.is-warning}



## Sous le capot : Les progrès techniques

Les LLM sont de plus en plus performants. Ce n'est pas de la magie, mais une convergence de plusieurs avancées mathématiques et techniques.

> Le rapport de Stanford sur l'IA (2025) détaille ces avancées : [https://hai.stanford.edu/ai-index/2025-ai-index-report/technical-performance](https://hai.stanford.edu/ai-index/2025-ai-index-report/technical-performance)

### 1. La vectorisation du langages (Embeddings) (Word2Vec et al.)


Premier défi : comment faire comprendre le langage humain à une machine qui ne comprend que des chiffres ?

La réponse : Les mathématiques, **transformer les mots en vecteurs** (des listes de nombres).

![Word2Vec général](/ai_ml/ai.fundamentals.word2vec.general.png){.align-center}


Grâce à des techniques comme **Word2Vec**, chaque mot devient un point dans un espace mathématique à plusieurs dimensions.

![Vecteurs Word2Vec](/ai_ml/ai.fundamentals.word2vec.vectors.jpg){.align-center}


>  **Pourquoi c'est génial ?**
> 
>    Dans cet espace, les mots qui ont des sens proches sont... géographiquement proches ! On peut calculer des "distances" entre les mots :
> 
>    - "Roi" est proche de "Reine"
>    - "Paris" est à "France" ce que "Rome" est à "Italie"
> 
>    On peut même faire des "calculs" avec les mots :
>    ```
>   Roi - Homme + Femme ≈ Reine
>   ```
{.is-info}

> 💡 **À retenir**
> 
> Pour l'IA, le sens d'un mot est défini par sa **position** dans cet espace mathématique. Le modèle n'apprend pas juste des mots, il **cartographie des concepts**.
{.is-info}



### 2. Les réseaux neuronaux profonds (Deep Learning)

Une fois les mots transformés en chiffres, ils passent dans le "cerveau" du modèle : un **réseau de neurones artificiels**. On parle d'IA "Connexionistes".

![Taille des réseaux de neurones](/ai_ml/ai.fundamentals.nn-size.png)
*La taille des réseaux a explosé ces dernières années !*

   Chaque neurone fait deux choses :
   1. Une **transformation affine** (transformation mathématique) des entrées (combinaison linéaire pondérée)
   2. Une **fonction d'activation** qui introduit de la non-linéarité (comme ReLU ou Sigmoïde)

   C'est cette non-linéarité qui permet d'apprendre des choses complexes. Sans elle, empiler des couches ne servirait à rien !

   > ℹ️ **Pourquoi "profond" ?**
   > 
   > Plus le réseau a de couches (= plus il est "profond"), plus il peut comprendre des concepts abstraits. Les premières couches détectent des patterns simples, les dernières comprennent des notions complexes comme l'ironie ou le raisonnement logique.


### 3. L'attention et les Transformers (La révolution de 2017)

> En 2017, une équipe de Google publie un article au titre évocateur : **"Attention Is All You Need"** (L'attention, c'est tout ce qu'il vous faut).
> 
>    C'est LA révolution qui a rendu les LLM modernes possibles.
{.is-success}


   ![Schéma LLM](/ai_ml/ai.fundamentals.llm-schema.png)

>    **Le problème des anciennes approches**
> 
>    Avant les Transformers, les modèles traitaient le texte mot par mot, dans l'ordre. Pour une longue phrase, le modèle "oubliait" le début quand il arrivait à la fin.
{.is-info}


>    **La solution : le mécanisme d'Attention**
> 
>    L'Attention permet au modèle de regarder **tous les mots en même temps** et de décider lesquels sont importants pour comprendre chaque partie.
> 
>    Prenons un exemple :
> 
>    > *"L'animal n'a pas traversé la rue car **il** était trop fatigué."*
> 
>    - Pour un humain, "il" désigne clairement "l'animal"
>    - Pour une ancienne IA, c'était ambigu : la rue ? l'animal ?
>    - Grâce à l'Attention, le modèle connecte fortement "il" à "animal" et faiblement à "rue"
> 
>    C'est ce mécanisme qui permet de générer des textes longs et cohérents !
{.is-success}


### 4. Le renforcement par l'humain / Reinforcement Learning from Human Feedback (RLHF)

 À ce stade, le modèle a été entraîné sur tout Internet. Il sait parler, mais... il peut être impoli, raconter n'importe quoi, ou donner des conseils dangereux.

   Il faut l'**éduquer**. C'est le rôle du **RLHF** (Reinforcement Learning from Human Feedback).

   ![Fine-tuning avec RLHF](/ai_ml/ai.fundamentals.fine-tuning-llm-with-rlhf.png)

   **Comment ça marche ?**

   1. Le modèle génère plusieurs réponses possibles
   2. Des humains classent ces réponses (de la meilleure à la pire)
   3. Le modèle ajuste ses paramètres pour maximiser la "récompense" (la satisfaction humaine)

   C'est cette étape qui transforme un simple "compléteur de texte" en un **assistant conversationnel utile** comme ChatGPT ou Claude.

> 💡 **C'est l'alignement !**
> 
> Le RLHF "aligne" le comportement du modèle sur les valeurs humaines. Sans cette étape, le modèle pourrait générer du contenu offensant ou dangereux.
{.is-warning}




## Panorama actuel des modèles (Juin 2025)

   ![Benchmark LLM Juin 2025](/ai_ml/ai.llm.benchmark.2025-06-04.png)


## Quelques modèles et entreprises du LLM

![ai-llm-benchmark-202501.png](/ai_ml/ai-llm-benchmark-202501.png)

En janvier 2025 :

 | Modèle                  | Entreprise | Type           |
   | ----------------------- | ---------- | -------------- |
   | **DeepSeek**            | DeepSeek   | Open Source 🔓  |
   | **ChatGPT (GPT-4, o1)** | OpenAI     | Propriétaire 🔒 |
   | **Llama**               | Meta       | Open Source 🔓  |
   | **Claude**              | Anthropic  | Propriétaire 🔒 |
   | **Qwen**                | Alibaba    | Open Weight 🔓  |
   | **Codestral**           | Mistral    | Open Source 🔓  |
   | **Gemini**              | Google     | Propriétaire 🔒 |
   | **Gemma**               | Google     | Open Weight 🔓  |

### Où suivre les benchmarks ?

   Les performances des modèles évoluent très vite ! Voici quelques ressources pour rester à jour :

   - [Vellum LLM Leaderboard](https://www.vellum.ai/llm-leaderboard)
   - [Artificial Analysis](https://artificialanalysis.ai/leaderboards/models)
   - [BigCode Bench](https://bigcode-bench.github.io/)
   - [LLM Stats](https://llm-stats.com/)
   - [Aider Leaderboards](https://aider.chat/docs/leaderboards/) (pour le code)


## Comment choisir son modèle ? 🤔

   Face à cette jungle de modèles, comment faire le bon choix ? Voici les critères à considérer :

### Les critères essentiels

   | Critère              | Questions à se poser                                               |
   | -------------------- | ------------------------------------------------------------------ |
   | **Efficacité**       | Le modèle est-il bon pour MA tâche ? (code, rédaction, analyse...) |
   | **Coûts**            | Quel est le prix par token ? Mon budget le permet-il ?             |
   | **Open Source**      | Ai-je besoin d'accéder au code ? De le modifier ?                  |
   | **Exécution locale** | Puis-je le faire tourner sur mes serveurs ?                        |
   | **Taille**           | Ai-je le matériel pour faire tourner un gros modèle ?              |
   | **Confidentialité**  | Mes données sont-elles sensibles ?                                 |
   | **Sécurité**         | Le modèle a-t-il des garde-fous suffisants ?                       |
   | **Performance**      | Vitesse de réponse acceptable ?                                    |

 ## QCM : Teste tes connaissances ! 🧠

   **Question 1** : Quelle est la mission principale d'un LLM ?
   - A) Stocker des connaissances comme une encyclopédie
   - B) Prédire le mot suivant le plus probable
   - C) Comprendre le sens profond des textes
   - D) Remplacer les humains

   **Question 2** : Qu'est-ce que l'hallucination dans le contexte des LLM ?
   - A) Un bug logiciel
   - B) Le fait de générer des informations fausses avec assurance
   - C) Un problème de connexion internet
   - D) Une fonctionnalité désactivée

   **Question 3** : Que permet le mécanisme d'Attention ?
   - A) De rendre l'IA plus polie
   - B) De traiter tous les mots d'une phrase simultanément
   - C) D'accélérer les calculs
   - D) De réduire la consommation électrique

   **Question 4** : À quoi sert le RLHF ?
   - A) À rendre le modèle plus rapide
   - B) À aligner le comportement du modèle sur les attentes humaines
   - C) À réduire la taille du modèle
   - D) À traduire le modèle en français

   <details>
   <summary>📖 Voir les réponses</summary>

   1. **B** - Prédire le mot suivant le plus probable
   2. **B** - Le fait de générer des informations fausses avec assurance
   3. **B** - De traiter tous les mots d'une phrase simultanément
   4. **B** - À aligner le comportement du modèle sur les attentes humaines

   </details>


<!--
### Les interfaces

**Les modèles LLM sont disponibles sous forme de services API ou d'interfaces qui exploitent ces API.**

Si on prend l'exemple de Claude par Anthropic.

- Chat Web : [https://claude.ai/](https://claude.ai/) est un chatbot qui permet de tester Claude en ligne.
- API : [https://docs.anthropic.com/en/api/overview](https://docs.anthropic.com/en/api/overview) est la documentation de l'API Claude.
- SDK : [https://github.com/anthropics/claude-code-sdk-python](https://github.com/anthropics/claude-code-sdk-python) est un client Python pour l'API Claude.

Aujourd'hui, les modèles LLM sont intégrables directement dans les applications, comme le font les IDE.

* * *

**Aujourd'hui on voit émerger une variété de solutions et d'interfaces.**

**A terme on aura de plus en plus d'architectures qui intègreront l'AI en tant que service.**

- Endpoint d'inférence : Code (autocomplétion) et Chat (questions / réponses)
- Interface web
- Intégration IDE
- Intégration CLI
- Interfaces agentique
- Application IA

**En l'état, toutes ces solutions utiliseront au final un prompt pour obtenir une réponse d'un modèle de langage.**

-->