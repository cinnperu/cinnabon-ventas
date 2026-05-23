# ⚡ GUÍA RÁPIDA - FLUJO CORRECTO

## 🎯 FLUJO DE REGISTRO

### 1. Usuario se registra (SIN elegir rol)
```
Nombre completo
Email
Contraseña
→ Cuenta PENDIENTE
```

### 2. Admin ve en "Usuarios Pendientes"
- Email
- Nombre
- Status: Pendiente

### 3. Admin hace click "Asignar Rol"
- Selecciona rol (Admin, Jefa Zonal, Gerente Tienda)
- Si es Jefa Zonal → selecciona su ZONA
- Si es Gerente → selecciona su TIENDA
- Click "Asignar y Aprobar"

### 4. Usuario ya puede acceder

---

## 📋 ROLES Y PERMISOS

### 👑 **ADMINISTRADOR**
✅ Ver todo
✅ Aprobar usuarios
✅ Crear zonas
✅ Crear tiendas
✅ Asignar roles a usuarios
✅ Ver todas las ventas

### 🗺️ **JEFA ZONAL**
✅ Ver su zona
✅ Ver sus tiendas (en su zona)
✅ Registrar ventas de su zona
✅ Dashboard de su zona
❌ No aprueba usuarios
❌ No crea zonas/tiendas

### 🏪 **GERENTE DE TIENDA**
✅ Ver solo su tienda
✅ Registrar ventas de su tienda
✅ Dashboard de su tienda
❌ No ve otras tiendas
❌ No aprueba usuarios

---

## 🚀 PASOS INICIALES

### 1. Crear cuenta ADMIN en Firebase (primero)

Ve a **Firebase Console → Authentication**

1. Click "Create user"
2. Email: `admin@cinnabon.pe`
3. Password: `admin123456`

Luego ve a **Firestore → users**

Crea documento manualmente:
```javascript
{
  name: "Tu Nombre",
  email: "admin@cinnabon.pe",
  role: "admin",
  zone: null,
  store: null,
  status: "approved",
  approved: true,
  createdAt: (ahora),
  approvedAt: (ahora)
}
```

### 2. Loguea como ADMIN

1. Abre tu app: `https://cinnabon-ventas.vercel.app`
2. "Iniciar Sesión"
3. Email: `admin@cinnabon.pe`
4. Contraseña: `admin123456`

### 3. Crea 4 Zonas

Ve a "🗺️ Gestionar Zonas"

Crea:
- Lima Norte
- Lima Centro
- Lima Este
- Lima Sur

### 4. Crea ~28 Tiendas

Ve a "🏪 Gestionar Tiendas"

Para cada zona (7 tiendas mínimo):
- Zona: Lima Norte
- Tienda: Barbershop Centro
- Tienda: Barbershop Norte
- Tienda: Ice Cream Plaza
- ... etc

### 5. Invita a tu equipo

- Comparte: `https://cinnabon-ventas.vercel.app`
- Ellos hacen "Crear Cuenta"
- Tú los ves en "⏳ Usuarios Pendientes"
- Asignas rol + zona/tienda
- ¡Aprueban!

---

## 💡 EJEMPLO: APROBAR A JEFA ZONAL

1. Usuario "María" se registra
2. Tú ves en "Usuarios Pendientes"
3. Click "Asignar Rol"
4. Rol: Jefa Zonal
5. Zona: Lima Norte (se muestra, seleccionas)
6. Click "Asignar y Aprobar"
7. María ya puede acceder
8. María ve solo Lima Norte y sus tiendas

---

## 💡 EJEMPLO: APROBAR A GERENTE

1. Usuario "Carlos" se registra
2. Tú ves en "Usuarios Pendientes"
3. Click "Asignar Rol"
4. Rol: Gerente de Tienda
5. Tienda: "Lima Norte - Barbershop Centro" (se muestra, seleccionas)
6. Click "Asignar y Aprobar"
7. Carlos ya puede acceder
8. Carlos ve solo su tienda: Barbershop Centro

---

## ✅ CHECKLIST

- [ ] Cuentacreada ADMIN en Firebase Auth
- [ ] Documento ADMIN en Firestore users
- [ ] Logueaste como ADMIN
- [ ] Creaste 4 zonas
- [ ] Creaste ~28 tiendas
- [ ] Invitaste a 1 usuario de prueba
- [ ] Lo aprobaste como Jefa Zonal
- [ ] Ese usuario puede registrar ventas
- [ ] Dashboard funciona

---

## 🐛 SOLUCIÓN DE PROBLEMAS

**"No puedo registrarme"**
- ¿Está Firestore habilitado?
- ¿La app ve Firebase?

**"Creo usuario pero no veo en Usuarios Pendientes"**
- Refresca la página
- Verifica que esté en colección `users`

**"Al asignar rol sale error"**
- ¿Seleccionaste zona/tienda?
- ¿Existe esa zona/tienda?

**"Usuario no puede registrar ventas"**
- ¿Está aprobado? (status: approved)
- ¿Tiene rol asignado? (role: admin/zonal/manager)

---

¡**Éxito!** 🎉
