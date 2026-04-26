# Esquema MongoDB Avanzado 🎵

## COLECCIONES BASE

USUARIO {
  _id: ObjectId (PK)
  nombre: string
  username: string
  edad: int
  correo: string
  genero: string
}

PLAYLIST {
  _id: ObjectId (PK)
  nombre: string
  fecha_creacion: date
  usuario_id: ObjectId (FK -> USUARIO._id)
}

CANCION {
  _id: ObjectId (PK)
  nombre: string
  duracion: int
  artista: string
  genero: string
}

## RELACIONES

USUARIO ||--o{ PLAYLIST : crea
PLAYLIST ||--o{ CANCION : contiene

----------------------------------

## MEJORA 1: PERFIL MUSICAL (IA)

PERFIL_MUSICAL {
  _id: ObjectId (PK)
  usuario_id: ObjectId (FK -> USUARIO._id)
  generos_favoritos: [string]
  artistas_favoritos: [string]
  nivel_actividad: float
}

USUARIO ||--|| PERFIL_MUSICAL : tiene

----------------------------------

## MEJORA 2: RECOMENDACIONES

RECOMENDACION {
  _id: ObjectId (PK)
  usuario_id: ObjectId (FK -> USUARIO._id)
  cancion_id: ObjectId (FK -> CANCION._id)
  algoritmo: string
  tipo: string
}

USUARIO ||--o{ RECOMENDACION : recibe
RECOMENDACION ||--o{ CANCION : sugiere

----------------------------------

## MEJORA 3: HISTORIAL

HISTORIAL {
  _id: ObjectId (PK)
  usuario_id: ObjectId (FK -> USUARIO._id)
  cancion_id: ObjectId (FK -> CANCION._id)
  fecha: date
  reproducciones: int
}

USUARIO ||--o{ HISTORIAL : escucha
CANCION ||--o{ HISTORIAL : aparece
