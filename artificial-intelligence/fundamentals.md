---
title: Les Fondamentaux
description: 
published: true
date: 2026-01-10T20:35:24.464Z
tags: 
editor: markdown
dateCreated: 2025-12-27T12:34:46.295Z
---

# Les Fondamentaux


![ai-ml-ds.png](/ai_ml/ai-ml-ds.png "Infographie par Jen Looper de Microsoft"){.align-center}


## Qu'est ce que l'IA ?

> L'Intelligence Artificielle (IA), c'est la capacité d'une machine ou d'un programme à imiter l'intelligence humaine pour réaliser des tâches complexes.
{.is-success}

## Qu'est ce que le Machine Learning ?

> Le **"Machine Learning"** (Apprentissage Automatique) est un sous-domaine de l'IA où la machine apprend à résoudre des tâches en analysant des données, plutôt qu'en suivant des règles dictées ligne par ligne par un développeur.
{.is-success}

## Qu'est ce que le Deep Learning ?

> Le Deep Learning (Apprentissage Profond) est une sous-catégorie du Machine Learning qui s'inspire de la structure du cerveau humain. Il utilise des "réseaux de neurones artificiels" composés de nombreuses couches superposées pour apprendre des données très complexes (images, son, texte).
{.is-success}

## Qu'est ce qu'un LLM ?

> Un LLM (Large Language Model) est un modèle de langage capable de générer du texte à partir d'un prompt donné. Il est basé sur du Deep Learning et entraîné sur une immense partie d'Internet, avec pour objectif principal de prédire le mot suivant le plus probable dans une phrase.
{.is-success}


![ai.fundamentals.token-guessing.jpg](/ai_ml/ai.fundamentals.token-guessing.jpg){.align-center}
![ai.fundamentals.tokenization.jpg](/ai_ml/ai.fundamentals.tokenization.jpg){.align-center}

Il est important de comprendre qu'un modèle ne lit pas des mots à partir de votre prompt, mais des Tokens, ou en tout cas une séquence de Tokens (morceaux de mots). (Pour simplification et abus de langage, on parle effectivement de mots).

Prenons l'exemple du Prompt : 
> Le chat mange → [Le], [chat], [mange]

Le modèle calcule les probabilités du mot suivant (Token) :
- des croquettes (Probabilité : 42%) → Choix le plus prudent
- une souris (Probabilité : 25%)
- du poisson (Probabilité : 15%)
- sa pâtée (Probabilité : 10%)
- une pizza (Probabilité : 0.01%) → Peu probable, sauf contexte spécifique

Et peut donc générer une réponse avec une séquence de tokens qui correspond à une phrase cohérente en rapport avec le contexte (votre prompt).

Au fur et à mesure de la production du texte, le modèle réutilise le prompt et le texte déjà produit pour prédire le token suivant, c'est ce que l'on appelle l'**Auto-régression**.

C'est pourquoi il est dit qu'un LLM est une "machine statistique", pas une encyclopédie.

C'est pour celà aussi que l'on dit qu'une IA peut subir le concept d'**Hallucination**.

C'est la conséquence directe des probabilités : comme il cherche le "probable" et non le "vrai", il peut inventer des faits avec aplomb.

Un petit plus pour aller plus loin. Dans certains cas on entends aussi parler de la notion de **Température** :

- Si la température est à 0, l'IA choisira toujours "des croquettes" (le plus probable).
- Si la température est élevée (ex: 0.8), l'IA prendra des risques et pourra choisir "sa pâtée" ou même "le canapé" pour être plus créative.
    
## Histoire de l'IA


![ai.history_1.png](/ai_ml/ai.history_1.png)
![ai.history_2.png](/ai_ml/ai.history_2.png)

### Des machines qui pensent

> **Alan Turing** (Elu scientifique du 20 siecle en 2029), considéré comme le père de l'IA et de l'informatique théorique pour avoir formalisé le concept d'algorithme avec sa Machine de Turing (1936). Au-delà de son rôle clé dans le décryptage d'Enigma lors de la Seconde Guerre Mondiale, il pose dès 1950 les fondements de l'IA moderne. Son célèbre **Test de Turing** (ou **"Jeu de l'imitation"**) reste la référence pour évaluer la capacité d'une machine à imiter une conversation humaine de manière indiscernable.
{.is-success}

Source : Test de turing


### Conférence de Dartmouth

