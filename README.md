# WeGyanik

<p align="center">
  <strong>Native Android Client for the WeGyanik Platform</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Android">
  <img src="https://img.shields.io/badge/Language-Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white" alt="Kotlin">
  <img src="https://img.shields.io/badge/UI-XML-1572B6?style=for-the-badge&logo=xml&logoColor=white" alt="XML">
  <img src="https://img.shields.io/badge/Networking-Retrofit-48B983?style=for-the-badge" alt="Retrofit">
  <img src="https://img.shields.io/badge/Database-PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL">
</p>

<p align="center">
  A native Android application that connects the WeGyanik platform with users through a structured mobile interface for products, projects, community content, domains, profiles, and platform offerings.
</p>

---

## Screenshots / Demo

> Screenshots can be added to this section as the project UI evolves.

|       Home       |     Projects     |       Shop       |      Profile     |
| :--------------: | :--------------: | :--------------: | :--------------: |
| *Add screenshot* | *Add screenshot* | *Add screenshot* | *Add screenshot* |

**Platform:** Android
**Backend:** WeGyanik REST API
**Minimum Android Version:** Android 7.0 / API 24
**Target Android Version:** API 35

---

## Overview

**WeGyanik** is a native Android client developed for the WeGyanik platform under **Raman Research and Innovation Pvt. Ltd.**

The application provides a mobile interface for accessing dynamically generated platform content instead of relying entirely on hardcoded application data.

The application integrates with the WeGyanik backend through REST APIs and retrieves product and project information dynamically. API responses are converted into Kotlin data models and displayed through reusable Android UI components such as `RecyclerView`, custom adapters, Activities, and Fragments.

The application is structured around a modular UI consisting of:

* Home
* Projects
* Shop / Products
* Profile
* Community
* Domain
* What We Offer
* Splash / Entry screens

The Android client communicates with the backend over HTTP/REST, while the backend handles communication with the PostgreSQL database.

### High-Level System

```text
┌──────────────────────────────┐
│       Android Application    │
│                              │
│ Kotlin + XML + Fragments     │
│ RecyclerView + Adapters      │
└──────────────┬───────────────┘
               │
               │ HTTP / REST
               ▼
┌──────────────────────────────┐
│      WeGyanik Backend        │
│                              │
│       REST API Layer         │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│        PostgreSQL            │
│          Database            │
└──────────────────────────────┘
```

The Android application does **not** directly access PostgreSQL. Database access remains on the server side behind the REST API.

---

## Features

### Application Entry

* Splash screen
* Structured application entry flow
* Native Android navigation

### Home

* Dedicated home screen
* Platform content presentation
* Navigation to major application sections
* Bottom navigation
* Navigation drawer

### Shop / Products

* Dynamic product listing
* REST API-based product retrieval
* RecyclerView-based product rendering
* Dedicated `ProductAdapter`
* Remote product image loading
* Glide-based image caching

### Projects

* Dynamic project listing
* REST API-based project retrieval
* RecyclerView-based project rendering
* Dedicated `ProjectAdapter`
* Kotlin data models for project responses

### Profile

* Dedicated profile section
* Navigation through bottom navigation and drawer

### Community

* Community section integrated into the navigation drawer

### Domain

* Domain-specific platform content

### What We Offer

* Dedicated section for platform offerings and services

### REST API Integration

* Retrofit 2.9.0
* Gson JSON conversion
* Dedicated API service interfaces
* Centralized Retrofit configuration
* Coroutine-based asynchronous requests

### Remote Image Loading

* Glide 4.15.1
* Remote image loading
* Image decoding
* Disk caching
* RecyclerView-compatible image rendering

### Asynchronous Networking

* Kotlin Coroutines
* `suspend` API functions
* Lifecycle-aware asynchronous operations
* Network operations kept away from the main UI thread

---

## Tech Stack

### Android

| Technology          | Usage                                  |
| ------------------- | -------------------------------------- |
| Kotlin              | Primary programming language           |
| Android SDK         | Native Android development             |
| XML                 | UI layouts                             |
| AndroidX            | Android support libraries              |
| AppCompat           | Backward-compatible Android components |
| Material Components | UI components                          |
| ConstraintLayout    | Responsive layouts                     |
| Fragments           | Modular UI components                  |
| RecyclerView        | Dynamic list rendering                 |

### Networking

