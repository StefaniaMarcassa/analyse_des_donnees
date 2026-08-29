# Analyse des Données — L3 Économie

**CY Cergy Paris Université** · Année 2026–2027
**Enseignante :** Stefania Marcassa
**Volume :** 10 séances de cours magistral (1h30) + 10 séances de travaux dirigés
**Langage :** Python (Google Colab, aucune installation requise)
**Évaluation :** contrôle continu (mi-parcours) + contrôle terminal

---

## Objectifs du cours

À l'issue du cours, vous serez capable de :

1. **Trouver et charger** des données économiques réelles (INSEE, Eurostat, DARES, FRED, données de marché) et lire une documentation de source.
2. **Nettoyer et restructurer** un jeu de données brut : valeurs manquantes, doublons, recodages, passage long ↔ large, fusion de sources.
3. **Produire des statistiques descriptives défendables** : distributions, valeurs extrêmes, pondérations d'enquête.
4. **Construire des graphiques honnêtes** et savoir quel graphique répond à quelle question.
5. **Estimer et lire une régression** en pratique : spécification, écarts-types robustes, variables muettes, effets fixes, export d'un tableau publiable.
6. **Rendre un travail reproductible**, c'est-à-dire qu'un tiers puisse ré-exécuter votre code et retrouver vos résultats.

**Ce que le cours n'est pas.** Ce n'est pas un cours d'économétrie théorique : aucune propriété d'estimateur n'y est démontrée. C'est un cours de *mise en œuvre*, où la difficulté réside dans les données, pas dans les formules.

On estime couramment qu'un économiste consacre environ un tiers de son temps de recherche empirique à obtenir et nettoyer ses données. Ce tiers n'est enseigné nulle part ailleurs dans le cursus.

**Une mise en garde d'emblée.** Une régression ne mesure pas un effet causal. Elle mesure une association conditionnelle aux variables incluses. Toute la difficulté du métier tient dans l'écart entre les deux, et le cours y revient à chaque séance du Bloc 2.

---

## Prérequis et articulation

- Statistiques descriptives (L1), Probabilités et Analyse statistique (L2)
- Informatique (L2)
- Aucun prérequis en programmation

**Le cours d'Économétrie est suivi en parallèle, au même semestre.** Les séances de régression de ce cours (7 et 8, mi-octobre) supposent que les moindres carrés y aient été introduits. Ce cours n'en démontre aucune propriété : il en montre la mise en œuvre.

**Ce cours prépare directement au stage obligatoire du semestre 6.** Nettoyer un fichier mal formé, comprendre ce que mesure une variable, produire un tableau défendable : c'est ce qu'on demande à un stagiaire dès la première semaine.

---

## Organisation

Le cours magistral introduit les concepts et les commandes ; le TD les applique **systématiquement à des données économiques réelles**. Chaque TD suit le même format :

| Temps | Activité |
|---|---|
| 20–25 min | Retour sur le devoir précédent, bugs fréquents, rappel des concepts |
| 25–30 min | *Live coding* : le chargé de TD traite un mini-problème économique en direct |
| 40–45 min | Travail autonome sur un « notebook à trous », avec assistance |

Trois fichiers sont déposés sur ce site pour chaque séance :

- le **notebook à trous**, à ouvrir avant le TD ;
- le **script complet**, mis en ligne après la séance ;
- l'**exercice à la maison**, à traiter pour la séance suivante.

**Venez avec le notebook déjà ouvert dans votre navigateur.**

---

## Programme

### Bloc 1 — Fondations et manipulation de données (séances 1 à 5)

Ce bloc est **auto-suffisant** : il constitue à lui seul le périmètre du contrôle continu.

#### Séance 1 · Environnement et anatomie d'un tableau de données
**CM.** Prise en main de Colab. Types de données, listes, dictionnaires. Qu'est-ce qu'une observation, une variable, une unité statistique ? Structure en coupe, en panel, en série temporelle.
**TD — *Micro / consommation*.** Construire à la main un indice des prix à la consommation à partir d'un panier de biens pondéré. Comparer indice de Laspeyres et de Paasche sur les mêmes données.

#### Séance 2 · Chargement, inspection, filtrage
**CM.** Introduction à `pandas`. Lire un CSV et un fichier Excel mal formaté. Sélectionner, filtrer, trier. Lire un **dictionnaire des variables** : la compétence la plus sous-estimée du cours.
**TD — *Travail*.** Enquête Emploi (INSEE). Retrouver dans la documentation les variables d'activité, reconstruire le statut BIT (actif occupé / chômeur / inactif) et calculer un taux de chômage. Comparer au chiffre officiel et expliquer l'écart.

#### Séance 3 · Nettoyage des données
**CM.** Valeurs manquantes : détecter, comprendre l'origine (MCAR, MAR, MNAR), décider — supprimer, imputer, signaler — et assumer les conséquences de ce choix sur l'inférence. Doublons. Types mal interprétés à la lecture. Recodages.
**TD — *Travail / inégalités*.** Données de salaires (FiLoSoFi / DADS). Identifier le *top-coding*, les salaires nuls, les temps partiels mal renseignés. Documenter chaque décision de nettoyage et mesurer son effet sur le salaire moyen.