> **La Conférence de Dartmout** (été 1956) marque la naissance officielle de l'Intelligence Artificielle en tant que discipline scientifique autonome. C'est lors de cet événement que le terme "Intelligence Artificielle" est inventé. Organisée par quatre pionniers dont John McCarthy et Marvin Minsky, elle réunit durant deux mois des chercheurs pour tester une hypothèse audacieuse : « tout aspect de l'apprentissage ou de l'intelligence peut être décrit si précisément qu'une machine peut le simuler ». 
{.is-success}


### 1956 - 1974 : "Les années dorées"

> Cette période est marquée par un optimisme débordant et des financements massifs (notamment gouvernementaux). Les chercheurs pensaient alors toucher au but, comme l'illustre la célèbre prédiction de Marvin Minsky en 1967 : « Dans une génération... le problème de la création de l'intelligence artificielle sera substantiellement résolu ».
>
> La recherche se concentre alors sur des "micro-mondes" : des environnements simplifiés où l'IA peut raisonner sans la complexité du monde réel. C'est l'essor des premiers algorithmes de résolution de problèmes et du Traitement du Langage Naturel (NLP), illustré par trois projets cultes :
>
> - ELIZA (1966) : Le premier "chatbot" capable de simuler un psychothérapeute, bluffant les utilisateurs par de simples reformulations.
>
>![ai.eliza.png](/ai_ml/ai.eliza.png){.align-center}
>
> - SHRDLU et le "Blocks World" : Un programme capable de manipuler des blocs virtuels en comprenant des ordres complexes en langage naturel.
>
>![ai.blocks_world.jpg](/ai_ml/ai.blocks_world.jpg){.align-center}
>
> - Shakey le robot (1972) : La première machine mobile capable de percevoir son environnement et de planifier ses actions pour se déplacer intelligemment.
>
>![ai.shakey_robot.jpg](/ai_ml/ai.shakey_robot.jpg){.align-center}
>
> ‎ 
{.is-success}


### 1974 - 1980 : "Hiver de l'IA" - La désillusion

> Après l'euphorie, la désillusion. Au milieu des années 70, les financeurs (comme la DARPA) réalisent que les promesses de l'IA ont été exagérées. C'est le début de l'Hiver de l'IA : une période de coupes budgétaires drastiques et de scepticisme, déclenchée notamment par le critique Rapport Lighthill (1973).
> 
> Trois murs techniques ont stoppé les recherches :
>
> - Limitations : La puissance de calcul était trop limitée. Le matériel n'était tout simplement pas prêt pour traiter les informations nécessaires à une "vraie" intelligence.
>      
> - L'explosion combinatoire : Les chercheurs découvrent que résoudre des problèmes simples ne suffit pas. Dès qu'on augmente la complexité, le temps de calcul augmente de façon exponentielle, dépassant les capacités des ordinateurs de l'époque.
> 
> - Manques de données: Pas assez de données, ce qui entravait le processus de test, de développement et de raffinement des algorithmes.
>     
> - Critiques philosophiques : En 1980, John Searle contre-attaque le Test de Turing avec l'expérience de la "Chambre Chinoise". Il prouve q'une machine peut donner les bonnes réponses sans rien comprendre à ce qu'elle dit. Elle maitrise la syntaxe mais pas la sémantique.
> 
> Enfin, une guerre interne divise la communauté : les "Scruffies" (bricoleurs de code intuitif, comme pour SHRDLU) s'opposent aux "Neats" (partisans de la logique formelle et rigoureuse). C'est finalement l'approche "Neat" qui l'emportera pour garantir des résultats explicables et scientifiques.
{.is-success}


### Années 1980 : L'ère des Systèmes Experts 


> L'IA sort des laboratoires pour entrer dans les entreprises. C'est la première grande réussite commerciale de la discipline grâce aux Systèmes Experts. Ces logiciels visent à reproduire le raisonnement d'un spécialiste humain (un médecin, un garagiste).
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

> La crise des machines spécialisées La bulle des Systèmes Experts éclate à la fin des années 80. Le problème est économique : ces logiciels tournaient sur des ordinateurs très coûteux et spécialisés (comme les "Lisp Machines").
>
> Soudainement, les ordinateurs personnels (PC et Apple), bien moins chers, deviennent assez puissants pour les concurrencer. Les entreprises abandonnent les solutions spécialisées coûteuses. C'est un nouvel hiver budgétaire, mais qui prépare le terrain : la démocratisation des PC va bientôt permettre de collecter des données partout.
{.is-success}

### 1993 - 2011 : Le triomphe de la Data (L'IA probabiliste)

