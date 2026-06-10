# 🍃 Audit Green IT – Analyse EcoIndex

- **Date de l'analyse :** 2026-06-10 10:10am
- **URL analysée :** https://localhost:3000
- **Outil utilisé :** Extension Chrome GreenIT-Analysis

---

## Résultats EcoIndex

| Indicateur         | Valeur         |
| ------------------ | -------------- |
| EcoIndex           | **46.53 (D)**  |
| Consommation d'eau | **3.10 cl**    |
| Émissions GES      | **2.07 gCO₂e** |

### Interprétation

L'EcoIndex obtenu est de **46.53**, correspondant à une note **D**. Ce résultat indique que la page présente une marge d'amélioration significative en matière de performance environnementale, principalement liée au volume des ressources téléchargées et au nombre très élevé de requêtes réseau.

---

## Caractéristiques techniques de la page

| Critère                  | Valeur             |
| ------------------------ | ------------------ |
| Nombre de requêtes HTTP  | 1466               |
| Taille totale de la page | 10 286 Ko (~10 Mo) |
| Taille du DOM            | 89 éléments        |

### Observations

* Le **nombre de requêtes HTTP** est extrêmement élevé (1466 contre une recommandation de 40 maximum).
* Le **poids total de la page** dépasse 10 Mo, ce qui impacte fortement la consommation de bande passante et l'empreinte environnementale.
* La **taille du DOM** reste faible et n'est pas un facteur de dégradation.

---

## Analyse des bonnes pratiques

| Bonne pratique                                       | Résultat                                     |
| ---------------------------------------------------- | -------------------------------------------- |
| Ajouter des en-têtes Cache-Control / Expires         | ✅ 1455 / 1461 ressources mises en cache      |
| Compresser les ressources                            | ❌ Seulement 3,5 % des ressources compressées |
| Limiter le nombre de domaines (< 6)                  | ✅ 4 domaines utilisés                        |
| Éviter le redimensionnement d'images côté navigateur | ✅ 0 image concernée                          |
| Externaliser CSS et JavaScript                       | ⚠️ 2 ressources inline détectées             |
| Éviter les erreurs HTTP                              | ✅ 0 erreur                                   |
| Limiter les requêtes HTTP (≤ 40)                     | ❌ 1466 requêtes                              |
| Éviter les images inutiles                           | ✅ Aucune image inutile téléchargée           |
| Minifier CSS et JavaScript                           | ❌ 1455 / 1457 fichiers non minifiés          |
| Éviter les cookies sur ressources statiques          | ✅ Aucun cookie                               |
| Éviter les redirections                              | ✅ 0 redirection                              |
| Optimiser les images bitmap                          | ✅ Aucune optimisation nécessaire             |
| Optimiser les SVG                                    | ✅ Aucune optimisation nécessaire             |
| Fournir une feuille de style d'impression            | ⚠️ Absente                                   |
| Éviter les widgets sociaux standards                 | ✅ Aucun détecté                              |
| Limiter le nombre de fichiers CSS (≤ 10)             | ✅ 7 fichiers CSS                             |
| Utiliser HTTP/2                                      | ❌ 1455 / 1466 ressources en HTTP/1           |
| Utiliser des polices standards                       | ⚠️ 1 police spécifique utilisée              |

---

## Principaux axes d'amélioration

### Priorité élevée

1. **Réduire drastiquement le nombre de requêtes HTTP**

   * Mutualiser les ressources.
   * Supprimer les dépendances inutilisées.
   * Regrouper certains fichiers lorsque cela est pertinent.

2. **Activer la compression des ressources**

   * Utiliser Gzip ou Brotli sur les ressources textuelles.
   * Objectif : >95 % des ressources compressées.

3. **Minifier les fichiers CSS et JavaScript**

   * Réduire la taille des ressources transférées.
   * Mettre en place une étape de minification dans le processus de build.

4. **Migrer vers HTTP/2 ou HTTP/3**

   * Améliorer les performances réseau.
   * Réduire les coûts liés aux nombreuses requêtes.

### Priorité moyenne

1. Externaliser les styles et scripts inline.
2. Ajouter une feuille de style d'impression si nécessaire.
3. Évaluer l'usage de polices système ou optimisées.

---

## Synthèse

