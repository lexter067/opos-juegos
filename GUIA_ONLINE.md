# Poner la web ONLINE (clasificación con Judith + app instalable)

## A) Conseguir tu `firebaseConfig` (5 min)
El `firebaseConfig` NO sale de la base de datos: sale de **registrar una app Web** en tu proyecto.

1. Entra en **https://console.firebase.google.com** y abre tu proyecto.
2. Arriba a la izquierda, pulsa el **engranaje ⚙** (junto a "Descripción general") → **Configuración del proyecto**.
3. Baja hasta **"Tus aplicaciones"**.
   - Si NO ves ninguna app web: pulsa el icono **`</>`** (Web), ponle un apodo (ej. "juegos"),
     **NO** hace falta marcar Hosting → **Registrar app**.
4. Aparece un bloque tipo:
   ```js
   const firebaseConfig = {
     apiKey: "AIza......",
     authDomain: "tuproyecto.firebaseapp.com",
     projectId: "tuproyecto",
     storageBucket: "tuproyecto.appspot.com",
     messagingSenderId: "1234567890",
     appId: "1:1234:web:abcd...."
   };
   ```
5. Copia esos 6 valores y pégalos en **`firebase-config.js`** (entre las comillas).
   *(Si solo quieres, pégame aquí el bloque y te lo dejo puesto yo.)*

### Reglas de Firestore (para que se pueda leer/escribir el ranking)
En la consola: **Firestore Database → Reglas** y pega esto → **Publicar**:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /scores/{doc} {
      allow read: if true;
      allow create: if true;
      allow update, delete: if false;
    }
    match /duels/{doc} {
      allow read, create, update: if true;
      allow delete: if false;
    }
  }
}
```
Permite ver el ranking y enviar puntuaciones (sin borrar/editar las de otros) y jugar duelos en directo. Sin contraseñas.

> Cuando `firebase-config.js` tenga tu config, en la web aparecerán activos **Reto diario** y **Clasificación**.

## B) Subir como app instalable (GitHub Pages, con GitHub Desktop)
1. En **GitHub Desktop**: *File → New repository* (ej. nombre `opos-juegos`, elige una carpeta local).
2. Copia **todos** los archivos de `Estudio/_Web` dentro de la carpeta de ese repositorio
   (`index.html`, `datos.js`, `contenido.js`, `firebase-config.js`, `sw.js`, `manifest.json`, `icon-192.png`, `icon-512.png`).
3. En GitHub Desktop: escribe un resumen y **Commit to main** → **Publish repository** (déjalo **público**).
4. En **github.com** → tu repo → **Settings → Pages** → en *Source* elige **main** y carpeta **/ (root)** → **Save**.
5. A los ~1-2 min tendrás la URL: `https://TU_USUARIO.github.io/opos-juegos/`
   - Ábrela en el móvil → menú del navegador → **Instalar app / Añadir a pantalla de inicio**.
   - Pásale la URL a Judith para que compita.

⚠️ GitHub Pages es **público**: cualquiera con la URL exacta puede verlo (aunque no esté indexado).
Si prefieres no publicar el temario, usa la web en **local** y comparte el resultado por captura.

## Actualizar después
Si regeneras datos (`build_web_data.py` / `build_contenido.py`), vuelve a copiar los `.js` al repo y
haz commit+push en GitHub Desktop. La web usa **network-first**: al recargar online ya coge la versión nueva.