> La convergence : Puissance de calcul + Big Data Cette période marque le retour en grâce de l'IA, portée par trois facteurs techniques qui résolvent les blocages passés :
>
> La Loi de Moore : La puissance de calcul explose, permettant enfin de traiter des algorithmes lourds.
>
> Le Big Data : Avec internet et l'arrivée du smartphone (2007), la quantité de données disponibles devient gigantesque.
>
> L'apprentissage statistique : On arrête d'essayer de coder des règles logiques parfaites. On laisse les algorithmes "deviner" et apprendre des probabilités à partir de ces immenses bases de données. L'IA devient une discipline scientifique mature et rigoureuse.
{.is-success}

Cette époque a vu une nouvelle ère pour l'apprentissage automatique et l'IA, permettant de résoudre certains des problèmes causés auparavant par le manque de données et de puissance de calcul. La quantité de données a commencé à augmenter rapidement et à devenir plus largement disponible, pour le meilleur et pour le pire, notamment avec l'avènement du smartphone vers 2007. La puissance de calcul a augmenté de manière exponentielle, et les algorithmes ont évolué en parallèle. Le domaine a commencé à gagner en maturité à mesure que les jours libres du passé se cristallisaient en une véritable discipline.

### Aujourd'hui : L'Ère de l'Ubiquité et de l'Éthique

> Grands pouvoirs, grandes responsabilités L'IA est désormais invisible mais omniprésente (smartphones, réseaux sociaux, banques). La question n'est plus "Est-ce que ça marche ?", mais "Est-ce que c'est juste ?".
>
> Cette ère est marquée par une prise de conscience des risques sociétaux : biais algorithmiques, protection de la vie privée et manipulation de l'opinion. Comme le souligne Brad Smith (Microsoft), la technologie touche désormais aux droits humains fondamentaux. L'enjeu actuel est donc la régulation et la création d'une IA éthique et explicable.

## �Quickstart : L'IA en action

Maintenant que vous en savez plus sur la théorie, passons à la pratique. Prenez une IA (ChatGPT, Claude, Mistral, Gemini...) et entrez le prompt suivant.

Objectif : Observer comment l'IA se "perçoit" et tester sa capacité à structurer une réponse complexe.

```text
Agis comme un formateur en IA expliquant les LLM à un apprenant curieux. Structure ta réponse en 4 couches :  
1. **Auto-description littérale** : "Je suis un Grand Modèle de Langage (LLM), ce qui signifie..."  
2. **Analogie** : Compare un LLM à une « **poupée russe de savoir humain compressé** » (explique les symboles : couches de la poupée = couches du modèle, compression = entraînement).  
3. **Auto-dissection** : Décris le *processus de génération* de *cette phrase même* :  
   - Tokenisation → Embeddings → Attention → Prédiction → Décodage  
4. **Métacognition** : "Pourquoi cette explication en couches fonctionne-t-elle ? Parce que les LLM apprennent le savoir *hiérarchiquement* – reflétant la manière dont je viens de vous l'enseigner."  
```

> Analyse : Comparez les réponses. Vous remarquerez que l'IA est capable de "métacognition simulée" (expliquer son propre fonctionnement), ce qui est une excellente démonstration de ses capacités de synthèse.
{.is-warning}



## Sous le capot : Les progrès techniques

Les LLM sont de plus en plus performants. Ce n'est pas de la magie, mais une convergence de plusieurs avancées mathématiques et techniques.

Cf. [https://hai.stanford.edu/ai-index/2025-ai-index-report/technical-performance](https://hai.stanford.edu/ai-index/2025-ai-index-report/technical-performance)


### La vectorisation du langages (Embeddings) (Word2Vec et al.)

La première étape pour qu'une machine comprenne le langage, c'est de transformer les mots en mathématiques.

La vectorisation (ou Word2Vec et successeurs) permet de représenter les mots par des vecteurs numériques dans un espace multidimensionnel.

![ai.fundamentals.word2vec.general.png](/ai_ml/ai.fundamentals.word2vec.general.png){.align-center}
![ai.fundamentals.word2vec.vectors.jpg](/ai_ml/ai.fundamentals.word2vec.vectors.jpg){.align-center}

Cette capacité permet de calculer des distances entre les mots :

    Le mot "Roi" est mathématiquement proche de "Reine".

    Le mot "Paris" est proche de "France" de la même manière que "Rome" est proche de "Italie".

Au fur et à mesure de son entraînement, le modèle n'apprend pas juste des mots, il cartographie des concepts.

    À retenir : Pour l'IA, le sens d'un mot est défini par sa position dans cet espace mathématique.


### Les réseaux neuronaux profonds (Deep Learning)

**La taille des IA dites "Connexionistes" a grandement évoluée depuis quelques années.**

![ai.fundamentals.nn-size.png](/ai_ml/ai.fundamentals.nn-size.png){.align-center}

Une fois les mots transformés en chiffres, ils passent dans le "cerveau" du modèle.

Chaque neurone artificiel applique une transformation affine (combinaison linéaire pondérée des entrées) suivie d'une fonction d'activation non linéaire (comme ReLU ou Sigmoïde).

L'empilement de ces couches (d'où le terme "Deep" Learning) permet d'approximer des fonctions extrêmement complexes. Plus le réseau est profond, plus il est capable de comprendre des nuances subtiles et des abstractions (ironie, code complexe, raisonnement logique).