| Critère                | Évaluation          |
| ---------------------- | ------------------- |
| Eco-conception globale | ⚠️ À améliorer      |
| Mise en cache          | ✅ Bonne             |
| Compression            | ❌ Très insuffisante |
| Minification           | ❌ Très insuffisante |
| Nombre de requêtes     | ❌ Critique          |
| Utilisation HTTP/2     | ❌ Critique          |
| Gestion des images     | ✅ Correcte          |

### Conclusion

La page obtient un **EcoIndex D**, principalement en raison d'un **nombre excessif de requêtes HTTP**, de l'absence de **compression généralisée**, de la **non-minification des ressources** et d'une utilisation majoritaire de **HTTP/1**. Les mécanismes de cache sont correctement configurés, mais les optimisations réseau constituent le principal levier d'amélioration de la performance environnementale.


___
___

# 💡 Audit Lighthouse – Performance

- **Date de l'analyse :** 2026-06-10 11:00am
- **URL analysée :** http://localhost:3000
- **Outil utilisé :** Lighthouse (Chrome DevTools)

---

# Résumé exécutif

| Indicateur         | Valeur                 |
| ------------------ | ---------------------- |
| Score Performance  | **53 / 100**           |
| Évaluation globale | ⚠️ Performance moyenne |
| Niveau de priorité | Élevé                  |

Le score Lighthouse de **53/100** révèle plusieurs problèmes de chargement impactant l'expérience utilisateur. Les principaux facteurs dégradant les performances sont :

* un **Largest Contentful Paint (LCP)** très élevé ;
* un **volume réseau important** (> 10 Mo) ;
* de nombreux fichiers JavaScript volumineux ;
* l'absence de minification JavaScript ;
* le chargement de bibliothèques lourdes non optimisées.

---

# Métriques Core Web Vitals

| Métrique                       | Résultat | Évaluation     |
| ------------------------------ | -------- | -------------- |
| First Contentful Paint (FCP)   | 6,9 s    | ❌ Mauvais      |
| Largest Contentful Paint (LCP) | 13,3 s   | ❌ Très mauvais |
| Total Blocking Time (TBT)      | 130 ms   | ✅ Correct      |
| Cumulative Layout Shift (CLS)  | 0        | ✅ Excellent    |
| Speed Index                    | 8,5 s    | ❌ Mauvais      |

## Analyse

### First Contentful Paint (FCP)

Le premier contenu visible apparaît après **6,9 secondes**, ce qui est largement supérieur aux recommandations Lighthouse (< 1,8 s).

### Largest Contentful Paint (LCP)

Le contenu principal n'est affiché qu'après **13,3 secondes**.

Ce résultat constitue actuellement le principal problème de performance de l'application.

### Total Blocking Time (TBT)

Avec seulement **130 ms**, le temps de blocage reste acceptable et indique que l'application demeure relativement réactive une fois les ressources chargées.

### Cumulative Layout Shift (CLS)

Aucun déplacement visuel n'a été détecté (**CLS = 0**), ce qui garantit une excellente stabilité de l'interface.

### Speed Index

Le contenu visible se construit lentement (**8,5 s**), traduisant un affichage progressif peu performant.

---

# Principaux constats Lighthouse

## Insights identifiés

* LCP Breakdown
* Network Dependency Tree
* Layout Shift Culprits
* Third Parties Analysis

Ces éléments confirment que les performances sont principalement affectées par :

* le poids des ressources JavaScript ;
* les dépendances externes ;
* l'ordre de chargement des ressources réseau.

---

# Diagnostics détaillés

## Travail du thread principal

Temps total observé : **2,2 secondes**

| Catégorie                    | Temps    |
| ---------------------------- | -------- |
| Other                        | 1 600 ms |
| Style & Layout               | 415 ms   |
| Script Evaluation            | 134 ms   |
| Script Parsing & Compilation | 66 ms    |
| Parse HTML & CSS             | 14 ms    |
| Rendering                    | 3 ms     |

### Analyse

Une part importante du temps CPU est consommée dans des traitements classés "Other", ce qui mérite une investigation complémentaire via le profiler Chrome.

---

## JavaScript non minifié

### Économie potentielle

**6 854 KiB**

Lighthouse détecte une absence quasi complète de minification JavaScript.

### Impact

* augmentation du temps de téléchargement ;
* augmentation du temps de parsing ;
* dégradation du FCP et du LCP.

---

## JavaScript inutilisé

### Économie potentielle

**1 641 KiB**

