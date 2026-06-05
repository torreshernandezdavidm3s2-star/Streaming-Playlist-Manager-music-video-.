PERFORMANCE AUDIT REPORT

Music Streaming Player

Week 16 (June 1 – June 5)

Introduction

During Week 16, the team focused on analyzing the performance of the database used in the Music Streaming Player project. As the platform continues to grow and store more songs, playlists, recommendations, and user activity records, database efficiency becomes increasingly important.

The main objective of this phase was to identify the most frequently executed queries and improve their performance through the implementation of MongoDB indexes.

---

Project Overview

Music Streaming Player is a multimedia music platform that allows users to listen to songs, create and manage playlists, receive personalized recommendations, and review their listening history.

The database was designed using MongoDB and follows a document-oriented architecture that supports flexibility and scalability.

Main Collections

- User
- Song
- Playlist
- Playlist_Song
- Musical_Profile
- Recommendation
- Recommendation_Song
- History
- History_Song

---

Performance Analysis

As the amount of stored information increases, query execution can become slower because MongoDB must scan a large number of documents before locating the requested data.

To improve efficiency, the team analyzed the most common operations performed by users within the application.

Frequently Used Queries

Search a song by name

db.song.find({ name: "Blinding Lights" })

Search songs by artist

db.song.find({ artist: "The Weeknd" })

Search songs by genre

db.song.find({ genre: "Pop" })

Retrieve playlists created by a user

db.playlist.find({ user_id: ObjectId("123") })

Retrieve listening history

db.history.find({ user_id: ObjectId("123") })

Retrieve user recommendations

db.recommendation.find({ user_id: ObjectId("123") })

---

Index Implementation

After identifying the most frequently executed queries, indexes were created to improve search speed and reduce database workload.

Song Name Index

db.song.createIndex({ name: 1 })

Artist Index

db.song.createIndex({ artist: 1 })

Genre Index

db.song.createIndex({ genre: 1 })

Playlist User Index

db.playlist.createIndex({ user_id: 1 })

History User Index

db.history.createIndex({ user_id: 1 })

Recommendation User Index

db.recommendation.createIndex({ user_id: 1 })

---

Results

Before implementing indexes, MongoDB performed collection scans when executing several queries. This process required checking a large number of documents before finding matching results.

After creating indexes, the database was able to locate information more efficiently by using indexed fields instead of scanning entire collections.

The optimization process produced the following benefits:

- Faster search operations.
- Reduced query execution time.
- Improved database efficiency.
- Better scalability for future growth.
- Enhanced user experience when browsing music content.

---

Impact on the Music Streaming Player Platform

The implemented indexes directly improved the responsiveness of several core features of the application, including:

- Song search functionality.
- Artist and genre filtering.
- Playlist retrieval.
- Listening history access.
- Personalized recommendation management.

These optimizations contribute to a smoother and more reliable streaming experience for users.

---

Conclusion

The performance audit demonstrated the importance of database optimization in modern applications. By implementing strategic indexes on frequently queried fields, the Music Streaming Player project achieved significant improvements in search efficiency and overall system responsiveness.

This activity reinforced the team's understanding of MongoDB indexing techniques and highlighted the role of performance optimization in building scalable and professional software solutions.