| Technology              | Usage                               |
| ----------------------- | ----------------------------------- |
| Retrofit 2.9.0          | REST API communication              |
| Gson Converter 2.9.0    | JSON serialization/deserialization  |
| Kotlin Coroutines 1.7.1 | Asynchronous API operations         |
| `lifecycleScope`        | Lifecycle-aware coroutine execution |

### Image Loading

| Technology       | Usage                            |
| ---------------- | -------------------------------- |
| Glide 4.15.1     | Remote image loading             |
| Glide Compiler   | Glide annotation/code generation |
| Glide Disk Cache | Image caching                    |

### Backend

| Technology       | Usage                               |
| ---------------- | ----------------------------------- |
| REST API         | Android-backend communication       |
| PostgreSQL       | Backend database                    |
| WeGyanik Backend | Server-side data and business layer |

### Development Tools

* Android Studio
* Gradle
* Git
* GitHub

---

## Architecture

The current application follows a **component-based Android architecture** built around Activities, Fragments, API service interfaces, data models, and RecyclerView adapters.

It is not currently a formal MVVM/Clean Architecture implementation.

### Application Architecture

```text
                    ┌─────────────────┐
                    │      User       │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │    Activity     │
                    └────────┬────────┘
                             │
                ┌────────────┴────────────┐
                │                         │
                ▼                         ▼
        ┌───────────────┐        ┌────────────────┐
        │   Fragments   │        │ Navigation UI  │
        │               │        │ Drawer / Bottom│
        └───────┬───────┘        └────────────────┘
                │
                ▼
        ┌───────────────┐
        │    Coroutine  │
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │    Retrofit   │
        │    Instance   │
        └───────┬───────┘
                │
        ┌───────┴────────┐
        │                │
        ▼                ▼
┌───────────────┐ ┌───────────────┐
│ Product API   │ │ Project API   │
│ Service       │ │ Service       │
└───────┬───────┘ └───────┬───────┘
        │                  │
        └────────┬─────────┘
                 ▼
        ┌─────────────────┐
        │ WeGyanik REST   │
        │ Backend         │
        └────────┬────────┘
                 │
                 ▼
        ┌─────────────────┐
        │   PostgreSQL    │
        └─────────────────┘
```

### Product Data Flow

```text
ShopFragment
     │
     ▼
Kotlin Coroutine
     │
     ▼
ProductApiService
     │
     ▼
GET /api/product
     │
     ▼
WeGyanik Backend
     │
     ▼
JSON Response
     │
     ▼
Gson Converter
     │
     ▼
ProductApiResponse
     │
     ▼
List<Product>
     │
     ▼
ProductAdapter
     │
     ▼
RecyclerView
     │
     ▼
Android UI
```

### Project Data Flow

```text
ProjectFragment
     │
     ▼
Kotlin Coroutine
     │
     ▼
ProjectApiService
     │
     ▼
GET /api/project
     │
     ▼
WeGyanik Backend
     │
     ▼
JSON Response
     │
     ▼
Gson Converter
     │
     ▼
List<Project>
     │
     ▼
ProjectAdapter
     │
     ▼
RecyclerView
```

### Navigation

The main `HomeScreen` activity manages:

* Bottom navigation
* Navigation drawer
* Fragment replacement
* Toolbar / drawer toggle
* Home screen initialization

Bottom navigation provides access to:

* Home
* Projects / Explore
* Products
* Profile

The navigation drawer provides access to:

* Profile
* Community
* Domain
* What We Offer

---

## Screenshots

The repository currently does not contain a dedicated screenshots/assets gallery for the README.

Recommended screenshots to add:

```text
docs/
└── screenshots/
    ├── splash.png
    ├── home.png
    ├── projects.png
    ├── shop.png
    ├── profile.png
    └── navigation-drawer.png
```

Once added, they can be displayed using:

```markdown
### Home

![Home Screen](docs/screenshots/home.png)

### Projects

![Projects Screen](docs/screenshots/projects.png)

### Shop

![Shop Screen](docs/screenshots/shop.png)

### Profile

![Profile Screen](docs/screenshots/profile.png)
```

---

## API / Database

### API Base URL

The Android client uses the following backend base URL:

```text
https://wegyanik.in/
```

Retrofit is configured centrally in:

```text
RetrofitInstance.kt
```

### Product API

```http
GET /api/product
```

Implemented through:

```text
ProductApiService.kt
```

The endpoint returns a `ProductApiResponse`, which is converted into Kotlin model objects using Gson.

### Project API

```http
GET /api/project
```

