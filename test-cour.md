# Le Bus Factor dans le Développement Web
---

## 🎯 Objectifs du cours

✅ Comprendre le concept de **Bus Factor** et son impact.

✅ Identifier les risques liés à une faible résilience des connaissances.

✅ Mettre en place des stratégies pour **réduire le Bus Factor**.

---

## 📌 1. Qu’est-ce que le Bus Factor ?

Le **Bus Factor** est le **nombre de personnes pouvant disparaître avant que le projet ne devienne inmaintenable**.

🚌 **Origine** : "Que se passe-t-il si un développeur clé est percuté par un bus ?" (ou quitte l'équipe).

![Bus Factor Illustration](https://placehold.co/600x400?text=Bus+Factor+Illustration)

```js
// Exemple de code ultra personnalisé (Bus Factor = 1)
function processData(input) {
  return input.split("").reverse().join(""); // Personne ne comprend pourquoi
}
```

🚨 **Problème** : Personne ne sait pourquoi ce code fonctionne ainsi.

---

## 🛑 Pourquoi un faible Bus Factor est dangereux ?

### 🚨 Risques :

❌ Dépendance à une seule personne.

❌ Maintenance compliquée, code difficile à comprendre.

❌ Délais rallongés, coûts élevés.

---

## 🔥 2. Exemples de conséquences

### 🏢 **Problème organisationnel**
📌 Dépendance excessive à une seule personne.

📌 Si elle part → **rupture du développement**.

![Illustration de dépendance](https://placehold.co/600x400?text=Dependance+Projet)

```sh
# Vérifier qui modifie le plus le projet
git shortlog -s -n
```

Si une seule personne est en haut du classement, c'est un **Bus Factor critique**.

---

## 🐌 **Maintenance difficile**
📌 Code sans documentation.

📌 Temps perdu à essayer de comprendre l’architecture.

📌 Nécessité de **reverse-engineering**.

![Exemple de projet avec un Bus Factor critique](https://placehold.co/600x400?text=Projet+Bus+Factor)

```sh
# Trouver qui a écrit un morceau de code spécifique
git blame src/app.js
```

---

## 📊 3. Comment évaluer le Bus Factor ?

### 🧐 **1. Audit des connaissances**
- Qui possède les compétences clés ?
- Que se passe-t-il si cette personne part ?

```sh
# Voir qui travaille sur chaque fichier
git log --pretty=format:"%an" --name-only | sort | uniq -c | sort -nr
```

---

## 🔍 **2. Analyse des contributions Git**
- Qui a écrit quelles parties du code ?
- Utiliser **GitHub Insights** ou `git shortlog -s -n`.

![Exemple de contribution Git](https://placehold.co/600x400?text=Git+Contributions)

```sh
# Qui a fait le plus de commits ?
git shortlog -s -n
```

---

## 📖 **3. Documentation existante**
- Le projet a-t-il un **README** ?
- La documentation est-elle suffisante pour un nouveau développeur ?

```md
# Exemple de README pour éviter le Bus Factor
## Installation
```sh
npm install
npm start
```

## API Endpoints
- **GET /users** → Liste des utilisateurs
- **POST /users** → Créer un utilisateur
```

---

## 🔧 4. Comment réduire le Bus Factor ?

### 📖 **1. Documentation claire**
📌 Une bonne documentation permet à n’importe qui de reprendre le projet.

✅ **README.md** clair.

✅ **Documentation API** (Swagger, Postman…).

✅ **Commentaires pertinents dans le code**.

![Documentation et bonne pratique](https://placehold.co/600x400?text=Documentation+Projet)

```js
// Mauvais commentaire
function calc(a, b) {
  return a + b; // Ajoute les valeurs
}

// Bon commentaire
/**
 * Additionne deux nombres et retourne la somme.
 * @param {number} a - Premier nombre
 * @param {number} b - Deuxième nombre
 * @returns {number} - Somme des deux nombres
 */
function calc(a, b) {
  return a + b;
}
```

---

## 🔄 **3. Automatisation et Standardisation**
📌 Moins de dépendance humaine = **plus de résilience**.

✅ **CI/CD automatisé**.

✅ **Utilisation de frameworks standards**.

✅ **Scripts d’installation (`docker-compose`, `npm scripts`)**.

![Automatisation](https://placehold.co/600x400?text=Automatisation+CI%2FCD)

```yaml
# Exemple de fichier GitHub Actions (CI/CD)
name: Deploy
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Install dependencies
        run: npm install
      - name: Run tests
        run: npm test
```

---

## 🚀 Conclusion : Se protéger du Bus Factor

✅ **Documentation complète et accessible**.

✅ **Partage des connaissances** (Code Reviews, Pair Programming).

✅ **Automatisation des processus et standardisation des outils**.

✅ **Rotation des responsabilités et planification de la succession**.

![Bus Factor Solution](https://placehold.co/600x400?text=Bus+Factor+Solution)

---

## 📚 **Ressources**
- [Bus Factor : définition](https://en.wikipedia.org/wiki/Bus_factor)
- [Guide sur la documentation technique](https://www.writethedocs.org/)
- [GitHub Insights](https://github.com/features/insights)
