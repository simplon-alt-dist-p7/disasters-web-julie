# Backlog du projet "Optimisation Sante+"

## USER STORIES

---

### Story 1 : Chargement initial plus rapide

**En tant que** nouvel utilisateur web,  
**je veux** que l’écran d’accueil charge en moins de 1,5 s  
**afin de** ne pas décrocher lors d’un pic de réseau lent.

- 🎯 Objectif : temps de chargement < 1500 ms
- 🧱 BP associée : réduire taille des ressources / lazy-loading
- 🛠️ KPI : LCP sur web (Lighthouse)
- 📅 Tag roadmap : M2

---

### Story 2 : Réduction poids images

**En tant que** utilisateur récurrent,  
**je veux** que les visuels du dashboard soient plus légers  
**afin de** économiser de la data sur mon forfait.

- 🎯 Objectif : 80% des images converties en WebP
- 🧱 BP associée : compression d’images / formats modernes
- 🛠️ KPI : poids total dossier `/assets` < 2 Mo
- 📅 Tag roadmap : M3

---

### Story 3 : Accessibilité améliorée

**En tant que** utilisateur malvoyant,  
**je veux** que les contrastes texte/fond soient conformes AA  
**afin de** pouvoir utiliser l’app sans difficulté visuelle.

- 🎯 Objectif : conformité AA WCAG
- 🧱 BP associée : respect contrastes (RGESN 6.3)
- 🛠️ KPI : score accessibilité Lighthouse > 90
- 📅 Tag roadmap : M4

---

### Story 4 : Désactivation des animations

**En tant que** utilisateur facilement déconcentré ou sensible aux mouvements,
**je veux** pouvoir désactiver les animations de l'interface,
**afin de** rester concentré sur le contenu et éviter toute gêne visuelle.

- 🎯 Objectif : mode "Réduire les animations" disponible dans les préférences
- 🧱 BP associée : respect de prefers-reduced-motion (WCAG)
- 🛠️ KPI : 100 % des animations CSS et Three.js désactivables
- 📅 Tag roadmap : M2

---

### Story 5 : Retour visuel rapide lors des chargements

**En tant que** utilisateur impatient,
**je veux** être informé immédiatement lorsqu'un contenu est en cours de chargement,
**afin de** comprendre que l'application fonctionne correctement.

- 🎯 Objectif : affichage systématique d'un indicateur de chargement ou skeleton screen
- 🧱 BP associée : perception de performance
- 🛠️ KPI : aucun écran vide supérieur à 500 ms
- 📅 Tag roadmap : M2

---

### Story 6 : Rationalisation des styles globaux

**En tant que** développeur frontend,
**je veux** simplifier et factoriser les styles du fichier index.css,
**afin de** faciliter la maintenance et réduire le volume de CSS chargé.

- 🎯 Objectif : suppression des styles inutilisés et mutualisation des tokens
- 🧱 BP associée : réduction du code mort
- 🛠️ KPI : réduction du poids CSS de 30 %
- 📅 Tag roadmap : M2

---

<!-- ⚠️ 1466 requêtes HTTP -->
### Story 7 : Réduction du nombre de requêtes HTTP

**En tant que** développeur frontend,
**je veux** limiter le nombre de ressources téléchargées,
**afin de** réduire le temps de chargement et l'impact environnemental.

- 🎯 Objectif : moins de 100 requêtes HTTP
- 🧱 BP associée : sobriété réseau
- 🛠️ KPI : nombre de requêtes observées par GreenIT
- 📅 Tag roadmap : M2

---

### Story 8 : Réduction des dépendances inutilisées

**En tant que** développeur frontend,
**je veux** identifier et supprimer les bibliothèques peu ou pas utilisées,
**afin de** réduire la dette technique et la taille du bundle.

- 🎯 Objectif : audit complet des dépendances npm
- 🧱 BP associée : sobriété logicielle
- 🛠️ KPI : réduction du nombre de dépendances de 20 %
- 📅 Tag roadmap : M3