Implemented through:

```text
ProjectApiService.kt
```

The endpoint returns a list of `Project` objects.

### Networking Layer

```kotlin
Retrofit.Builder()
    .baseUrl("https://wegyanik.in/")
    .addConverterFactory(GsonConverterFactory.create())
    .build()
```

### Database Architecture

The Android application does not connect directly to PostgreSQL.

```text
Android Client
      │
      │ REST / HTTP
      ▼
WeGyanik Backend
      │
      │ Database Operations
      ▼
PostgreSQL
```

This separation keeps database credentials and database operations on the backend rather than embedding them inside the Android application.

### Internet Permission

The application requires internet access for API communication:

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

---

## Project Structure

```text
WeGyanik/
│
├── app/
│   ├── src/
│   │   └── main/
│   │       │
│   │       ├── java/
│   │       │   └── com/
│   │       │       └── example/
│   │       │           └── wegyanik/
│   │       │               │
│   │       │               ├── CommunityFragment.kt
│   │       │               ├── DomainFragment.kt
│   │       │               ├── HomeScreen.kt
│   │       │               ├── HomeScreenFragment.kt
│   │       │               ├── Installation_for_MAC.kt
│   │       │               ├── MainActivity.kt
│   │       │               ├── MainActivity2.kt
│   │       │               │
│   │       │               ├── ProductAdapter.kt
│   │       │               ├── ProductApiService.kt
│   │       │               ├── ProductModels.kt
│   │       │               │
│   │       │               ├── ProfileFragment.kt
│   │       │               ├── Project.kt
│   │       │               ├── ProjectAdapter.kt
│   │       │               ├── ProjectApiService.kt
│   │       │               ├── ProjectFragment.kt
│   │       │               │
│   │       │               ├── RetrofitInstance.kt
│   │       │               ├── ShopFragment.kt
│   │       │               ├── WhatWeOfferFragment.kt
│   │       │               ├── bannerAdapter.kt
│   │       │               ├── home_Screen.kt
│   │       │               ├── screen1.kt
│   │       │               └── splashscreen.kt
│   │       │
│   │       ├── res/
│   │       │   ├── drawable/
│   │       │   ├── font/
│   │       │   ├── layout/
│   │       │   ├── menu/
│   │       │   ├── mipmap-anydpi-v26/
│   │       │   ├── mipmap-hdpi/
│   │       │   ├── mipmap-mdpi/
│   │       │   ├── mipmap-xhdpi/
│   │       │   ├── mipmap-xxhdpi/
│   │       │   ├── mipmap-xxxhdpi/
│   │       │   ├── values/
│   │       │   ├── values-night/
│   │       │   └── xml/
│   │       │
│   │       └── AndroidManifest.xml
│   │
│   ├── build.gradle.kts
│   └── proguard-rules.pro
│
├── gradle/
│
├── build.gradle.kts
├── gradle.properties
├── gradlew
├── gradlew.bat
├── settings.gradle.kts
├── .gitignore
└── README.md
```

### Important Components

| File                     | Responsibility                        |
| ------------------------ | ------------------------------------- |
| `HomeScreen.kt`          | Main application shell and navigation |
| `RetrofitInstance.kt`    | Centralized Retrofit configuration    |
| `ProductApiService.kt`   | Product API definition                |
| `ProjectApiService.kt`   | Project API definition                |
| `ProductModels.kt`       | Product response/data models          |
| `Project.kt`             | Project data model                    |
| `ProductAdapter.kt`      | Product RecyclerView adapter          |
| `ProjectAdapter.kt`      | Project RecyclerView adapter          |
| `ShopFragment.kt`        | Product/shop UI                       |
| `ProjectFragment.kt`     | Project listing UI                    |
| `ProfileFragment.kt`     | Profile UI                            |
| `CommunityFragment.kt`   | Community UI                          |
| `DomainFragment.kt`      | Domain UI                             |
| `WhatWeOfferFragment.kt` | Platform offerings UI                 |

---

## Setup

### Prerequisites

Install the following before running the project:

* Android Studio
* Android SDK
* JDK compatible with Java 11
* Android emulator or physical Android device
* Git
* Internet connection

### Android Configuration

The current application configuration is:

```text
compileSdk = 35
targetSdk  = 35
minSdk     = 24

Java       = 11
Kotlin JVM = 11

versionCode = 1
versionName = 1.0
```

### 1. Clone the Repository