#### Séance 4 · Restructuration et fusion
**CM.** `groupby` et agrégation. `merge` : jointures internes, externes, clés multiples, doublons de clé. Passage format long ↔ format large. Structure d'un panel.
**TD — *Macro*.** Panel Eurostat pays × années. Fusionner PIB par habitant, taux de chômage et taux d'emploi issus de trois fichiers distincts. Passer en format long, gérer les pays absents d'une des sources, produire un tableau pays × décennie.

#### Séance 5 · Statistiques descriptives défendables
**CM.** Moyennes, médianes, quantiles. Valeurs extrêmes : distinguer valeur extrême, point atypique et point influent. **Pondérations d'enquête** : pourquoi une moyenne non pondérée sur données d'enquête est fausse. Puis le livrable réel du métier : le **tableau de comparaison de groupes**, avec écarts-types, erreurs-types et intervalles de confiance. Comparaison de moyennes par le test de Welch, systématiquement. Ce qu'une p-value dit et ne dit pas ; pourquoi significatif ne veut pas dire important. Test du khi-deux pour deux variables qualitatives.
**TD — *Micro / redistribution*.** Distribution des revenus des ménages : déciles, rapport interdécile, indice de Gini. Construire le tableau de comparaison des revenus entre deux groupes, avec intervalles de confiance, et l'interpréter. Refaire l'ensemble sans pondération et mesurer le biais.

> **Contrôle continu à l'issue de cette séance.** Voir la section Évaluation.

---

### Bloc 2 — Visualisation et régression appliquée (séances 6 à 8)

#### Séance 6 · Visualisation de données économiques
**CM.** `matplotlib` et `seaborn`. Quel graphique pour quelle question : distribution, relation, évolution, comparaison. Graphiques trompeurs : axes tronqués, échelles, agrégation abusive.
**TD — *Travail / macro*.** Courbe de Beveridge française (chômage vs emplois vacants, DARES) : identifier visuellement les déplacements de courbe et les dater. Puis courbe de Phillips sur données longues et discussion de sa disparition apparente.

#### Séance 7 · Régression en pratique I
**CM.** `statsmodels`. Lecture complète d'une sortie de régression. **Une différence de moyennes entre deux groupes est le coefficient d'une régression sur une muette** : le t du test et le t du coefficient sont le même nombre, montré une fois sur les deux sorties côte à côte. Variables muettes et catégories de référence. Écarts-types robustes et *clustering*. Ce que le R² dit et ne dit pas. Ce qu'un coefficient permet et ne permet pas d'affirmer.
**TD — *Travail*.** Équation de Mincer : rendement d'une année d'éducation supplémentaire. Ajouter l'expérience et son carré, une muette de genre, puis une interaction genre × éducation. Interpréter chaque coefficient en français, en une phrase, sans employer le mot « effet » sans justification.

#### Séance 8 · Régression en pratique II
**CM.** Transformations logarithmiques et interprétation en élasticité. Interactions. Effets fixes par groupe. Export automatique d'un tableau de régression au format LaTeX.
**TD — *Micro / immobilier*.** Régression hédonique sur données DVF (transactions immobilières). Prix au m² en fonction des caractéristiques, avec effets fixes départementaux puis communaux. Observer le déplacement des coefficients et discuter ce que les effets fixes absorbent.

---

### Bloc 3 — Séries temporelles, finance, synthèse (séances 9 et 10)

#### Séance 9 · Séries temporelles et import automatique
**CM.** Manipulation des dates. Import par API (FRED, Eurostat). Taux de croissance, moyennes mobiles, désaisonnalisation simple. Stationnarité : le problème en pratique.
**TD — *Finance*.** Séries de cours boursiers (CAC 40 et titres individuels). Calculer des rendements, mesurer la volatilité et son regroupement dans le temps, estimer un bêta de MEDAF par régression. Vérifier ce que devient le bêta selon la fenêtre d'estimation retenue.

#### Séance 10 · Prédiction, reproductibilité, synthèse
**CM.** **Prédiction et causalité** : pourquoi un bon modèle prédictif peut avoir des coefficients ininterprétables, et pourquoi un bon modèle causal peut mal prédire. Démonstration commentée d'une régression LASSO. Organisation d'un projet reproductible.
**TD — Révisions.** Traitement d'un sujet de contrôle terminal des années précédentes, corrigé en séance. Retour sur les erreurs récurrentes du contrôle continu.

---

## Couverture par champ disciplinaire

| Champ | Séances de TD |
|---|---|
| Économie du travail | 2, 3, 6, 7 |
| Macroéconomie | 4, 6, 9 |
| Microéconomie appliquée | 1, 5, 8 |
| Finance | 9 |

---

## Sources de données utilisées

