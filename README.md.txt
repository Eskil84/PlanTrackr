# 📋 PlanTrackr

**PlanTrackr** egy egyszerű, felhőalapú tervkezelő alkalmazás, amely lehetővé teszi terveid nyomon követését, szerkesztését és fájlok csatolását bármilyen formátumban.  
Az alkalmazás Firebase-re épül, és GitHub Pages-en futtatható.

## ✨ Fő funkciók

- 🔐 Google-alapú bejelentkezés
- 🌗 Világos / sötét mód váltása egyetlen ikon segítségével
- 📂 Tervlista megjelenítése jobb oldali oszlopban
- 📝 Terv részleteinek megtekintése
- 📎 Fájl feltöltés tetszőleges formátumban (pl. .pdf, .jpg, .zip stb.)
- ☁ Firebase Firestore és Storage integráció

## 🚀 Használat

1. **Nyisd meg az alkalmazást a GitHub Pages-en**  
   `https://<felhasznalonev>.github.io/<repo-nev>/`

2. **Jelentkezz be Google-fiókoddal**

3. **Válassz ki egy tervet** a jobb oldali listából

4. **Tekintsd meg a részleteket**, vagy tölts fel hozzá fájlokat

## ⚙ Telepítés saját célra

1. Készíts egy új GitHub repót (pl. `plantrackr`)
2. Töltsd fel a `index.html` és `README.md` fájlokat
3. A repó **Settings > Pages** részében válaszd ki a forrást:  
   ➜ `main` branch, `/ (root)`
4. Néhány másodperc múlva elérhető lesz az app

## 🛡 Firebase beállítások

Győződj meg róla, hogy a Firebase projektedben:

- Engedélyezve van a Google bejelentkezés
- A Firestore és Storage engedélyek be vannak állítva a következőképp:

```js
// Firestore szabály (egyszerű példa)
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth.uid == userId;
    }
  }
}

// Storage szabály
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /uploads/{userId}/{allPaths=**} {
      allow read, write: if request.auth.uid == userId;
    }
  }
}
