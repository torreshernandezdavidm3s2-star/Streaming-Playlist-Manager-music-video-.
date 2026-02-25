# Playlist System – NoSQL Data Model (MongoDB)
 
## Description
 
This project represents a data model for a music playlist system using a NoSQL approach based on MongoDB Document Model.
 
Users can:
 
* Create an account
* Create playlists
* Add songs to playlists
* Allow other users to view playlist author and songs
 
This model uses embedded documents to optimize read performance, which is a recommended practice in MongoDB.
 
---
 
## NoSQL Document Structure Overview
 
Hierarchy:
 
User
└── playlists[]
└── songs[]

 
This means:
 
* A User document embeds many Playlist documents
* Each Playlist embeds many Song documents
 
---
 
## Mermaid Diagram (MongoDB Document Model)
 
```mermaid
erDiagram
    %% ==========================================
    %% PARTE 1: REGISTRO Y ENTIDAD DE USUARIO
    %% (Criterio: Registro de cuenta y Metadata)
    %% ==========================================
    USER {
        ObjectId user_id PK "Generado automáticamente"
        string nombre
        string nombre_usuario
        int edad
        string correo
        string genero
    }

    %% ==========================================
    %% PARTE 2: CREACIÓN Y AUTORÍA 
    %% (Criterio: Relación entre Creador y Playlist)
    %% ==========================================
    USER ||--o{ PLAYLIST : "crea y es autor de"
    
    PLAYLIST {
        ObjectId playlist_id PK
        string nombre_playlist
        date fecha_creacion
    }

    %% ==========================================
    %% PARTE 3: DETALLE DEL CONTENIDO
    %% (Criterio: Listado de canciones detallado)
    %% ==========================================
    PLAYLIST ||--o{ SONG : "contiene"

    SONG {
        ObjectId song_id PK
        string nombre_cancion
        string duracion
        string artista "Creador de la canción"
        string genero_musical
    }
MongoDB Example Document
Example of how data is stored in MongoDB:

JSON
{
  "_id": "65f1a2b3c4d5e6f7890abcde",
  "nombre": "Erick Lopez",
  "nombre_usuario": "erickdev",
  "edad": 22,
  "correo": "erick@email.com",
  "genero": "male",
  "playlists": [
    {
      "playlist_id": "65f1a2b3c4d5e6f7890abcd1",
      "nombre_playlist": "Rock Classics",
      "fecha_creacion": "2026-02-20",
      "songs": [
        {
          "song_id": "65f1a2b3c4d5e6f7890abcd2",
          "nombre_cancion": "Bohemian Rhapsody",
          "duracion": "5:55",
          "artista": "Queen",
          "genero_musical": "Rock"
        },
        {
          "song_id": "65f1a2b3c4d5e6f7890abcd3",
          "nombre_cancion": "Hotel California",
          "duracion": "6:30",
          "artista": "Eagles",
          "genero_musical": "Rock"
        }
      ]
    }
  ]
}
Design Approach
This model uses embedding because:

Playlists belong to a single user

Songs belong to a single playlist

The main query is to view playlists with songs and creator information

Embedding improves read performance

Reduces the need for joins (which MongoDB does not use)

Technologies
MongoDB

BSON / JSON

Mermaid.js

GitHub Markdown