- **INSEE** — Enquête Emploi, FiLoSoFi, DADS, séries conjoncturelles
- **DARES** — offres et demandes d'emploi
- **DVF** (data.gouv.fr) — transactions immobilières
- **Eurostat** — comptes nationaux, marché du travail
- **FRED** (Federal Reserve Bank of St. Louis) — séries macroéconomiques américaines
- **Données de marché** — cours et indices boursiers

Toutes les sources sont publiques et gratuites. Les extraits utilisés en TD sont déposés sur ce site ; l'accès aux fichiers complets est expliqué en séance.

---

## Évaluation

| Épreuve | Poids | Moment | Durée | Périmètre |
|---|---|---|---|---|
| **Contrôle continu (CC)** | 50 % | Lundi 5 octobre | 1 h | Séances 1 à 5 |
| **Contrôle terminal (CT)** | 50 % | Session d'examens | 2 h | Ensemble du cours |

Les deux épreuves se déroulent **sur papier, sans machine et sans document**. Aucune des deux ne demande d'écrire du code de mémoire.

### Ce qui est évalué

Une épreuve écrite pour un cours de programmation peut sembler paradoxale. Elle ne l'est pas : ce que le cours cherche à installer n'est pas la mémorisation d'une syntaxe — que tout éditeur complète et que tout assistant produit — mais le **jugement sur les données**. C'est cela qui s'évalue sur papier, et c'est cela qui distingue un économiste d'un exécutant.

Les deux épreuves reposent sur quatre types de questions :

1. **Lecture de sortie.** Un tableau descriptif, une sortie de régression ou un graphique vous est donné ; vous devez dire ce qu'il montre, et surtout ce qu'il ne montre pas.
2. **Diagnostic.** Un extrait de données ou de code est présenté avec un problème (valeurs manquantes mal traitées, jointure qui duplique des lignes, moyenne non pondérée, axe tronqué) ; vous devez l'identifier et proposer une correction.
3. **Interprétation économique.** Un coefficient, une élasticité, un écart de moyennes : que peut-on en dire, sous quelles conditions, et quelle formulation serait abusive.
4. **Code court.** Trois à cinq lignes à écrire ou à compléter — jamais un script entier.

### Contrôle continu — séance 5

Porte sur le Bloc 1 : chargement et inspection, lecture d'un dictionnaire des variables, traitement des manquants et des points atypiques, fusion et restructuration, statistiques descriptives, pondération, et lecture d'un tableau de comparaison de groupes.

Deux questions au moins portent sur une **décision de nettoyage à justifier**. Il n'y a pas de bonne réponse unique ; c'est la justification qui est notée.

### Contrôle terminal

Porte sur l'ensemble du cours, avec une pondération plus forte sur les séances 6 à 10, non couvertes par le CC. Une partie de l'épreuve est consacrée à la lecture et à l'interprétation d'un tableau de régression complet.

### Exercices à la maison

Les exercices hebdomadaires ne sont **pas notés**, mais ils sont la seule préparation efficace aux deux épreuves : les questions de diagnostic sont construites à partir des erreurs qui y apparaissent le plus souvent. Les corrections sont mises en ligne après chaque séance.

---

## Usage des assistants d'IA

L'usage d'un assistant d'IA (ChatGPT, Claude, Copilot) est **autorisé et attendu** pour les exercices : c'est l'outil de travail réel de votre future profession. Il est évidemment interdit lors des deux épreuves, qui se tiennent sans machine.

C'est précisément pour cette raison que le format des épreuves est celui décrit ci-dessus. Un assistant écrit très bien la syntaxe ; il est peu fiable sur les décisions qui font l'objet de ce cours — quelle variable de l'enquête retenir, comment traiter les manquants, quelle spécification est défendable, ce qu'un coefficient autorise à conclure. Le CC et le CT évaluent exactement cette zone.

Un conseil pratique, sans valeur réglementaire : si vous ne pouvez pas expliquer une ligne que l'assistant a produite, vous ne saurez pas répondre à la question de diagnostic qui portera dessus. L'écart apparaît immédiatement dans les copies.

---

## Environnement de travail

Tout le cours se fait sur **Google Colab**, dans le navigateur. Aucune installation, aucune version de Python à gérer, aucun problème de chemin d'accès. Un compte Google suffit.

Si vous préférez travailler en local (Anaconda, VS Code), c'est possible mais non assisté : les séances de TD ne sont pas consacrées au dépannage d'installations.

---

## Bibliographie

- Alberto Cairo, *How Charts Lie*, Norton, 2019 — sur les graphiques honnêtes.
- Angrist & Pischke, *Mastering 'Metrics*, Princeton University Press, 2014 — pour le rappel des méthodes.
- Documentation `pandas` : [pandas.pydata.org/docs](https://pandas.pydata.org/docs/) — à consulter en réflexe, pas en dernier recours.
- Documentation `statsmodels` : [statsmodels.org](https://www.statsmodels.org/)

---

## Contact et permanences

Questions de cours : à poser en séance ou en TD, de préférence.
Questions techniques bloquantes : décrivez le problème **avec le message d'erreur complet** ; un « ça ne marche pas » ne permet aucune réponse utile.
