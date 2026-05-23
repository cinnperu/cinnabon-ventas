# 📚 GUÍA PASO A PASO: GitHub → Vercel

## PARTE 1: SUBIR A GITHUB

### Paso 1: Crea un repositorio nuevo en GitHub

1. Ve a **github.com**
2. Haz login con tu cuenta
3. Click en **"+"** (arriba a la derecha)
4. Selecciona **"New repository"**
5. **Nombre**: `cinnabon-ventas`
6. **Descripción**: "Sistema de Gestión de Ventas Cinnabon Perú"
7. **Público** (selecciona esto)
8. Click **"Create repository"**

### Paso 2: Descarga los archivos

Ya tienes los archivos listos:
- `index.html` ← La app principal
- `package.json`
- `vercel.json`
- `README.md`
- `.gitignore`

Descárgalos todos de la carpeta "Outputs" de este chat.

### Paso 3: Crea una carpeta local

1. En tu PC, crea una carpeta: `C:\Users\[TuUsuario]\cinnabon-ventas`
2. Copia todos los archivos allí

### Paso 4: Inicializa Git (en tu carpeta)

**Opción A: Con Git Bash o Terminal**

```bash
cd C:\Users\[TuUsuario]\cinnabon-ventas
git init
git add .
git commit -m "Initial commit - Cinnabon Ventas v1.0"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/cinnabon-ventas.git
git push -u origin main
```

**Opción B: Sin terminal (GitHub Desktop)**

1. Descarga **GitHub Desktop** (https://desktop.github.com)
2. Abre GitHub Desktop
3. Click **"Create a New Repository"**
4. **Name**: `cinnabon-ventas`
5. **Local Path**: `C:\Users\[TuUsuario]\cinnabon-ventas`
6. Click **"Create Repository"**
7. Copia los archivos a esa carpeta
8. En GitHub Desktop:
   - Click **"Commit to main"** (con todos los archivos)
   - Click **"Publish repository"** (elige público)
   - ¡Listo!

---

## PARTE 2: SUBIR A VERCEL

### Paso 1: Ve a Vercel

1. Abre **vercel.com**
2. Haz login (si no tienes cuenta, créala gratis)

### Paso 2: Importa desde GitHub

1. Click **"Add New..."**
2. Selecciona **"Project"**
3. Click **"Continue with GitHub"**
4. Busca tu repo `cinnabon-ventas`
5. Click **"Import"**

### Paso 3: Configuración (automático)

Vercel detectará automáticamente:
- Framework: Static
- Build: Ninguno (es HTML puro)
- Output: Root directory

Solo dale click a **"Deploy"**

### Paso 4: ¡Espera!

- Vercel procesa (2-3 minutos)
- Verás barra de progreso
- Cuando termine: **"Deployment successful"**

### Paso 5: Tu app está en vivo

Te dará una URL como:
```
https://cinnabon-ventas.vercel.app
```

¡Esa es tu app en producción!

---

## PARTE 3: PRIMEROS PASOS EN LA APP

### Crear tu usuario ADMIN

1. Abre tu URL: `https://cinnabon-ventas.vercel.app`
2. Click **"Crear Cuenta"**
3. Llena:
   - Nombre: `Tu Nombre`
   - Email: `admin@cinnabon.pe`
   - Contraseña: `admin123456`
   - Rol: **Selecciona "Jefa Zonal" o "Gerente de Tienda"** (por ahora)
4. Click **"Crear Cuenta"**
5. **Espera a que te apruebe** (necesitas otra cuenta admin en Firebase)

### Crear admin desde Firebase

1. Ve a **firebase.google.com → Console**
2. Selecciona tu proyecto `cinnabon-ventas`
3. Ve a **Firestore**
4. Crea colección **`users`**
5. Añade un documento con esto:

```javascript
{
  name: "Tu Nombre",
  email: "admin@cinnabon.pe",
  role: "admin",
  zone: null,
  store: null,
  status: "approved",
  approved: true,
  createdAt: (timestamp ahora),
  approvedAt: (timestamp ahora)
}
```

Luego en Firebase Auth:
1. Ve a **Authentication**
2. Click **"Add user"** (icono + arriba)
3. Email: `admin@cinnabon.pe`
4. Contraseña: `admin123456`
5. Click **"Add user"**

Ahora podrás loguear como admin.

### Primera vez como ADMIN

1. Crea 4 zonas:
   - Lima Norte
   - Lima Centro
   - Lima Este
   - Lima Sur

2. Crea ~28 tiendas (7 por zona):
   - Lima Norte - Barbershop Centro
   - Lima Norte - Barbershop Norte
   - ... etc

3. Comparte el link con tu equipo:
   ```
   https://cinnabon-ventas.vercel.app
   ```

4. Ellos se registran
5. Tú los apruebas en "Usuarios Pendientes"
6. ¡Empiezan a registrar ventas!

---

## SOLUCIÓN DE PROBLEMAS

### "Connection refused" o "Firebase not found"
- Verifica que el projectId sea `cinnabon-ventas`
- Revisa que Firestore esté habilitado

### "No puedo registrar ventas"
- ¿Tu usuario está aprobado?
- Ve a Firebase → Firestore → users
- Verifica que tu usuario tenga `approved: true`

### "¿Cómo cambio datos después de Vercel?"
- Haz cambios en `index.html`
- `git add .`
- `git commit -m "Descripción"`
- `git push`
- Vercel redeploy automático (~1 min)

### "Quiero más usuarios"
- Firebase Auth permite usuarios ilimitados en plan gratis
- Firestore: 1 GB gratis

---

## CHECKLIST FINAL

✅ Descargaste los archivos
✅ Creaste repo en GitHub
✅ Subiste archivos a GitHub
✅ Conectaste Vercel con GitHub
✅ Tu app está en vivo
✅ Creaste colecciones en Firestore
✅ Creaste usuario ADMIN
✅ Probaste registrar una venta
✅ ¡Lista para compartir con tu equipo!

---

## LINKS IMPORTANTES

- **Tu app**: https://cinnabon-ventas.vercel.app
- **GitHub repo**: https://github.com/TU_USUARIO/cinnabon-ventas
- **Vercel dashboard**: https://vercel.com/dashboard
- **Firebase console**: https://console.firebase.google.com/project/cinnabon-ventas

---

## ¿PREGUNTAS?

Si algo no funciona:
1. Verifica que Firestore esté activo
2. Verifica que Authentication esté activo
3. Revisa la consola (F12) para errores
4. Contacta al equipo de desarrollo

¡**Éxito!** 🚀
