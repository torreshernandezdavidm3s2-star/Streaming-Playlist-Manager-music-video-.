
# 🎵 

## 📌 Project Overview

**Version:** 1.0.0  
**Status:** 🚀 Active Development  
**Target Audience:** Independent Creators & Music Lovers  

---

## 🎯 The Product Goal & Vision

> **For** independent music creators and avid listeners **who** struggle with cluttered, non-intuitive, or highly restrictive audio platforms, **the NextGen Music Platform** is a decentralized-feeling ecosystem **that** seamlessly bridges the gap between high-fidelity music streaming and effortless community sharing. 
> 
> Unlike traditional streaming giants with rigid barrier entries, our platform delivers an ultra-fast, accessible, and deeply personalized music management experience right from your browser.

---

## ⚡ Core Strategic Pillars

To achieve this goal, the project's development is governed by four fundamental pillars:

### 👤 1. Empowered Identity
* **Deep Personalization:** Enable users to shape their musical space through dynamic profiles and smart libraries that adapt to their listening habits.
* **Security First:** Safeguard account integrity and privacy using modern authentication standards and data encryption.

### 🎧 2. Frictionless Audio Pipeline
* **Creator-Friendly Uploads:** Remove technical friction for artists by supporting high-fidelity formats (`.flac`, `.wav`) with automatic cloud processing.
* **Seamless Streaming:** Guarantee continuous, low-latency playback with native controls that emulate a desktop application experience.

### 🔍 3. Hyper-Efficient Discovery
* **Instant Search:** Implement intelligent search mechanisms (Fuzzy Match) and advanced filtering systems that return relevant results in milliseconds.
* **Curated Curation:** Facilitate playlist creation and management through intuitive interfaces (drag-and-drop), turning song lists into shareable content collections.

### 📥 4. Ubiquitous Access
* **Offline Independence:** Break dependency on internet connectivity through a smart, encrypted local storage system (IndexedDB).
* **Responsive Harmony:** Ensure the interface is visually stunning and 100% functional, whether accessing from a smartphone, tablet, or desktop computer.

---
## 🗺️ Product Roadmap & Requirements Traceability

Use this matrix to navigate between high-level Epics and their technical requirements (User Stories).