Les principaux contributeurs sont :

| Ressource                | Taille transférée | Gain potentiel |
| ------------------------ | ----------------- | -------------- |
| three.js                 | 1 174 KiB         | 937 KiB        |
| react-dom.development.js | 888 KiB           | 422 KiB        |
| lodash.js                | 219 KiB           | 164 KiB        |
| react.development.js     | 75 KiB            | 49 KiB         |

### Analyse

Une quantité importante de code est téléchargée mais jamais exécutée.

Cela suggère :

* absence de tree shaking efficace ;
* bundles de développement utilisés ;
* dépendances trop larges pour les besoins réels de la page.

---

## Charge réseau excessive

### Taille totale transférée

**10 046 KiB (~10 Mo)**

### Principaux contributeurs

| Ressource         | Taille  |
| ----------------- | ------- |
| three.js          | 1,17 Mo |
| chunk-NGODP64W.js | 906 Ko  |
| lucide-react.js   | 238 Ko  |
| lodash.js         | 219 Ko  |
| icons/index.js    | 154 Ko  |
| vite client       | 135 Ko  |
| react refresh     | 115 Ko  |

### Analyse

Le poids global est particulièrement élevé pour une page web moderne.

Les bibliothèques 3D représentent une part significative du volume téléchargé.

---

## Longues tâches JavaScript

Lighthouse identifie **4 tâches longues** sur le thread principal.

| Durée  |
| ------ |
| 480 ms |
| 196 ms |
| 59 ms  |
| 195 ms |

### Impact

Ces tâches peuvent provoquer :

* des micro-freezes ;
* une dégradation de l'interactivité ;
* un ressenti de lenteur.

---

## Back/Forward Cache (bfcache)

### Échec détecté

Motif :

> Pages with WebSocket cannot enter back/forward cache.

### Conséquence

Les retours arrière dans le navigateur ne bénéficient pas du cache instantané proposé par les navigateurs modernes.

---

# Points positifs

Les audits suivants sont validés :

✅ Cache efficace

✅ Taille du DOM optimisée

✅ Pas de duplication JavaScript majeure

✅ Chargement des polices correctement configuré

✅ Livraison des images optimisée

✅ HTTP moderne utilisé

✅ CSS minifié

✅ CSS inutilisé limité

✅ Temps d'exécution JavaScript faible

✅ Animations optimisées

✅ Images avec dimensions explicites

✅ Aucun problème de CLS

---

# Recommandations

## Priorité 1 – Réduire le poids JavaScript

* Utiliser les builds de production.
* Activer la minification.
* Vérifier le tree shaking.
* Fractionner les bundles (code splitting).

### Gain estimé

≈ 8 Mo

---

## Priorité 2 – Optimiser Three.js

* Charger les scènes à la demande.
* Utiliser des imports ciblés.
* Découper les fonctionnalités 3D en modules.

### Gain estimé

≈ 900 Ko

---

## Priorité 3 – Charger les ressources à la demande

Mettre en œuvre :

* Lazy Loading ;
* Dynamic Imports ;
* Suspense React.

---

## Priorité 4 – Réduire le LCP

* Identifier l'élément LCP exact.
* Précharger les ressources critiques.
* Limiter les dépendances bloquantes.

Objectif :

* LCP < 2,5 s
* FCP < 1,8 s

---

# Synthèse

| Domaine                    | État           |
| -------------------------- | -------------- |
| Core Web Vitals            | ⚠️ Moyen       |
| Stabilité visuelle         | ✅ Excellent    |
| Interactivité              | ✅ Correcte     |
| Taille des bundles         | ❌ Critique     |
| Charge réseau              | ❌ Critique     |
| Optimisation JavaScript    | ❌ Critique     |
| Architecture de chargement | ⚠️ À améliorer |

## Conclusion

Le principal problème de performance provient du **volume excessif de JavaScript téléchargé et exécuté**, notamment autour de **Three.js**, des dépendances React en mode développement et de plusieurs bundles volumineux. Malgré une bonne stabilité visuelle (CLS = 0) et un TBT satisfaisant, les temps de rendu initiaux (FCP 6,9 s et LCP 13,3 s) restent trop élevés pour offrir une expérience utilisateur fluide.

Les gains les plus importants seront obtenus en activant les builds de production, en réduisant la taille des bundles JavaScript et en mettant en place une stratégie de chargement différé des ressources non critiques.