# Esquema MongoDB Avanzado 🎵

```mermaid
erDiagram

%% =========================================
%% 🔹 NODO PRINCIPAL
%% =========================================

USUARIO {
  ObjectId _id PK
  string nombre
  string username
  int edad
  string correo
  string genero
}

%% =========================================
%% 🔹 CONTENIDO
%% =========================================

CANCION {
  ObjectId _id PK
  string nombre
  int duracion
  string artista
  string genero
}

%% =========================================
%% 🔹 CREACIÓN (SIN CRUCES)
%% =========================================

PLAYLIST {
  ObjectId _id PK
  string nombre
  date fecha_creacion
  ObjectId usuario_id FK
}

PLAYLIST_CANCION {
  ObjectId _id PK
  ObjectId playlist_id FK
  ObjectId cancion_id FK
}

%% =========================================
%% 🔹 PERFIL
%% =========================================

PERFIL_MUSICAL {
  ObjectId _id PK
  ObjectId usuario_id FK
  string generos_favoritos
  string artistas_favoritos
  float nivel_actividad
}

%% =========================================
%% 🔹 INTERACCIONES (SEPARADAS)
%% =========================================

RECOMENDACION {
  ObjectId _id PK
  ObjectId usuario_id FK
  string algoritmo
  string tipo
}

RECOMENDACION_CANCION {
  ObjectId _id PK
  ObjectId recomendacion_id FK
  ObjectId cancion_id FK
}

HISTORIAL {
  ObjectId _id PK
  ObjectId usuario_id FK
  date fecha
  int reproducciones
}

HISTORIAL_CANCION {
  ObjectId _id PK
  ObjectId historial_id FK
  ObjectId cancion_id FK
}

%% =========================================
%% 🔹 RELACIONES (ULTRA LIMPIAS)
%% =========================================

USUARIO ||--o{ PLAYLIST : crea
PLAYLIST ||--o{ PLAYLIST_CANCION : contiene
PLAYLIST_CANCION }o--|| CANCION : incluye

USUARIO ||--|| PERFIL_MUSICAL : tiene

USUARIO ||--o{ RECOMENDACION : recibe
RECOMENDACION ||--o{ RECOMENDACION_CANCION : genera
RECOMENDACION_CANCION }o--|| CANCION : sugiere

USUARIO ||--o{ HISTORIAL : registra
HISTORIAL ||--o{ HISTORIAL_CANCION : guarda
HISTORIAL_CANCION }o--|| CANCION : reproduce
