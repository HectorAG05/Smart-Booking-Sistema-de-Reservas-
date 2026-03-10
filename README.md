# 📅 Smart-Booking: Sistema de Reservas Inteligente para WordPress

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![WordPress](https://img.shields.io/badge/WordPress-5.0%2B-blue.svg)](https://wordpress.org/)
[![PHP](https://img.shields.io/badge/PHP-8.0%2B-purple.svg)](https://www.php.net/)
[![Version](https://img.shields.io/badge/Version-1.0.0-green.svg)](https://github.com/hectorgeorge/smart-booking-wp/releases)

**Smart-Booking** es un plugin profesional de WordPress que revoluciona la gestión de turnos y reservas para servicios profesionales. Elimina el overbooking mediante validación en tiempo real, integra un calendario interactivo y envía confirmaciones automáticas por WhatsApp.

---
---

## 👨‍💻 Autores
Este proyecto fue desarrollado en colaboración por:
* **Hector George**: Arquitectura de Software
* **Stefania Medina**: Diseño de Interfaz (UI), Experiencia de Usuario (UX) 
* **Donald Rodriguez**: Lider de proyecto

---

## 🎯 Características Principales

### ✨ Para Clientes
- 📅 **Calendario interactivo** con FullCalendar.js
- 🎯 **Formulario de reservas en 3 pasos** intuitivo
- ⏱️ **Slots dinámicos** según duración del servicio
- 📱 **Interfaz 100% responsive** (mobile-first)
- 🔔 **Confirmación automática por WhatsApp**
- ✅ **Validación en cliente** (nombre, teléfono, fecha)

### 🛠️ Para Administradores
- 📊 **Dashboard completo** en wp-admin
- 📈 **Estadísticas en tiempo real** (confirmados, pendientes, cancelados)
- 🎛️ **Acciones rápidas** (confirmar, cancelar, reactivar)
- 🔗 **Enlaces directos a WhatsApp** para contactar clientes
- 📅 **Filtro por fecha** para ver turnos de cualquier día
- 🗓️ **Calendario mensual** con vista de eventos

### 🔒 Técnicas
- 🛡️ **Anti-overbooking garantizado** (validación de servidor)
- 🔐 **Seguridad robusta** (consultas preparadas, sanitización, nonces)
- 🚀 **REST API completa** (endpoints para CRUD)
- 📦 **Arquitectura MVC** (separación clara de responsabilidades)
- 💾 **Base de datos optimizada** (índices en columnas críticas)
- 🌍 **Preparado para multiidioma**

---

## 📋 Requisitos

| Requisito | Versión Mínima |
|-----------|-----------------|
| WordPress | 5.0+ |
| PHP | 8.0+ |
| MySQL | 5.7+ |
| Navegador | Chrome, Firefox, Safari, Edge (últimas 2 versiones) |

### Dependencias Externas (CDN)
- FullCalendar.js v6.1.11
- Tailwind CSS v4
- (Opcional) WhatsApp Business API de Meta

---

## 🚀 Instalación Rápida

### Opción 1: Instalación Estándar (Recomendado)

1. **Descargar el plugin**
   ```bash
   # Descarga smart-booking-v1.zip desde la sección de Releases
   ```

2. **Instalar en WordPress**
   - Ve a **Plugins > Añadir nuevo**
   - Haz clic en **Subir plugin**
   - Selecciona `smart-booking-v1.zip`
   - Haz clic en **Instalar ahora** → **Activar**

3. **Configurar**
   - Ve a **Smart Booking > Configuración**
   - Completa el **Nombre del Negocio**
   - (Opcional) Añade credenciales de WhatsApp

4. **Usar el Plugin**
   - Crea una página nueva
   - Pega el shortcode: `[smart_booking]`
   - ¡Listo! Los clientes pueden reservar

### Opción 2: Instalación Manual

```bash
# 1. Descargar y extraer
unzip smart-booking-v1.zip

# 2. Subir a WordPress
cp -r smart-booking /ruta/a/wordpress/wp-content/plugins/

# 3. Activar en WordPress wp-admin
```

### Opción 3: Instalación desde Git

```bash
cd /ruta/a/wordpress/wp-content/plugins/
git clone https://github.com/hectorgeorge/smart-booking-wp.git smart-booking
# Luego activar en WordPress wp-admin
```

---

## 📖 Guía de Uso

### Para Usuarios Finales

#### Paso 1: Acceder al Formulario
1. Abre la página donde instalaste el shortcode `[smart_booking]`
2. Verás un formulario de reservas en 4 pasos

#### Paso 2: Seleccionar Servicio
- Elige el tipo de servicio (Consulta Médica, Fisioterapia, etc.)
- El sistema muestra la duración del servicio

#### Paso 3: Elegir Fecha y Horario
- Selecciona una fecha en el calendario
- Verás los horarios disponibles (verdes) y ocupados (grises)
- Haz clic en un horario disponible

#### Paso 4: Completar Datos
- Ingresa tu nombre completo
- Ingresa tu número de WhatsApp (con código de país)
- Haz clic en **Confirmar Reserva**

#### Paso 5: Confirmación
- Recibirás un número de reserva
- Se enviará un mensaje de confirmación por WhatsApp
- ¡Tu turno está reservado!

### Para Administradores

#### Acceder al Dashboard
1. Ve a **Smart Booking > Turnos del Día** en wp-admin
2. Verás una tabla con todas las reservas del día

#### Gestionar Turnos
- **Confirmar**: Envía notificación por WhatsApp
- **Cancelar**: Marca como cancelado
- **Filtrar**: Por fecha usando el selector

#### Ver Estadísticas
- Total de turnos del día
- Turnos confirmados
- Turnos pendientes
- Turnos cancelados

#### Configurar el Plugin
1. Ve a **Smart Booking > Configuración**
2. Completa los datos:
   - **Nombre del Negocio**: Tu empresa
   - **Token de WhatsApp**: (Opcional) Token de Meta
   - **Número de WhatsApp**: (Opcional) Número del negocio

---

## 🏗️ Estructura del Proyecto

```
smart-booking-wp/
├── smart-booking/                      # Plugin WordPress
│   ├── model/
│   │   ├── class-sb-database.php      # Acceso a BD (CRUD)
│   │   └── class-sb-booking.php       # Lógica de negocio
│   ├── controller/
│   │   ├── class-sb-rest-controller.php    # REST API
│   │   ├── class-sb-admin-controller.php   # Panel admin
│   │   └── class-sb-whatsapp.php          # WhatsApp
│   ├── view/
│   │   ├── booking-form.php           # Formulario
│   │   ├── admin-dashboard.php        # Dashboard
│   │   ├── admin-settings.php         # Configuración
│   │   └── class-sb-shortcode.php     # Shortcode
│   ├── assets/
│   │   ├── css/
│   │   │   ├── frontend.css
│   │   │   └── admin.css
│   │   └── js/
│   │       ├── frontend.js
│   │       └── admin.js
│   ├── smart-booking.php              # Archivo principal
│   └── uninstall.php                  # Desinstalación
│
├── smart-booking-demo/                 # Landing Page
│   ├── client/
│   │   ├── src/
│   │   │   ├── pages/
│   │   │   ├── components/
│   │   │   └── App.tsx
│   │   └── index.html
│   ├── server/
│   ├── package.json
│   └── README.md
│
├── README.md                           # Este archivo
├── DOCUMENTACION_TECNICA.md            # Documentación técnica
├── AUTHORS.md                          # Información de autores
├── CONTRIBUTING.md                     # Guía para contribuyentes
├── LICENSE                             # Licencia MIT
└── .gitignore                          # Archivos a ignorar
```

---

## 🔌 API REST

### Endpoints Disponibles

#### 1. Crear Reserva
```http
POST /wp-json/smart-booking/v1/bookings
Content-Type: application/json

{
  "user_name": "María García",
  "service_type": "consulta_medica",
  "booking_date": "2026-03-15",
  "start_time": "10:00",
  "whatsapp_phone": "5491112345678"
}
```

**Respuesta (201 Created)**
```json
{
  "success": true,
  "booking_id": 42,
  "message": "¡Turno reservado con éxito!",
  "end_time": "10:30"
}
```

#### 2. Obtener Eventos (Calendario)
```http
GET /wp-json/smart-booking/v1/bookings?start=2026-03-01&end=2026-03-31
```

**Respuesta (200 OK)**
```json
[
  {
    "id": 1,
    "title": "Consulta Médica – Juan Pérez",
    "start": "2026-03-15T10:00:00",
    "end": "2026-03-15T10:30:00",
    "color": "#10b981",
    "extendedProps": {
      "status": "confirmado",
      "service": "Consulta Médica",
      "user": "Juan Pérez"
    }
  }
]
```

#### 3. Obtener Slots Disponibles
```http
GET /wp-json/smart-booking/v1/slots?date=2026-03-15&service_type=consulta_medica
```

**Respuesta (200 OK)**
```json
{
  "success": true,
  "slots": [
    {
      "start": "09:00",
      "end": "09:30",
      "available": true
    },
    {
      "start": "09:30",
      "end": "10:00",
      "available": false
    }
  ]
}
```

#### 4. Actualizar Estado (Solo Admin)
```http
PATCH /wp-json/smart-booking/v1/bookings/42
Content-Type: application/json

{
  "status": "confirmado"
}
```

---

## ⚙️ Configuración

### Personalizar Servicios

Edita `smart-booking/model/class-sb-booking.php`:

```php
public const SERVICES = [
    'consulta_medica' => [
        'label' => 'Consulta Médica',
        'duration' => 30  // minutos
    ],
    'fisioterapia' => [
        'label' => 'Fisioterapia',
        'duration' => 60
    ],
    // Añade más servicios aquí
];
```

### Personalizar Horario

Edita las constantes en el mismo archivo:

```php
public const OPEN_HOUR  = 8;   // 08:00
public const CLOSE_HOUR = 20;  // 20:00
```

### Configurar WhatsApp

**Opción 1: API de Meta (Automático)**
1. Ve a **Smart Booking > Configuración**
2. Añade tu Token de acceso de Meta
3. Añade tu Número de teléfono del negocio
4. Los mensajes se enviarán automáticamente

**Opción 2: URL Masking (Manual)**
1. Deja los campos de WhatsApp vacíos
2. En el dashboard, verás enlaces wa.me
3. Haz clic para enviar mensajes manualmente

---

## 🧪 Probar el Plugin Localmente

### Con LocalWP (Recomendado)

```bash
# 1. Descargar LocalWP desde localwp.com
# 2. Crear un sitio WordPress local
# 3. Descargar smart-booking-v1.zip
# 4. Instalar en Plugins > Añadir nuevo
# 5. Activar y configurar
```

### Con XAMPP

```bash
# 1. Descargar XAMPP
# 2. Instalar WordPress en htdocs/
# 3. Copiar plugin a wp-content/plugins/
# 4. Activar en wp-admin
```

### Con Docker

```bash
# Crear docker-compose.yml con WordPress + MySQL
docker-compose up -d

# Acceder a http://localhost:8000
# Instalar plugin como de costumbre
```

---

## 🐛 Solución de Problemas

### El plugin no aparece en el menú
- ✅ Verifica que esté **activado** en Plugins
- ✅ Recarga la página (Ctrl+F5)
- ✅ Comprueba que tienes permisos de administrador

### El shortcode no muestra nada
- ✅ Verifica que copiaste: `[smart_booking]`
- ✅ Asegúrate de que el plugin está activado
- ✅ Abre la consola (F12) y busca errores

### No puedo crear reservas
- ✅ Verifica que la fecha sea hoy o en el futuro
- ✅ Comprueba que el horario esté dentro del rango permitido
- ✅ Intenta con otro servicio

### El calendario no carga
- ✅ Abre la consola (F12) y busca errores
- ✅ Verifica que FullCalendar se carga desde CDN
- ✅ Desactiva extensiones del navegador que bloqueen scripts

### WhatsApp no envía mensajes
- ✅ Verifica que el número tiene código de país correcto
- ✅ Si usas API, comprueba que el token es válido
- ✅ Si usas URL masking, haz clic en el enlace wa.me

---

## 🎨 Landing Page Demo

La carpeta `smart-booking-demo/` contiene una Landing Page profesional para presentar el plugin.

### Instalar la Demo Localmente

```bash
cd smart-booking-demo
pnpm install
pnpm dev

# Accede a http://localhost:3000
```

### Características de la Demo

- 🎯 Hero section impactante
- ✨ Sección de características
- 🎬 Demo interactivo del formulario
- ❓ FAQ con preguntas frecuentes
- 📞 Sección de contacto
- 🎨 Diseño moderno con Tailwind CSS

---

## 📚 Documentación Completa

- **[DOCUMENTACION_TECNICA.md](DOCUMENTACION_TECNICA.md)** - Arquitectura MVC, algoritmos, endpoints
- **[CONTRIBUTING.md](CONTRIBUTING.md)** - Guía para contribuir al proyecto

---

## 🤝 Contribuir

¿Quieres mejorar Smart-Booking? ¡Bienvenido!

### Pasos para Contribuir

1. **Fork el repositorio**
   ```bash
   git clone https://github.com/tu-usuario/smart-booking-wp.git
   cd smart-booking-wp
   ```

2. **Crea una rama para tu feature**
   ```bash
   git checkout -b feature/mi-nueva-caracteristica
   ```

3. **Haz tus cambios y prueba**
   ```bash
   # Edita archivos, prueba localmente
   git add .
   git commit -m "Añadir: descripción del cambio"
   ```

4. **Sube y abre un Pull Request**
   ```bash
   git push origin feature/mi-nueva-caracteristica
   ```

Consulta [CONTRIBUTING.md](CONTRIBUTING.md) para más detalles.

---

## 🗺️ Roadmap (Próximas Mejoras)

### Fase 2: Funcionalidades Avanzadas
- [ ] Notificaciones por email
- [ ] Recordatorios automáticos 24h antes
- [ ] Cancelación de turnos por el cliente
- [ ] Reprogramación de turnos
- [ ] Historial de reservas del cliente

### Fase 3: Experiencia de Usuario
- [ ] Múltiples idiomas
- [ ] Tema oscuro
- [ ] Validación de teléfono
- [ ] Autocompletado de datos
- [ ] Galería de fotos de servicios

### Fase 4: Administración Avanzada
- [ ] Gestión de múltiples empleados
- [ ] Asignación de turnos a empleados
- [ ] Reportes y estadísticas avanzadas
- [ ] Gráficos de ocupación
- [ ] Integración con sistemas de pago

### Fase 5: Integraciones
- [ ] Google Calendar
- [ ] Outlook/Exchange
- [ ] Zapier/Make.com
- [ ] Webhooks
- [ ] CRM (HubSpot, Salesforce)

---

## 📊 Estadísticas del Proyecto

| Métrica | Valor |
|---------|-------|
| Líneas de código PHP | ~1,500 |
| Líneas de código JavaScript | ~800 |
| Líneas de código CSS | ~600 |
| Archivos totales | 20+ |
| Endpoints REST API | 4 |
| Servicios predefinidos | 8 |
| Tiempo de desarrollo | ~40 horas |

---

## 🙏 Agradecimientos

- **FullCalendar.js** - Calendario interactivo
- **Tailwind CSS** - Framework de estilos
- **WordPress** - Plataforma base
- **Meta** - API de WhatsApp Business
- **Comunidad de desarrolladores** - Feedback y sugerencias

---

## 🎉 ¡Comienza Ahora!

2. **Instala** en tu WordPress
3. **Configura** con tu nombre de negocio
4. **Usa** el shortcode `[smart_booking]` en una página
5. **¡Disfruta** de reservas sin overbooking!

---

**Última actualización:** 10 de Marzo de 2026  
**Versión:** 1.0.0  
**Desarrollador:** Hector George 
**Estado:** ✅ Producción 

---