### L'attention et les transformers

**Le concept d'attention a permis des progrès considérables dans le traitement du langage naturel via la prise en compte des séquences de mots et phrases au lieu de mot à mot*.*

![ai.fundamentals.llm-schema.png](/ai_ml/ai.fundamentals.llm-schema.png)

Le mécanisme d'Attention permet au modèle de pondérer dynamiquement l'importance des éléments d'une séquence.

C'est un mécanisme qui permet de calculer des poids d'importance pour chaque élément d'une séquence lors du traitement d'une cible.

C'est ainsi que les LLM peuvent produire des phrases cohérentes avec le contexte.

Prenons la phrase : "L'animal n'a pas traversé la rue car il était trop fatigué."

    Pour un humain, "il" désigne "l'animal".

    Pour une ancienne IA, c'était ambigu (la rue ? l'animal ?).

    Grâce à l'Attention, le modèle connecte fortement le mot "il" au mot "animal" et faiblement au mot "rue". C'est ce qui permet de générer des textes longs et cohérents.

### Le renforcement par l'humain / Reinforcement Learning from Human Feedback (RLHF)

Une fois le modèle entraîné sur tout Internet, il sait parler, mais il peut être grossier, raciste ou inutile. Il faut l'éduquer.

**Pour cela, la dernière étape consiste à rendre le modèle plus performant en lui fournissant des récompenses pour les actions appropriées et des punitions pour les actions inappropriées.**

![ai.fundamentals.fine-tuning-llm-with-rlhf.png](/ai_ml/ai.fundamentals.fine-tuning-llm-with-rlhf.png)



Le RLHF est donc l'étape d'**alignement** du comportement du modèle. On récompense le modèle pour les bonnes réponses et on le "punit" pour les mauvaises.

1. Le modèle génère plusieurs réponses.

2. Des humains classent ces réponses de la meilleure à la pire.

3. Le modèle ajuste ses paramètres pour maximiser la "récompense" (satisfaction humaine).


Cette dernière étape optimise le réseau neuronal brut via une approche de fine-tuning et transforme un "compléteur de texte" brut en un "assistant conversationnel" utile (comme ChatGPT).



## Panorama actuel des modèles (Juin 2025)

![ai.llm.benchmark.2025-06-04.png](/ai_ml/ai.llm.benchmark.2025-06-04.png)

Il existe des benchmarks automatisés :

- [https://www.vellum.ai/llm-leaderboard](https://www.vellum.ai/llm-leaderboard)
- [https://artificialanalysis.ai/leaderboards/models](https://artificialanalysis.ai/leaderboards/models)
- [https://bigcode-bench.github.io/](https://bigcode-bench.github.io/)
- [https://llm-stats.com/](https://llm-stats.com/)
- [https://aider.chat/docs/leaderboards/](https://aider.chat/docs/leaderboards/)


## Quelques modèles et entreprises du LLM

![ai-llm-benchmark-202501.png](/ai_ml/ai-llm-benchmark-202501.png)

En janvier 2025 :

- DeepSeek / DeepSeek (Open Source)
- ChatGPT / OpenAI (Propriétaire)
- Llama / Meta (Open Source)
- Claude / Anthropic (Propriétaire)
- Qwen / Alibaba (Open Weight / Source)
- Codestral / Mistral (Open Source)
- Gemini / Google (Propriétaire)
- Gemma / Google (Open Weight)


## Les contraintes de choix

**Comment choisir un modèle adapté à ses besoins ?**

Il y a différents paramètres à considérer dans l'absolu :

- Efficacité pour les tâches demandées
- Coûts
- Open Source
- Exécution locale
- Taille
- Privacy
- Sécurité
- Performance

Souvent, les développeurs sont dépendants des modèles disponibles dans leur organisation.

**Il est néanmoins utile d'avoir une idée des modèles disponibles et de leur efficacité, si l'on considère qu'il s'agit d'outils de développement essentiels.**


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