# Sprint Backlog & MVP Strategy — NextGen Music Platform
Project Version: 2.0.5  
Target Audience: Independent Creators & Music Lovers  
Approach: Frictionless Audio Pipeline & Empowered Identity

---

## 🎯 Sprint Goal
**Establish creator visual identity capabilities and enable interactive content curation on the client side, ensuring that playlist management and reordering persist in the database without degrading the performance of the global audio player.**

---

## 🎯 Strategic Approach

With the streaming engine, authentication protocols, and search indexes successfully established in Sprint 1, the architecture now scales toward the **Empowered Identity** pillar and user retention. This cycle's focus mitigates the risks of dynamic storage and complex persistent states on the client side by implementing relational management for collections and optimizing binary identity resources (images) prior to cloud persistence.

These user stories represent the transformation of an isolated playback utility into a personalized, dynamic ecosystem.

---

## ⛓️ Sprint Dependencies & Cross-Functional Mapping

* **Profile Assets Dependency:** Integrating the frontend logic for image conversion and WebP upload (`TSK-02.3`) directly depends on the prior expansion of user tables and schema fields in the database (`TSK-02.1`).
* **Drag-and-Drop UI Blocker:** Developing the interactive interface for playlist reordering (`TSK-05.3`) requires the query developer to have already finalized the atomic bulk update procedures for position indexes (`TSK-05.2`) to prevent state mismatch between client and server.
* **Volume Testing in Playlists:** QA volume and stress testing for large collections (`TSK-05.4`) is strictly tied to the delivery of the final relational model for the `track_playlist` pivot table (`TSK-05.1`).

---

## ⚠️ Potential Impediments & Risk Mitigation

* **UI Rendering Degradation due to List Reordering:** Inefficient Drag-and-Drop libraries or poor global state handling can trigger massive UI re-renders, causing visual stuttering or freezing the main thread where the Web Audio API context (`US-04`) runs.
  * *Mitigation:* Implement memoized components (`React.memo` or equivalent wrappers) and utilize isolated local states for dragging, syncing with the backend only upon component release (drop).
* **Network Overhead from Raw Image Uploads:** If creators upload heavy, uncompressed images (such as high-res raw PNGs or JPEGs) for banners or avatars, network bandwidth will saturate and cloud storage costs will spike.
  * *Mitigation:* Enforce client-side image compression and resizing using the Canvas API (`TSK-02.3`), converting all assets to WebP format before dispatching to Object Storage.
* **Database Deadlocks during Bulk Position Updates:** If multiple users concurrently reorder playlists, poorly optimized bulk update queries could lock rows or entire tables, throttling the entire API.
  * *Mitigation:* Apply transaction-specific indexed sequencing or spaced integer tracking in the database layer (`TSK-05.2`).

---

## 🔴 High Priority: Core Capabilities (Value & Urgency)

### 🧪 US-02: Profile Customization
* **Why it's in the Sprint:** Independent creators require visual branding capabilities (avatar, banners, extended metadata) to anchor their identity alongside their audio content. Previously deferred in Sprint 1, its implementation is now mandatory to validate UI consistency and static asset cloud pipelines.
* **Key Focus:** * Client-side image compression and resizing via the Canvas API to minimize bandwidth impact.
  * Decoupled storage for user metadata and CDN-optimized static asset URLs.

### 🧪 US-05: Playlist Management
* **Why it's in the Sprint:** This is the functional core of continuous and interactive music consumption. Listeners need to curate content without relying strictly on global search queries or main discovery feeds.
* **Key Focus:**
  * Implementation of a fluid client-side state architecture for interactive reordering (Drag-and-Drop UI).
  * Atomic backend mutations to prevent sequential query overhead during order updates.

---

## 👤 EPIC-01: User Account Management (Cont.)

### 🧪 US-02: Profile Customization
**Goal:** Allow users and creators to customize their profiles with optimized avatars, banners, and biographies.

| Task ID | Task Description | Est. Time | Primary Assignee |
| :--- | :--- | :--- | :--- |
| **TSK-02.1** | Expand user database schema to support asset URLs (avatar/banner), profile search indexing, and extended biography fields. | 4 hrs | Rueda Jaime Maria Argel (Data Modeler) |
| **TSK-02.2** | Write profile update stored procedures with strict account status validation and asset cleanup triggers. | 6 hrs | López Torres Erick de Jesus (Query Developer) |
| **TSK-02.3** | Build profile API endpoints and integrate frontend client-side WebP compression/conversion before uploading to Object Storage. | 12 hrs | Peralta Trujillo Oliver (Integration Specialist) |
| **TSK-02.4** | Validate ingestion pipelines with massive files, corrupted payloads, XSS injection scripts in biographies, and mobile responsive viewports. | 8 hrs | Torres Hernández David (Data Seeder / QA) |

---

## 🎵 EPIC-03: Playlist & Curation Systems

### 🧪 US-05: Playlist Management
**Goal:** Interactive playlist creation, editing, and sorting with real-time data persistence.

| Task ID | Task Description | Est. Time | Primary Assignee |
| :--- | :--- | :--- | :--- |
| **TSK-05.1** | Design the Playlist relational model, pivot tables (`track_playlist`), visibility flags (public/private), and sequential sorting keys. | 6 hrs | Rueda Jaime Maria Argel (Data Modeler) |
| **TSK-05.2** | Develop optimized queries for bulk track index updates, minimizing table locks and database transaction latency. | 10 hrs | López Torres Erick de Jesus (Query Developer) |
| **TSK-05.3** | Develop frontend Drag-and-Drop layout components and seamlessly connect them to the global player playback queue state (`US-04`). | 16 hrs | Peralta Trujillo Oliver (Integration Specialist) |
| **TSK-05.4** | Seed mock collections with 200+ associated tracks to stress test pagination, client state re-renders, and database synchronization. | 10 hrs | Torres Hernández David (Data Seeder / QA) |

---

## 📋 Scrum Master Checklist (Jorge Florencio Severiano)

To maintain velocity and ensure optimal rendering performance for the reactive user interface:
* **Local State Monitoring:** Verify that dynamic drag-and-drop mutations do not cause expensive UI re-renders that could degrade background audio streaming performance.
* **Task Synchronization:** Ensure that optimized static asset ingestion (`TSK-02.3`) correctly aligns with the cloud infrastructure security policies and CDN edge caching rules established in Sprint 1.

---

## ✅ Definition of Done (DoD) — Specialized Sprint 2

A requirement or task in this sprint is considered **completely done** if and only if it meets the following global acceptance criteria:

1. **Target Asset Optimization:** All uploaded profile images successfully process, convert to WebP on the client side, and their target object storage URLs resolve instantly via the edge CDN cache.
2. **Audio Anti-Regression Rule:** Reactive state mutations triggered by Drag-and-Drop sorting actions do not pause, interrupt, or introduce micro-stuttering into the actively running Web Audio API streaming instance.
3. **State Consistency & Persistence:** The visual order of tracks in a playlist matches the position index integers stored in the database exactly (1:1 ratio) upon hard browser refreshes.
4. **Sanitization & Security Validation:** All open text fields submitted by users (such as biographies or playlist descriptions) pass through strict encoding and escaping layers to neutralize potential XSS (Cross-Site Scripting) vectors.
5. **Pull Request (PR) Approval:** Code is successfully merged into the development branch after passing automated unit tests and receiving formal peer review sign-offs.
