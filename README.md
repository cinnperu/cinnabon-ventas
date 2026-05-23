# 🥐 Cinnabon Ventas - Sistema de Gestión

Sistema web completo para gestión de ventas y transacciones de Cinnabon Perú.

## Características

✅ **Autenticación Real** - Registro, login y aprobación de usuarios
✅ **3 Roles** - Admin, Jefa Zonal, Gerente de Tienda
✅ **Sistema de Aprobación** - Admin aprueba nuevos usuarios
✅ **Gestión de Zonas** - Admin puede crear y eliminar zonas
✅ **Gestión de Tiendas** - Admin asigna tiendas a zonas
✅ **Carga de Ventas** - Registro diario de ventas y transacciones
✅ **Dashboard** - Visualización de datos en tiempo real
✅ **Acceso Limitado** - Cada usuario ve solo sus datos

## Estructura

```
cinnabon-ventas/
├── index.html          (App principal)
├── package.json        (Dependencias)
├── README.md           (Este archivo)
├── .gitignore          (Archivos ignorados)
└── vercel.json         (Configuración Vercel)
```

## Tecnologías

- **Frontend**: HTML5, CSS3, JavaScript Vanilla
- **Backend**: Firebase (Firestore, Authentication)
- **Hosting**: Vercel
- **Versionamiento**: GitHub

## Instalación Local

1. **Clona el repositorio**
```bash
git clone https://github.com/tu-usuario/cinnabon-ventas.git
cd cinnabon-ventas
```

2. **Abre index.html en tu navegador**
```bash
# Opción 1: Abre directamente
open index.html

# Opción 2: Con servidor local (requiere Node.js)
npx http-server
# Luego ve a http://localhost:8080
```

## Configuración Firebase

La app ya tiene Firebase configurado. El proyecto Firebase es:
- **Project ID**: cinnabon-ventas
- **Database**: Firestore
- **Auth**: Email/Contraseña

### Primera vez en Firebase:

1. Ve a la consola de Firestore
2. Crea las colecciones:
   - `users` - Información de usuarios
   - `sales` - Registro de ventas
   - `zones` - Zonas (creadas por admin)
   - `stores` - Tiendas (creadas por admin)

## Cómo Usar

### Para Gerentes/Jefas Zonales:

1. **Crear Cuenta**
   - Selecciona tu rol (Jefa Zonal o Gerente)
   - Completa los datos
   - Espera aprobación del admin

2. **Registrar Ventas**
   - Ve a "Registrar Ventas"
   - Ingresa fecha, monto y concepto
   - La venta se guarda en Firestore

3. **Ver Dashboard**
   - Total de ventas del mes
   - Transacciones recientes
   - Ticket promedio

### Para Admin (Tu usuario):

1. **Aprobar Usuarios**
   - Ve a "Usuarios Pendientes"
   - Revisa solicitudes
   - Aprueba o rechaza

2. **Crear Zonas**
   - Ve a "Gestionar Zonas"
   - Ingresa el nombre (ej: Lima Norte)
   - Se crea la zona automáticamente

3. **Crear Tiendas**
   - Ve a "Gestionar Tiendas"
   - Selecciona zona
   - Ingresa nombre de tienda
   - Se asigna automáticamente a la zona

## Flujo de Usuario

### Registro:
1. Usuario se registra (pendiente)
2. Admin ve en "Usuarios Pendientes"
3. Admin aprueba
4. Usuario accede a la app

### Rol Zonal:
- Ve solo su zona
- Ve todas sus tiendas en esa zona
- Registra ventas de su zona

### Rol Manager:
- Ve solo su tienda
- Registra ventas de su tienda
- Visualiza datos de su tienda

### Rol Admin:
- Ve todo
- Aprueba usuarios
- Crea zonas y tiendas
- Dashboard de toda la empresa

## Deployment en Vercel

1. **Sube a GitHub**
```bash
git add .
git commit -m "Initial commit"
git push origin main
```

2. **Conecta a Vercel**
   - Ve a vercel.com
   - Importa tu repo de GitHub
   - Vercel detecta automáticamente
   - Click "Deploy"

3. **¡Listo!**
   - Tu app estará en vivo en: `https://cinnabon-ventas.vercel.app`

## Variables de Entorno

Estas credenciales Firebase están hardcodeadas en `index.html` (seguro para este proyecto).

Si quieres usar `.env`, crea:
```
VITE_FIREBASE_API_KEY=AIzaSyDSCj_IukZemj9uniAlxuZvO5-r4JloPzU
VITE_FIREBASE_PROJECT_ID=cinnabon-ventas
...
```

## Estructura de Datos Firestore

### Collection: users
```javascript
{
  name: "Juan García",
  email: "juan@cinnabon.pe",
  role: "zonal|manager|admin",
  zone: "Lima Norte", // si es zonal
  store: "doc_id", // si es manager
  status: "pending|approved|rejected",
  approved: true|false,
  createdAt: timestamp,
  approvedAt: timestamp
}
```

### Collection: sales
```javascript
{
  userId: "uid",
  userName: "Juan García",
  zone: "Lima Norte",
  store: "doc_id",
  date: timestamp,
  amount: 450.00,
  description: "Venta de cinnabons",
  createdAt: timestamp
}
```

### Collection: zones
```javascript
{
  name: "Lima Norte",
  storeCount: 7,
  createdAt: timestamp
}
```

### Collection: stores
```javascript
{
  zone: "Lima Norte",
  name: "Barbershop Centro",
  createdAt: timestamp
}
```

## Cuentas Demo

Una vez aprobado por admin, todos los usuarios pueden acceder. Para testing:

**Admin (tú):**
- Email: admin@cinnabon.pe
- Contraseña: admin123456
- Rol: admin

Crea este usuario manualmente en Firebase o a través de la app de registro.

## Soporte y Mejoras Futuras

- [ ] Reportes en PDF
- [ ] Gráficos avanzados
- [ ] Exportar a Excel
- [ ] Notificaciones en tiempo real
- [ ] Móvil app nativa
- [ ] Sistema de comisiones
- [ ] Integración con POS

## Licencia

MIT - Libre para usar y modificar

---

**¿Preguntas?** Contacta al equipo de desarrollo.

Versión: 1.0.0
Última actualización: Mayo 2024