```bash
git clone https://github.com/aishwaryguptadz/WeGyanik.git
```

### 2. Open the Project

Open Android Studio and select:

```text
File
  ↓
Open
  ↓
WeGyanik
```

Allow Android Studio to index the project.

### 3. Sync Gradle

Use:

```text
File → Sync Project with Gradle Files
```

Wait for Gradle dependency resolution to complete.

### 4. Verify Backend Configuration

The Retrofit base URL is configured in:

```text
app/src/main/java/com/example/wegyanik/RetrofitInstance.kt
```

Current base URL:

```text
https://wegyanik.in/
```

### 5. Connect an Android Device

Either:

* Connect a physical Android device with USB debugging enabled, or
* Start an Android emulator.

### 6. Run the Application

From Android Studio:

```text
Run → Run 'app'
```

The application will build and install on the selected device.

---

## My Role

### Android Application Development

My primary role in the WeGyanik project was **Android application development**.

Key responsibilities included:

* Developing Android screens using Kotlin and XML.
* Implementing Activity- and Fragment-based UI components.
* Building the application navigation structure.
* Implementing product and project listing screens.
* Integrating REST APIs using Retrofit.
* Creating API service interfaces for products and projects.
* Handling JSON responses using Gson.
* Implementing asynchronous API operations using Kotlin Coroutines.
* Creating reusable RecyclerView adapters.
* Rendering dynamically retrieved product and project data.
* Integrating Glide for remote image loading and caching.
* Working with product and project data models.
* Connecting the Android client with the WeGyanik backend.
* Managing Android resources and application components.
* Working with Git and GitHub for source-code management.

### Backend / Database Integration

The Android application was integrated with a backend architecture backed by PostgreSQL.

My work on the Android side involved consuming the backend's REST APIs rather than directly accessing the PostgreSQL database.

```text
Android Development
       │
       ├── Kotlin
       ├── XML
       ├── Fragments
       ├── RecyclerView
       ├── Retrofit
       ├── Gson
       ├── Coroutines
       └── Glide
              │
              ▼
       WeGyanik REST API
              │
              ▼
          PostgreSQL
```

---

## Future Improvements

The current implementation provides a functional foundation that can be evolved into a more scalable production architecture.

### Architecture

* [ ] Introduce MVVM architecture.
* [ ] Add ViewModels for UI state management.
* [ ] Introduce a Repository layer.
* [ ] Separate presentation, domain, and data layers.
* [ ] Introduce the Android Navigation Component.
* [ ] Add dependency injection using Hilt.

### Networking

* [ ] Improve API error handling.
* [ ] Add centralized network error states.
* [ ] Add loading states and skeleton screens.
* [ ] Add network connectivity handling.
* [ ] Introduce request/response logging for development.
* [ ] Improve API abstraction.

### Product Experience

* [ ] Add product detail screens.
* [ ] Add product search.
* [ ] Add product filtering and sorting.
* [ ] Add shopping cart functionality.
* [ ] Add order management.
* [ ] Add user authentication and session management.

### Data & Performance

* [ ] Add Room for local persistence.
* [ ] Implement offline-first caching.
* [ ] Add Paging for large product/project lists.
* [ ] Improve image loading and caching strategies.

### Quality

* [ ] Expand unit test coverage.
* [ ] Add API/data-model tests.
* [ ] Add Fragment navigation tests.
* [ ] Add RecyclerView UI tests.
* [ ] Add integration testing.
* [ ] Add CI/CD automation.
* [ ] Configure production release signing.

### UI / UX

* [ ] Improve responsive layouts across screen sizes.
* [ ] Improve loading and empty states.
* [ ] Add better error feedback.
* [ ] Improve accessibility.
* [ ] Modernize the UI while maintaining the existing platform identity.

---

## License

No explicit open-source license is currently specified in the repository.

Therefore, unless a license is added to the repository, the source code should **not be assumed to be freely reusable, modified, or redistributed**.

If this project is intended to be open source, an appropriate license such as **MIT**, **Apache-2.0**, or another license should be added through a `LICENSE` file.

---

## Acknowledgements

* Android SDK
* Kotlin
* AndroidX
* Material Components
* Retrofit
* Gson
* Kotlin Coroutines
* Glide
* Raman Research and Innovation Pvt. Ltd.
* WeGyanik

---

<p align="center">
  Built with Kotlin and Android
</p>

<p align="center">
  If you find this project useful, consider starring the repository.
</p>
