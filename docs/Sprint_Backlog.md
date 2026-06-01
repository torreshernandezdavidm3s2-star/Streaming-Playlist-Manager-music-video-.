# 🏃‍♂️ Sprint Backlog — Sprint 1 (Con Estimación de Tiempos en Horas)

## 🎯 1. Objetivo del Sprint (Sprint Goal)
> **"Desplegar la arquitectura base y el flujo funcional extremo a extremo (E2E) de NextGen Music Platform: permitiendo el registro/perfil de usuarios, la carga y reproducción de audio persistente, búsquedas con debounce, inicialización de IndexedDB para descargas, generación de enlaces y renderizado responsivo con Modo Oscuro."**

---

## 📋 2. Elementos Seleccionados del Product Backlog
El equipo se compromete a entregar los cimientos de las 9 historias de usuario en este ciclo de 1 semana (5 días laborables).

---

## 🛠️ 3 y 4. Plan de Acción: Tareas, Responsables y Estimación en Horas

### 👤 EPIC-01: User Account Management (US-01 & US-02)
* **TS-01.1 [Estructura]** — **4 Horas**
    * *Descripción:* Modelar las tablas/colecciones de usuarios, banderas de estado (`Pending_Verification`, `Locked`) y unicidad de usernames.
    * *Responsable:* **Maria Argel** (The Data Modeler)
* **TS-01.2 [Desarrollo]** — **10 Horas**
    * *Descripción:* Backend en Node.js/Python para hashing de contraseñas (Regex), tokens HTTP-Only JWT y contador de reintentos para la política de bloqueo de 15 min.
    * *Responsable:* **Erick de Jesus** (The Query Developer)
* **TS-01.3 [Integración]** — **6 Horas**
    * *Descripción:* Formulario de registro interactivo con validación asíncrona de disponibilidad de username mientras el usuario escribe y feedback visual de fuerza de clave.
    * *Responsable:* **Oliver Peralta** (The Integration Specialist)
* **TS-01.4 [Pruebas/QA]** — **6 Horas**
    * *Descripción:* Automatización de scripts con herramientas de testing (Cypress/Jest) para simular los 5 ataques fallidos consecutivos y carga de archivos >2MB.
    * *Responsable:* **David Torres** (The Data Seeder / QA)

### 🎧 EPIC-02: Music Upload and Playback (US-03 & US-04)
* **TS-02.1 [Estructura]** — **4 Horas**
    * *Descripción:* Esquema de datos para canciones, géneros y links CDN de almacenamiento.
    * *Responsable:* **Maria Argel** (The Data Modeler)
* **TS-02.2 [Desarrollo]** — **6 Horas**
    * *Descripción:* Endpoint de subida de archivos que valide en el servidor el tamaño límite de 50MB y las extensiones explícitas (.mp3, .wav, .flac).
    * *Responsable:* **Erick de Jesus** (The Query Developer)
* **TS-02.3 [Integración]** — **9 Horas**
    * *Descripción:* Creación del componente UI de barra de progreso (cálculo cada 500ms) y maquetación del *Persistent Media Player* fijo en el viewport.
    * *Responsable:* **Oliver Peralta** (The Integration Specialist)

### 🎶 EPIC-03: Playlist Management (US-05)
* **TS-03.1 [Estructura]** — **4 Horas**
    * *Descripción:* Estructura de tablas intermedias para listas, orden de canciones e índices de privacidad (`Public`/`Private`).
    * *Responsable:* **Maria Argel** (The Data Modeler)
* **TS-03.2 [Integración]** — **4 Horas**
    * *Descripción:* Menú contextual "Añadir a Playlist" en filas de canciones y preparación del entorno para drag-and-drop.
    * *Responsable:* **Oliver Peralta** (The Integration Specialist)

