# PracticaMenus

Aplicación Android nativa desarrollada en **Kotlin** que demuestra la implementación de diferentes tipos de menús y navegación en Android. Este proyecto es una práctica educativa que incluye ejemplos de Toolbar, Navigation Drawer y Floating Action Buttons.

---

## 📋 Descripción del Proyecto

PracticaMenus es una aplicación Android que implementa patrones modernos de interfaz de usuario y navegación. El proyecto contiene dos actividades principales que muestran distintos enfoques para la navegación y presentación de menús:

### **MainActivity** - Toolbar con Menú Superior
Implementa un enfoque tradicional con:
- **Material Toolbar** en la parte superior
- **Menú de opciones** con iconos
- **Floating Action Button (FAB)** para acciones rápidas
- Respuesta táctil mediante Toast notifications

### **MainActivity2** - Navigation Drawer con Navegación por Fragmentos
Implementa un patrón moderno de navegación con:
- **Navigation Drawer** (menú lateral deslizable)
- **Fragmentos dinámicos** para diferentes secciones
- **Cabecera personalizada** en el drawer
- Navegación sin cambio de actividad

---

## 🏗️ Arquitectura del Proyecto

```
PracticaMenus/
├── app/
│   ├── src/main/
│   │   ├── java/com/example/practicamenus/
│   │   │   ├── MainActivity.kt              # Actividad con toolbar
│   │   │   ├── MainActivity2.kt             # Actividad con drawer
│   │   │   ├── fragmentClientes.kt          # Fragment de clientes
│   │   │   ├── fragmentProductos.kt         # Fragment de productos
│   │   │   └── fragmentProveedores.kt       # Fragment de proveedores
│   │   ├── res/
│   │   │   ├── layout/
│   │   │   │   ├── activity_main.xml        # Layout con toolbar
│   │   │   │   ├── activity_main2.xml       # Layout con drawer
│   │   │   │   ├── fragment_clientes.xml    # UI del fragment clientes
│   │   │   │   ├── fragment_productos.xml   # UI del fragment productos
│   │   │   │   ├── fragment_proveedores.xml # UI del fragment proveedores
│   │   │   │   └── ly_cabecera.xml          # Header del drawer
│   │   │   └── menu/
│   │   │       ├── menu1.xml                # Menú toolbar
│   │   │       └── menu2.xml                # Menú drawer
│   │   └── AndroidManifest.xml
│   └── build.gradle.kts
└── README.md
```

---

## ✨ Características Principales

### 1. **Menú Toolbar (MainActivity)**
- ✅ Material Design Toolbar
- ✅ Menú con 3 opciones: Nuevo, Buscar, Config
- ✅ Iconos personalizados
- ✅ Floating Action Button (FAB) para añadir elementos
- ✅ Feedback visual mediante Toast

### 2. **Navigation Drawer (MainActivity2)**
- ✅ Drawer navigation con gestos deslizables
- ✅ Header personalizado con imagen de usuario
- ✅ Navegación dinámica entre Fragments
- ✅ Menú principal con tres secciones:
  - 👥 Clientes
  - 📦 Productos
  - 🏭 Proveedores
- ✅ Submenu con opciones adicionales

### 3. **Fragmentos Reutilizables**
- ✅ Fragmentos para cada módulo (Clientes, Productos, Proveedores)
- ✅ Patrón Factory para instanciación
- ✅ Fácil extensión y personalización

---

## 🛠️ Tecnologías Utilizadas

| Tecnología | Versión | Uso |
|---|---|---|
| **Kotlin** | Latest | Lenguaje principal |
| **Android API** | 37+ | Versión mínima |
| **AndroidX** | Latest | Compatibilidad |
| **Material Design 3** | Latest | Componentes UI |
| **Fragment** | - | Navegación modular |
| **DrawerLayout** | - | Menú lateral |
| **CircleImageView** | Library | Imágenes circulares |

### Dependencias Principales
```gradle
- androidx.appcompat
- androidx.constraintlayout
- com.google.android.material
- de.hdodenhof:circleimageview
- androidx.activity.ktx
```

---

## 📱 Componentes Clave

### **Toolbar Menu (menu1.xml)**
Menú superior con las siguientes opciones:
- Nuevo (Add)
- Buscar (Search)
- Configuración (Settings)

### **Drawer Menu (menu2.xml)**
Menú lateral con:
- **Grupo principal** (checkeable):
  - Clientes
  - Productos
  - Proveedores
- **Grupo secundario**:
  - Opciones 1
  - Opciones 2

### **Navigation Header**
Cabecera personalizada que incluye:
- Imagen de fondo (navheader)
- Avatar circular del usuario
- Nombre del usuario (Mario Zambrano)

---

## 📸 Capturas de Pantalla

> Agrega aquí las capturas de pantalla de tu aplicación

