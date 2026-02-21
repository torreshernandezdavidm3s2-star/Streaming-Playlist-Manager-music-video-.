flowchart TD

    USER["USER Document
    ---
    _id : ObjectId
    name : string
    username : string
    age : int
    email : string
    gender : string
    playlists : array"]

    PLAYLIST["PLAYLIST Embedded Document
    ---
    playlist_id : ObjectId
    playlist_name : string
    created_at : date
    songs : array"]

    SONG["SONG Embedded Document
    ---
    song_id : ObjectId
    name : string
    duration : string
    artist : string
    genre : string"]

    USER -->|embeds| PLAYLIST
    PLAYLIST -->|embeds| SONG
