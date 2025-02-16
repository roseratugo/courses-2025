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

![Bus Factor Illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Bus_factor_diagram.svg/1200px-Bus_factor_diagram.svg.png)

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

![Illustration de dépendance](https://miro.medium.com/max/1400/1*fIcKKTXYhS66FUbjwGfM8A.png)

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

![Exemple de projet avec un Bus Factor critique](https://media.licdn.com/dms/image/C5612AQHgWSPcaeYZQA/article-cover_image-shrink_600_2000/0/1520110595336?e=2147483647&v=beta&t=yLdpw0GONKKQOCyQkCzglPkmjfjcJAr6n34u9sJX3k8)

```sh
# Trouver qui a écrit un morceau de code spécifique
git blame src/app.js
```

---

## 💰 **Impact économique**
📌 Coût élevé pour former de nouveaux développeurs.

📌 Retards dans les livraisons.

📌 Risque de **perte de compétitivité**.

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

![Exemple de contribution Git](https://user-images.githubusercontent.com/6280556/73296054-dc8f5700-41ef-11ea-9399-6634a1fd61b2.png)

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

## 🏗 **4. Mapping des responsabilités**
- Qui est responsable de quoi ?
- Les tâches sont-elles bien réparties ?

---

## 🔧 4. Comment réduire le Bus Factor ?

### 📖 **1. Documentation claire**
📌 Une bonne documentation permet à n’importe qui de reprendre le projet.

✅ **README.md** clair.

✅ **Documentation API** (Swagger, Postman…).

✅ **Commentaires pertinents dans le code**.

![Documentation et bonne pratique](https://user-images.githubusercontent.com/6280556/73296449-a69e6c00-41f0-11ea-91c4-4b3e5c6fd083.png)

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

## 🤝 **2. Partage des connaissances**
📌 Éviter que **seule une personne détienne l’expertise**.

✅ **Code Reviews systématiques**.

✅ **Pair Programming**.

✅ **Sessions de formation internes**.

---

## 🔄 **3. Automatisation et Standardisation**
📌 Moins de dépendance humaine = **plus de résilience**.

✅ **CI/CD automatisé**.

✅ **Utilisation de frameworks standards**.

✅ **Scripts d’installation (`docker-compose`, `npm scripts`)**.

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

## 🔀 **4. Rotation des rôles**
📌 Assurer une **distribution des responsabilités**.

✅ Ne pas laisser une seule personne gérer une partie critique.

✅ Organiser des **sessions de passation de connaissances**.

---

## 🚨 5. Étude de cas : Bus Factor critique

📌 **Contexte** : Une startup utilise **NestJS + Vue.js**.  
Le CTO, unique développeur du backend, **démissionne**.

💥 **Problèmes** :
- Aucune documentation.
- CI/CD incompréhensible.
- Code ultra personnalisé.

---

## ✅ Solution mise en place

✅ **Analyse du code** par l’équipe.

✅ **Sessions de reverse-engineering**.

✅ **Création d’une documentation technique**.

✅ **Formation des développeurs sur NestJS**.

📌 **Résultat** : Éviter un **retard de plusieurs mois**.

---

## 🚀 Conclusion : Se protéger du Bus Factor

✅ **Documentation complète et accessible**.

✅ **Partage des connaissances** (Code Reviews, Pair Programming).

✅ **Automatisation des processus et standardisation des outils**.

✅ **Rotation des responsabilités et planification de la succession**.

---

## 📚 **Ressources**
- [Bus Factor : définition](https://en.wikipedia.org/wiki/Bus_factor)
- [Guide sur la documentation technique](https://www.writethedocs.org/)
- [GitHub Insights](https://github.com/features/insights)