### MainActivity
![MainActivity - Toolbar Menu](./screenshots/mainactivity.png)

### MainActivity2
![MainActivity2 - Navigation Drawer](./screenshots/mainactivity2.png)

### Drawer Abierto
![Drawer Navigation](./screenshots/drawer_open.png)

### Fragmentos
![Fragmentos](./screenshots/fragments.png)

---

## 🚀 Instalación y Uso

### Requisitos Previos
- Android Studio 2023.1 o superior
- SDK de Android 37 o superior
- Gradle 8.0+

### Instalación

1. **Clonar el repositorio**
   ```bash
   git clone https://github.com/Yukisan-uwo/PracticaMenus.git
   cd PracticaMenus
   ```

2. **Abrir en Android Studio**
   - File → Open → Selecciona la carpeta del proyecto

3. **Sincronizar Gradle**
   - Android Studio sincronizará automáticamente las dependencias

4. **Compilar y ejecutar**
   ```bash
   ./gradlew build
   ```

5. **Ejecutar en emulador o dispositivo físico**
   - Click en "Run" o presiona Shift + F10

---

## 💡 Funcionalidades Detalladas

### MainActivity - Enfoque Tradicional
```kotlin
// Manejo del menú de opciones
override fun onOptionsItemSelected(item: MenuItem): Boolean {
    return when (item.itemId) {
        R.id.mnuNuevo -> {
            Toast.makeText(this, "Click en Nuevo", Toast.LENGTH_LONG).show()
            true
        }
        R.id.mnuBuscar -> {
            Toast.makeText(this, "Click en Buscar", Toast.LENGTH_LONG).show()
            true
        }
        R.id.mnuConfig -> {
            Toast.makeText(this, "Click en Settings", Toast.LENGTH_LONG).show()
            true
        }
        else -> super.onOptionsItemSelected(item)
    }
}
```

### MainActivity2 - Navegación por Drawer
```kotlin
// Manejo de navegación de drawer
override fun onNavigationItemSelected(menuItem: MenuItem): Boolean {
    val fragment = when (menuItem.itemId) {
        R.id.menu_clientes -> fragmentClientes()
        R.id.menu_productos -> fragmentProductos()
        R.id.menu_proveedores -> fragmentProveedores()
        else -> null
    }
    fragment?.let {
        supportFragmentManager.beginTransaction()
            .replace(R.id.content_frame, it)
            .commit()
        menuItem.isChecked = true
        supportActionBar?.title = menuItem.title
    }
    drawerLayout.closeDrawers()
    return true
}
```

---

## 🎓 Conceptos Aprendidos

Este proyecto demuestra:
- ✅ Implementación de Toolbar y AppBar
- ✅ Creación de menús de opciones
- ✅ Floating Action Buttons
- ✅ Navigation Drawer pattern
- ✅ Fragment transactions
- ✅ Material Design components
- ✅ Event handling en Android
- ✅ Kotlin coroutines y lambdas

---

## 📝 Notas Importantes

- La aplicación utiliza **Kotlin** como lenguaje de programación principal
- Sigue el patrón **MVVM** (Model-View-ViewModel) de forma básica
- Compatible con **Material Design 3**
- Los fragmentos incluyen plantillas para futuras expansiones
- Soporta **Edge-to-Edge** layouts en dispositivos modernos

---

## 🔧 Configuración Gradle

```gradle kotlin dsl
android {
    namespace = "com.example.practicamenus"
    compileSdk = 37
    
    defaultConfig {
        applicationId = "com.example.practicamenus"
        minSdk = 37
        targetSdk = 37
        versionCode = 1
        versionName = "1.0"
    }
    
    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_11
        targetCompatibility = JavaVersion.VERSION_11
    }
}
```

---

## 🤝 Contribuciones

Si deseas mejorar este proyecto:
1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

---

## 📄 Licencia

Este proyecto es de código abierto y está disponible bajo la licencia MIT.

---

## 👨‍💻 Autor

**Yukisan-uwo**

- GitHub: [@Yukisan-uwo](https://github.com/Yukisan-uwo)
- Repositorio: [PracticaMenus](https://github.com/Yukisan-uwo/PracticaMenus)

---

## 📞 Soporte

Si tienes preguntas o encuentras problemas:
- Abre un **Issue** en el repositorio
- Revisa la documentación oficial de Android
- Consulta la documentación de Material Design

---

## 🎯 Mejoras Futuras

- [ ] Integrar base de datos local (SQLite/Room)
- [ ] Implementar MVVM con LiveData
- [ ] Agregar validación de formularios
- [ ] Implementar animaciones de transición
- [ ] Agregar persistencia de datos
- [ ] Implementar ViewModel y Repository patterns

---

**Última actualización:** 2026-06-16  
**Versión:** 1.0  
**Estado:** En desarrollo