### 🎶 EPIC-04: Advanced Music Search (US-06)
* **TS-04.1 [Desarrollo]** — **6 Horas**
    * *Descripción:* Creación de consultas con operadores de búsqueda parcial (*Fuzzy Match*) optimizadas para responder en menos de 1.5 segundos.
    * *Responsable:* **Erick de Jesus** (The Query Developer)
* **TS-04.2 [Integración]** — **5 Horas**
    * *Descripción:* Función de Debounce de 300ms en el input de búsqueda del cliente y diseño del estado vacío (sugerencias Pop, Rock, Hip-Hop).
    * *Responsable:* **Oliver Peralta** (The Integration Specialist)

### 📥 EPIC-05: Offline Listening (US-07)
* **TS-05.1 [Estructura]** — **6 Horas**
    * *Descripción:* Configuración del ciclo de vida de **IndexedDB** local y desarrollo del helper criptográfico nativo en el navegador (Web Crypto API).
    * *Responsable:* **Maria Argel** (The Data Modeler)
* **TS-05.2 [Integración]** — **8 Horas**
    * *Descripción:* Integración con la Web Storage API para control de cuota de disco en el dispositivo y eventos de pausa por pérdida de red (`navigator.onLine`).
    * *Responsable:* **Oliver Peralta** (The Integration Specialist)

### 🔗 EPIC-06: Social Sharing Features (US-08)
* **TS-06.1 [Integración]** — **4 Horas**
    * *Descripción:* Helper JS para inyectar URLs dinámicas con soporte de portapapeles (`navigator.clipboard`) y Web Share API para móviles.
    * *Responsable:* **Oliver Peralta** (The Integration Specialist)

### 🎨 EPIC-07: UI/UX Design (US-09)
* **TS-07.1 [Estructura]** — **4 Horas**
    * *Descripción:* Configuración inicial del archivo de Design Tokens en CSS/Sass con el mapa de variables Claro/Oscuro.
    * *Responsable:* **Maria Argel** (The Data Modeler / UI Support)
* **TS-07.2 [Integración]** — **6 Horas**
    * *Descripción:* Layout base responsivo (breakpoints de pantalla) e implementación de accesibilidad semántica ARIA para lectores de pantalla.
    * *Responsable:* **Oliver Peralta** (The Integration Specialist)
* **TS-07.3 [Pruebas/QA]** — **10 Horas**
    * *Descripción:* Auditorías continuas con Axe/Lighthouse a la interfaz en ambos modos para asegurar que los ratios de contraste se mantengan en un mínimo de 4.5:1.
    * *Responsable:* **David Torres** (The Data Seeder / QA)

---

## 📊 4. Balanceo de Carga e Historial de Tiempos
El Scrum Master (**Jorge Florencio Severiano**) corrobora que la asignación de horas respeta la capacidad real del equipo para un sprint de 1 semana, evitando sobrecargas de trabajo:

* **Maria Argel (The Data Modeler):** **22 Horas** en total.
    * *Foco:* Concentrada al inicio de la semana (Lunes a Miércoles) entregando las bases lógicas, IndexedDB y tokens CSS al equipo.
* **Erick de Jesus (The Query Developer):** **22 Horas** en total.
    * *Foco:* Desarrollo continuo de endpoints y consultas seguras en el servidor durante toda la semana.
* **Oliver Peralta (The Integration Specialist):** **42 Horas** en total.
    * *Nota de mitigación de riesgo:* Oliver cuenta con una carga superior de trabajo. Para balancear, Erick de Jesus y Maria Argel le darán soporte técnico directo en la maquetación del modo oscuro una vez terminen sus entregables de bases de datos el Jueves por la mañana.
* **David Torres (The Data Seeder / QA):** **16 Horas** en total.
    * *Foco:* Aseguramiento de calidad, auditorías WCAG 2.1 AA y simulación de fallas de seguridad/red desde el Miércoles en adelante.

---
*Métricas tácticas de tiempo estimadas por el equipo de desarrollo de NextGen Music Platform.*
