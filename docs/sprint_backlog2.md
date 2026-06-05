# Sprint Backlog & MVP Strategy — NextGen Music Platform
Project Version: 2.0.5
Target Audience: Independent Creators & Music Lovers
Approach: Frictionless Audio Pipeline & Empowered Identity

## 🎯 Sprint Goal
**Establecer las capacidades de identidad visual de los creadores y permitir la curación interactiva de contenido en el cliente, garantizando que la gestión y el reordenamiento de listas de reproducción (Playlists) persistan en la base de datos sin degradar el rendimiento del reproductor de audio global.**

---

## 🎯 Strategic Approach

Una vez establecidos el motor de streaming, los protocolos de autenticación y los índices de búsqueda en el Sprint 1, la arquitectura evoluciona hacia el pilar de **Empowered Identity** y la retención del usuario. El enfoque de este ciclo mitiga los riesgos de almacenamiento dinámico y estado persistente complejo en el cliente, implementando la gestión relacional para colecciones y la optimización de recursos binarios de identidad (imágenes) antes de su persistencia en la nube.

Estas historias de usuario representan la transición de una utilidad de reproducción aislada a un ecosistema personalizado y dinámico.

---

## 🟢 High Priority: Core Capabilities (Value & Urgency)

### 🧪 US-02: Profile Customization
* **Why it's in the Sprint:** Los creadores e independientes requieren establecer su marca visual (avatar, banners, metadatos extendidos) para que el contenido de audio tenga un punto de anclaje identitario. Dejado en el backlog diferido del Sprint 1, su implementación es mandatoria ahora para validar la consistencia estética y el almacenamiento de assets estáticos de perfil.
* **Key Focus:** * Compresión y redimensionamiento de imágenes en cliente (Canvas API) para limitar el impacto en la red.
  * Almacenamiento desacoplado de metadatos de usuario y URLs estáticas optimizadas para CDN.

### 🧪 US-05: Playlist Management
* **Why it's in the Sprint:** Es el núcleo funcional del consumo continuo e interactivo. Los oyentes necesitan agrupar contenidos sin depender exclusivamente de consultas globales o feeds generales.
* **Key Focus:**
  * Implementación de una arquitectura de estado local fluida para reordenamiento posicional interactivo (Drag-and-Drop).
  * Mutaciones atómicas en backend para evitar la sobrecarga de consultas secuenciales ante cambios de orden.

---

## 👤 EPIC-01: User Account Management (Cont.)

### 🧪 US-02: Profile Customization
**Goal:** Permitir a usuarios y creadores personalizar sus perfiles con avatares, banners y biografías con carga optimizada.

| Task ID | Task Description | Est. Time | Primary Assignee |
| :--- | :--- | :--- | :--- |
| **TSK-02.1** | Expandir el esquema de usuarios en base de datos para soportar URLs de assets (avatar/banner), índices de búsqueda de perfiles y campos extendidos de biografía. | 4 hrs | Rueda Jaime Maria Argel (Data Modeler) |
| **TSK-02.2** | Crear procedimientos de actualización de perfil con validación estricta de estado de cuenta y triggers de limpieza de registros antiguos. | 6 hrs | López Torres Erick de Jesus (Query Developer) |
| **TSK-02.3** | Implementar endpoints API de perfiles e integrar lógica frontend para compresión/conversión de imágenes a WebP antes de subirlas al Object Storage. | 12 hrs | Peralta Trujillo Oliver (Integration Specialist) |
| **TSK-02.4** | Validar el procesamiento con imágenes masivas, payloads corruptos, inyección de scripts en biografías y pruebas de adaptabilidad en vistas móviles. | 8 hrs | Torres Hernández David (Data Seeder / QA) |

---

## 🎵 EPIC-03: Playlist & Curation Systems

### 🧪 US-05: Playlist Management
**Goal:** Creación, edición y ordenamiento interactivo de listas de reproducción con persistencia de datos en tiempo real.

| Task ID | Task Description | Est. Time | Primary Assignee |
| :--- | :--- | :--- | :--- |
| **TSK-05.1** | Diseñar el modelo relacional de Playlists, tablas pivot (track_playlist), flags de visibilidad (pública/privada) y claves secuenciales para ordenación posicional. | 6 hrs | Rueda Jaime Maria Argel (Data Modeler) |
| **TSK-05.2** | Desarrollar consultas optimizadas para reordenamiento masivo de canciones mediante bulk updates de índices de posición, minimizando bloqueos de tablas. | 10 hrs | López Torres Erick de Jesus (Query Developer) |
| **TSK-05.3** | Desarrollar los componentes de interfaz Drag-and-Drop para ordenamiento e integrarlos de manera transparente con el contexto del reproductor global (US-04). | 16 hrs | Peralta Trujillo Oliver (Integration Specialist) |
| **TSK-05.4** | Generar colecciones mock con más de 200 tracks asociados para estresar el rendimiento de la paginación, re-renders de UI y sincronización con base de datos. | 10 hrs | Torres Hernández David (Data Seeder / QA) |

---

## 📋 Scrum Master Checklist (Jorge Florencio Severiano)

Para mantener la velocidad y asegurar un rendimiento óptimo de la interfaz reactiva:
* **Monitoreo de Estado Local:** Controlar que el estado del orden de los tracks en listas no provoque re-renders costosos que degraden la experiencia de reproducción activa en segundo plano.
* **Sincronización de Tareas:** Garantizar que la subida optimizada de assets estáticos (TSK-02.3) se acople correctamente con las políticas de acceso público y caché de la infraestructura de almacenamiento cloud establecida en el Sprint 1.
