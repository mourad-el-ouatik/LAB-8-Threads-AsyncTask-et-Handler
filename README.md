# ⏳ LAB-8 | Threads-AsyncTask-et-Handler
Une application Android démontrant la **programmation asynchrone** sur Android, avec un Thread de fond, une AsyncTask avec progression, et un Handler pour revenir sur le UI thread sans bloquer l'interface.

---

## ✨ Fonctionnalités

- 🖼️ **Chargement d'image** — Thread de fond simulant un téléchargement avec `Handler.post()` pour mettre à jour l'UI
- ⚙️ **Calcul lourd** — AsyncTask exécutant une boucle intensive en arrière-plan
- 📊 **Progression en temps réel** — ProgressBar horizontale mise à jour via `publishProgress()`
- 🔔 **Toast réactif** — Bouton Toast répondant immédiatement même pendant un traitement
- 🧵 **UI non bloquée** — Démonstration concrète de la fluidité avec Worker Thread
- 🔁 **Cycle de vie AsyncTask** — `onPreExecute`, `doInBackground`, `onProgressUpdate`, `onPostExecute`

---

## 🛠️ Stack technique

| Composant | Technologie |
|---|---|
| Langage | Java |
| UI | XML Layouts + LinearLayout |
| Threading | Thread + Runnable |
| Asynchrone | AsyncTask (pédagogique) |
| UI Update | Handler + Looper.getMainLooper() |
| Images | BitmapFactory + ImageView |

---

## 📁 Architecture du projet

```
com.example.labthreadsasynctask
├── MainActivity.java          # Activité principale + Thread + AsyncTask
└── res/
    └── layout/
        └── activity_main.xml  # Interface : TextView, ProgressBar, ImageView, Buttons
```

---

## 📦 Aucune dépendance externe

Ce lab utilise uniquement les APIs Android standard — aucune bibliothèque tierce requise.

```gradle
dependencies {
    implementation("androidx.appcompat:appcompat:1.6.1")
}
```

---

## 🔑 Concepts clés

```
UI Thread       → affiche l'écran, gère les clics, exécute onCreate()
Worker Thread   → calculs lourds, accès réseau, chargement long
Handler.post()  → revenir au UI thread depuis un Worker Thread
AsyncTask       → wrapper pédagogique gérant automatiquement les threads
```

---

## ⚠️ Règle fondamentale

```xml
<!-- Un Worker Thread ne peut JAMAIS modifier une View directement -->
<!-- Sinon : CalledFromWrongThreadException -->

<!-- Solution 1 -->
mainHandler.post(() -> img.setImageBitmap(bitmap));

<!-- Solution 2 -->
view.post(() -> textView.setText("résultat"));

<!-- Solution 3 -->
runOnUiThread(() -> progressBar.setProgress(50));
```

---

## 🎞️ Demo


https://github.com/user-attachments/assets/8fcdfae5-a45e-4826-8021-79c449d9b9ec


---

## 👨‍💻 Auteur

**Mourad EL OUATIK** | Réalisé dans le cadre d'un **Lab 8 Android** | Programmation Mobile.
