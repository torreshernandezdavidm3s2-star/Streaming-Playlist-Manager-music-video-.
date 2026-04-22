# Esquema MongoDB Avanzado 🎵

Sistema de streaming musical con funciones tipo Spotify / YouTube Music

```mermaid
erDiagram

%% =========================
%% COLECCIONES BASE (DEL COMPAÑERO)
%% =========================

USER {
    string nombre
    string username
    int edad
    string correo
    string genero
}

PLAYLIST {
    string nombre
    date fecha_creacion
}

SONG {
    string nombre_cancion
    int duracion
    string artista
    string genero_musical
}

USER ||--o{ PLAYLIST : crea
PLAYLIST ||--o{ SONG : contiene

%% =========================
%% MEJORA 1: PERFIL MUSICAL (IA)
%% =========================

PERFIL_MUSICAL {
    string generos_favoritos
    string artistas_favoritos
    float nivel_actividad
}

USER ||--|| PERFIL_MUSICAL : tiene

%% =========================
%% MEJORA 2: RECOMENDACIONES INTELIGENTES
%% =========================

RECOMENDACION {
    string algoritmo
    string tipo
}

USER ||--o{ RECOMENDACION : recibe
RECOMENDACION ||--o{ SONG : sugiere

%% =========================
%% MEJORA 3: HISTORIAL Y MÉTRICAS
%% =========================

HISTORIAL {
    date fecha
    int reproducciones
}

USER ||--o{ HISTORIAL : escucha
SONG ||--o{ HISTORIAL : aparece