| Epic | Description | Linked User Stories |
| :--- | :--- | :--- |
| [👤 EPIC-01](#-epic-01--user-account-management) | User Account Management | [US-01](#-user-story-us-01-user-registration-and-login), [US-02](#-user-story-us-02-profile-customization) |
| [🎧 EPIC-02](#-epic-02--music-upload-and-playback) | Music Upload and Playback | [US-03](#-user-story-us-03-audio-file-upload), [US-04](#-user-story-us-04-music-playback-controls) |
| [🎶 EPIC-03](#-epic-03--playlist-management) | Playlist Management | [US-05](#-user-story-us-05-playlist-creation-and-curation) |
| [🔎 EPIC-04](#-epic-04--advanced-music-search) | Advanced Music Search | [US-06](#-user-story-us-06-search-music-by-different-criteria) |
| [📥 EPIC-05](#-epic-05--offline-listening) | Offline Listening | [US-07](#-user-story-us-07-download-music-for-offline-use) |
| [🔗 EPIC-06](#-epic-06--social-sharing-features) | Social Sharing Features | [US-08](#-user-story-us-08-share-music-content) |
| [🎨 EPIC-07](#-epic-07--user-experience-and-interface-design) | UI/UX Design | [US-09](#-user-story-us-09-modern-user-interface) |

---

# 🧩 Epics

## 👤 EPIC-01 — User Account Management
**Description:** Secure authentication and user profile management system.
**Goals:**
* User registration and authentication
* Profile customization
* Secure account management

## 🎧 EPIC-02 — Music Upload and Playback
**Description:** System for uploading, storing, and streaming music.
**Goals:**
* Upload audio files
* Stream and play music
* Manage playback controls

## 🎶 EPIC-03 — Playlist Management
**Description:** Create and manage custom playlists.
**Goals:**
* Create playlists
* Add or remove songs
* Organize music collections

## 🔎 EPIC-04 — Advanced Music Search
**Description:** Search engine for songs, artists, albums, and genres.
**Goals:**
* Search by title
* Search by artist or genre
* Fast and accurate results

## 📥 EPIC-05 — Offline Listening
**Description:** Download music for offline playback.
**Goals:**
* Download songs
* Offline playback support
* Storage management

## 🔗 EPIC-06 — Social Sharing Features
**Description:** Share songs and playlists with other users.
**Goals:**
* Generate shareable links
* Social media integration
* Cross-platform sharing
  
## 🎨 EPIC-07 — User Experience and Interface Design
**Description:** Modern and responsive UI/UX design.
**Goals:**
* Responsive interface
* Consistent design system
* Easy navigation

---

# 🧪 User Stories (Detailed & Specific)

### 🧪 User Story (US-01): User Registration and Login
**Epic Link:** [EPIC-01](#-epic-01--user-account-management)  
**As a:** New or returning user  
**I want:** To create an account and log in securely  
**So that:** I can save my personal preferences and music library  

#### ✅ Acceptance Criteria
* **AC-01.1 (Password Complexity):** The system must reject passwords that do not contain at least 8 characters, 1 uppercase letter, 1 lowercase letter, 1 number, and 1 special character (`@`, `$`, `!`, `%`, `*`, `#`, `?`, `&`).
* **AC-01.2 (Email Validation):** The system must validate email syntax (`user@domain.com`) and check for uniqueness in the database before creating the account.
* **AC-01.3 (Token Expiration):** Successful login must return a secure HTTP-Only JWT cookie with an expiration time of 7 days.
* **AC-01.4 (Account Lockout):** The account must be temporarily locked for 15 minutes after 5 consecutive failed login attempts to prevent brute-force attacks.

#### 🔍 Scenarios
**Scenario 1: Successful registration with valid data**
* **Given** the user is on the registration form and enters a non-registered email "test@musicapp.com"  
* **And** entering the password "SecurePass123!"  
* **When** the user clicks the "Sign Up" button  
* **Then** the system creates the user record with status `Pending_Verification`  
* **And** a toast notification appears saying: "Verification email sent. Please check your inbox."  

**Scenario 2: Failed registration due to weak password**
* **Given** the user is on the registration form  
* **When** they enter the password "12345"  
* **Then** the system disables the "Sign Up" button  
* **And** displays an inline error message: "Password must be at least 8 characters long and include numbers and special characters."  

**Scenario 3: Account lockout after multiple failed logins**
* **Given** a registered user exists with email "user@musicapp.com"  
* **When** the user enters an incorrect password 5 times in a row within 5 minutes  
* **Then** the system displays the error: "Account locked due to multiple failed attempts. Try again in 15 minutes."  
* **And** updates the user status in the database to `Locked`.

---

### 🧪 User Story (US-02): Profile Customization
**Epic Link:** [EPIC-01](#-epic-01--user-account-management)  
**As a:** Registered user  
**I want:** To customize my profile picture, username, and bio  
**So that:** I can personalize my identity on the platform  

#### ✅ Acceptance Criteria
* **AC-02.1 (Image Constraints):** Users can upload profile images restricted to JPEG/PNG formats with a maximum file size of 2MB.
* **AC-02.2 (Username Uniqueness):** Usernames must be unique across the platform. The UI must validate availability asynchronously as the user types.
* **AC-02.3 (Immediate Feedback):** Profile updates must reflect instantly across the current user session upon clicking "Save Changes".

---

### 🧪 User Story (US-03): Audio File Upload
**Epic Link:** [EPIC-02](#-epic-02--music-upload-and-playback)  
**As a:** Creator / Artist user  
**I want:** To upload audio files with metadata  
**So that:** I can share my music on the platform  

#### ✅ Acceptance Criteria
* **AC-03.1 (Format Restriction):** Only `.mp3`, `.wav`, and `.flac` extensions are allowed. Any other file format must be rejected immediately at the browser level.
* **AC-03.2 (Size Limits):** The maximum allowable file size is exactly 50 Megabytes (MB).
* **AC-03.3 (Required Metadata):** The "Song Title" field (min 2 characters, max 100) and "Genre" dropdown selection are mandatory before allowing the upload button to be clicked.
* **AC-03.4 (Progress Visibility):** The upload progress bar must update every 500ms and display both the visual percentage completed and the remaining transfer time.

#### 🔍 Scenarios
**Scenario 1: Uploading a valid MP3 track**
* **Given** the artist is on the "Upload Track" dashboard  
* **And** they select a valid file named "track1.mp3" (size 12MB)  
* **And** they fill out the mandatory fields "Song Title: Summer Vibes" and "Genre: Pop"  
* **When** they click the "Upload" button  
* **Then** the progress bar starts animating from 0% to 100%  
* **And** upon 100% completion, the track status changes to "Processing" and a success message is shown.

**Scenario 2: Trying to upload an invalid file extension**
* **Given** the artist opens the file selector  
* **When** they attempt to select a file named "album_cover.png" or a video file "video.mp4"  
* **Then** the file explorer filters out these formats  
* **And** if forced via drag-and-drop, the application displays a red alert banner: "Invalid file format. Please upload MP3, WAV, or FLAC."  

---

### 🧪 User Story (US-04): Music Playback Controls
**Epic Link:** [EPIC-02](#-epic-02--music-upload-and-playback)  
**As a:** Listener  
**I want:** A standard media player with Play, Pause, Skip, and Volume controls  
**So that:** I can control my streaming experience smoothly  

#### ✅ Acceptance Criteria
* **AC-04.1 (Buffer Management):** Audio must stream smoothly with a pre-buffering window of at least 5 seconds on standard mobile network speeds.
* **AC-04.2 (Queue Management):** Next/Previous buttons must instantly transition to the corresponding item in the active playback queue.
* **AC-04.3 (Persistent Player):** The media player component must remain mounted and active at the bottom of the viewport during application route changes.

---

### 🧪 User Story (US-05): Playlist Creation and Curation
**Epic Link:** [EPIC-03](#-epic-03--playlist-management)  
**As a:** User  
**I want:** To create playlists and add/remove tracks easily  
**So that:** I can organize my favorite tracks for different moods  

#### ✅ Acceptance Criteria
* **AC-05.1 (Contextual Actions):** An "Add to Playlist" action must be present on all track listing instances.
* **AC-05.2 (Privacy Controls):** Playlists must support explicit toggles between Public and Private visibility scopes.
* **AC-05.3 (Interactive Reordering):** The user interface must support dragging and dropping list rows to alter playlist execution orders.

---

### 🧪 User Story (US-06): Search Music by Different Criteria
**Epic Link:** [EPIC-04](#-epic-04--advanced-music-search)  
**As a:** User  
**I want:** To search songs by title, artist, album, or genre  
**So that:** I can quickly find music  

#### ✅ Acceptance Criteria
* **AC-06.1 (Debounce Mechanism):** The search API call must only trigger after the user has stopped typing for 300 milliseconds (debounce) to avoid overloading the server.
* **AC-06.2 (Minimum Input):** Search queries must require a minimum of 2 characters to trigger a database search.
* **AC-06.3 (Fuzzy Match Performance):** Search results must return partial matches (e.g., typing "rock" should return "Rockstar", "Rocket Man") and load in less than 1.5 seconds under a standard network connection.
* **AC-06.4 (Empty States):** If no matches are found, the UI must display a friendly clear message and recommend popular genres.

#### 🔍 Scenarios
**Scenario 1: Real-time search with partial text**
* **Given** the user places the cursor in the global search bar  
* **When** the user types the letters "Beat"  
* **Then** the application waits 300ms  
* **And** displays a dropdown list displaying "The Beatles (Artist)" and "Beat It - Michael Jackson (Song)" within 1.5 seconds.

**Scenario 2: No search results found**
* **Given** the user is typing in the search bar  
* **When** they type a random string like "xyzqwe123"  
* **Then** the results area clears  
* **And** shows the message: "No results found for 'xyzqwe123'. Try exploring these genres instead:" followed by quick-clickable tags for Pop, Rock, and Hip-Hop.

---

### 🧪 User Story (US-07): Download Music for Offline Use
**Epic Link:** [EPIC-05](#-epic-05--offline-listening)  
**As a:** User  
**I want:** To download songs and playlists  
**So that:** I can listen offline  

#### ✅ Acceptance Criteria
* **AC-07.1 (Storage Space Check):** Before starting a download, the app must estimate the required space and verify via the Web Storage API / IndexedDB if the device has enough local storage.
* **AC-07.2 (Download Interruption Management):** If the network drops during download, the app must pause the state, and automatically resume from the last downloaded byte once connection returns.
* **AC-07.3 (Encryption):** Downloaded audio files must be stored encrypted locally in IndexedDB, preventing users from copying raw `.mp3` files out of the browser/app application folders.

#### 🔍 Scenarios
**Scenario 1: Insufficient device storage**
* **Given** the user wants to download a high-fidelity playlist requiring 500MB of space  
* **And** the device only has 100MB of free space allocated for the app storage  
* **When** the user clicks the "Download Playlist" icon  
* **Then** the download process is blocked from starting  
* **And** a modal pops up stating: "Insufficient storage space. Please clear some cached tracks or free up device space."

**Scenario 2: Automatic resume on network recovery**
* **Given** a song download is currently at 45% completion  
* **When** the internet connection drops (offline status detected)  
* **Then** the download indicator icon changes to a yellow warning symbol saying "Paused - Waiting for network"  
* **And** when the network status changes back to online, the download automatically resumes from 45% without restarting from 0%.

---

### 🧪 User Story (US-08): Share Music Content
**Epic Link:** [EPIC-06](#-epic-06--social-sharing-features)  
**As a:** User  
**I want:** To share songs and playlists  
**So that:** I can recommend music  

#### ✅ Acceptance Criteria
* **AC-08.1 (Action Presence):** A share context action must accompany every playable track and curated playlist entry.
* **AC-08.2 (Link Uniqueness):** Sharable links must resolve dynamically depending on platform parameters (Web/iOS/Android deep-linking support).
* **AC-08.3 (Integration Ecosystem):** Built-in native shares must adapt to system overlays on mobile devices, or trigger standard clipboard copy backups on desktop browsers.

#### 🔍 Scenario
**Scenario 1: Generating a shareable link**
* **Given** the user selects a song  
* **When** share is clicked  
* **Then** a shareable link is copied to the clipboard and social options open.

---

### 🧪 User Story (US-09): Modern User Interface
**Epic Link:** [EPIC-07](#-epic-07--user-experience-and-interface-design)  
**As a:** User  
**I want:** A clean, responsive, and intuitive interface with Dark Mode support  
**So that:** I can use the app easily during day or night without eye strain  

#### ✅ Acceptance Criteria
* **AC-09.1 (Responsive Formats):** Viewports must scale dynamically layout metrics to support mobile, tablet, and widescreen desktop presentation frameworks.
* **AC-09.2 (Dynamic Styling):** System style sheets must support instant switches between Light and Dark mode variables without structural page resets.
* **AC-09.3 (Accessibility Compliance):** Contrast elements and structural element landmarks must conform fully to WCAG 2.1 AA screen reader standards.

#### 🔍 Scenarios
**Scenario 1: Switch to Dark Mode**
* **Given** the user is in the settings panel  
* **When** they toggle the theme switch  
* **Then** the entire interface updates to a dark color palette instantly.
