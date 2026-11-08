# Maqueta digital: el aparato digestivo

App web de la exposición de Sofía, Luz Martina, Camila, Zahira y María.

- `index.html`: la app completa (maqueta 3D, partes, juegos y desafío en vivo).
- `database.rules.json`: reglas de seguridad para Firebase Realtime Database.

## Cómo funciona

- **Link normal** (`https://.../`): lo abren todos con el QR. Siguen la exposición en vivo.
- **Link de presentadora** (`https://.../#presentar`): pide mail y clave. El que entra maneja la maqueta en todos los celulares.
- Si Firebase no está configurado, la app igual funciona en **modo libre** (cada uno la navega solo).

## 1. Firebase (unos 10 minutos)

1. Entrá a https://console.firebase.google.com y creá un proyecto (por ejemplo `maqueta-digestivo`). Podés desactivar Google Analytics.
2. **Realtime Database** → Crear base de datos → ubicación `us-central1` → "Comenzar en modo bloqueado".
3. **Authentication** → Comenzar → Método de acceso → activá **Correo electrónico/contraseña**.
4. Authentication → **Usuarios** → Agregar usuario: un mail y una clave para la presentadora. Copiá el **UID** que aparece.
5. Realtime Database → **Reglas**: pegá el contenido de `database.rules.json`, reemplazá `PEGAR_UID_DE_LA_PRESENTADORA` (aparece 3 veces) por el UID y tocá **Publicar**.
6. ⚙️ Configuración del proyecto → **Tus apps** → ícono web `</>` → registrá la app (sin Hosting). Copiá los valores de `firebaseConfig`.
7. En `index.html`, arriba de todo en el `<script>`, reemplazá los `PEGAR...` de `FIREBASE_CONFIG` con esos valores. Asegurate de que esté `databaseURL`.

## 2. GitHub Pages

1. En GitHub creá un repositorio **público** llamado `maqueta-digestivo`.
2. Subí `index.html` (Add file → Upload files → Commit).
3. Settings → **Pages** → Source: "Deploy from a branch" → Branch `main` / `(root)` → Save.
4. En 1 o 2 minutos queda en: `https://TU-USUARIO.github.io/maqueta-digestivo/`

## 3. Probar antes de la exposición

1. En la compu abrí `.../maqueta-digestivo/#presentar` y entrá con el mail y la clave.
2. En un celular abrí `.../maqueta-digestivo/` (sin login).
3. Pasá de parte en la compu: el celular tiene que moverse y arriba decir **🔴 EN VIVO**.
4. Probá el desafío: respondé en el celular y mirá que en la compu sube el contador.

## Nota de seguridad

La `apiKey` de Firebase no es secreta, puede estar en la página. Lo que protege el control son las reglas: solo el usuario presentadora puede cambiar la exposición. Los demás solo pueden marcar que están conectados y responder el desafío.
