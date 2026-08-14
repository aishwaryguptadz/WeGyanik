# WeGyanik Android App

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android-green?style=for-the-badge&logo=android" alt="Android">
  <img src="https://img.shields.io/badge/Language-Kotlin-purple?style=for-the-badge&logo=kotlin" alt="Kotlin">
  <img src="https://img.shields.io/badge/UI-XML-blue?style=for-the-badge&logo=android" alt="XML">
  <img src="https://img.shields.io/badge/API-REST-orange?style=for-the-badge" alt="REST API">
  <img src="https://img.shields.io/badge/Retrofit-2.9.0-red?style=for-the-badge" alt="Retrofit">
</p>

<p align="center">
  <b>Native Android client for the WeGyanik platform</b>
</p>

<p align="center">
  A Kotlin-based Android application that provides a structured mobile interface for
  accessing WeGyanik platform content, projects, products, and other services through
  REST APIs.
</p>

---

## About the Project

**WeGyanik** is a native Android application developed as a mobile client for the **Wegyanik platform**.

The application provides users with a structured Android interface for exploring platform content, projects, products, and other offerings. Dynamic data is retrieved from the backend through REST APIs and displayed using Android UI components such as `RecyclerView`, `Fragments`, and custom adapters.

The project was developed under:

**Raman Research and Innovation Pvt. Ltd.**

The Android application communicates with the Wegyanik backend and consumes dynamically generated product and project information instead of relying entirely on hardcoded application data.

---

## Project Objectives

The primary objectives of the application are:

- Provide a native Android interface for the WeGyanik platform.
- Display dynamic product and project information.
- Integrate Android applications with RESTful backend services.
- Implement asynchronous network operations using Kotlin Coroutines.
- Parse JSON API responses into Kotlin data models.
- Display remote images efficiently using Glide.
- Organize application functionality using Activities and Fragments.
- Provide reusable list components using RecyclerView and adapters.
- Build a scalable foundation for extending the mobile application.

---

## Features

### User Interface

- Login screen
- Signup screen
- Splash screen
- Home screen
- Profile section
- Community section
- Domain section
- What We Offer section

### Product & Shop

- Shop/product listing
- Dynamic product data
- Product images loaded from remote URLs
- RecyclerView-based product rendering
- Dedicated product adapter
- REST API integration for product data

### Projects

- Project listing
- Dynamic project data
- Remote project information
- RecyclerView-based project rendering
- Dedicated project adapter
- REST API integration

### API Integration

- REST API communication using Retrofit
- Gson-based JSON deserialization
- Kotlin Coroutines for asynchronous operations
- Dedicated API service interfaces
- Centralized Retrofit configuration

### Image Loading

- Glide integration
- Remote image loading
- Disk caching through Glide
- Efficient image rendering inside RecyclerView items

### Android Architecture

- Activity-based application entry points
- Fragment-based modular screens
- RecyclerView for scalable list rendering
- Separate API service interfaces
- Dedicated model classes
- Dedicated adapters for dynamic lists

---

## High-Level Architecture

The application follows a component-based Android architecture built around Activities, Fragments, API service interfaces, model classes, and RecyclerView adapters.

### Product Data Flow

```text
┌─────────────────────┐
│      User           │
│   Opens Shop        │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│   ShopFragment      │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│ Kotlin Coroutine    │
│ / lifecycleScope    │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│ RetrofitInstance    │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│ ProductApiService   │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│   REST API          │
│   Wegyanik Backend  │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│ ProductApiResponse  │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│    List<Product>    │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│  ProductAdapter     │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│    RecyclerView     │
└─────────────────────┘
```

### API Communication Flow

The general networking flow is:

```text
Fragment
   │
   ▼
Coroutine
   │
   ▼
Retrofit
   │
   ▼
API Service Interface
   │
   ▼
HTTP Request
   │
   ▼
Wegyanik Backend
   │
   ▼
JSON Response
   │
   ▼
Gson Converter
   │
   ▼
Kotlin Data Model
   │
   ▼
RecyclerView Adapter
   │
   ▼
Android UI
```

This approach keeps API communication separate from the UI rendering components and makes the networking layer easier to maintain.

---

## Technology Stack

### Android

| **Technology** | **Purpose** |
|---|---|
| Kotlin | Primary programming language |
| Android SDK | Android application development |
| XML | UI layouts |
| AndroidX | Android support libraries |
| AppCompat | Backward-compatible Android components |
| Material Components | UI components and Material Design |
| ConstraintLayout | Responsive UI layouts |
| Fragments | Modular screen architecture |
| RecyclerView | Dynamic list rendering |

### Networking

| **Technology** | **Purpose** |
|---|---|
| Retrofit 2.9.0 | REST API communication |
| Gson Converter | JSON serialization/deserialization |
| Kotlin Compose | Asynchronous operations |
| lifecycleScope | Lifecycle-aware coroutine execution |

### Image Loading

| **Technology** | **Purpose** |
|---|---|
| Glide 4.15.1 | Remote image loading |
| Glide Disk Cache | Image caching |

### Development Tools

- Android Studio
- Gradle
- Git
- GitHub

---

## Dependencies

The project currently uses the following major dependencies:

- AndroidX Core KTX
- AndroidX AppCompat
- Material Components
- AndroidX Activity
- ConstraintLayout
- AndroidX Fragment
- Retrofit 2.9.0
- Retrofit Gson Converter 2.9.0
- Kotlin Coroutines Android 1.7.1
- Glide 4.15.1
- Glide Compiler 4.15.1

---

## Project Structure

The repository follows a standard Android project structure.

```text
WeGyanik/
│
├── app/
│   │
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
│   │       │               ├── ProductAdapter.kt
│   │       │               ├── ProductApiService.kt
│   │       │               ├── ProductModels.kt
│   │       │               ├── ProfileFragment.kt
│   │       │               ├── Project.kt
│   │       │               ├── ProjectAdapter.kt
│   │       │               ├── ProjectApiService.kt
│   │       │               ├── ProjectFragment.kt
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

---

## Important Components

```text
MainActivity.kt
```

Primary Android activity responsible for application-level navigation and initialization.
<br>
<br>
```text
MainActivity2.kt
```

Additional activity used by the application for a separate application flow/screen.
<br>
<br>
```text
RetrofitInstance.kt
```

Centralized Retrofit configuration used for communicating with the backend APIs.

Conceptually:

```text
Application
     │
     ▼
RetrofitInstance
     │
     ├──────────────► ProductApiService
     │
     └──────────────► ProjectApiService
```

<br>

```text
ProductApiService.kt
```

Defines the Retrofit endpoints used for retrieving product-related information from the backend.

<br>

```text
ProjectApiService.kt
```

Defines the Retrofit endpoints used for retrieving project-related information.

<br>

```text
ProductModels.kt
```

Contains the Kotlin model structures required for representing product API responses.

<br>

```text
Project.kt
```

Contains the project-related data model used by the application.

<br>

```text
ProductAdapter.kt
```

RecyclerView adapter responsible for converting product data into Android UI list items.

Responsibilities include:

- Receiving product data.
- Creating/binding product list items.
- Loading product images.
- Displaying product information.

<br>

```text
ProjectAdapter.kt
```

RecyclerView adapter responsible for rendering project information in the project listing.

<br>

```text
ShopFragment.kt
```

Fragment responsible for the shop/product section.

The general flow is:

```text
ShopFragment
      │
      ▼
Coroutine
      │
      ▼
ProductApiService
      │
      ▼
Backend API
      │
      ▼
Product Models
      │
      ▼
ProductAdapter
      │
      ▼
RecyclerView
```

<br>

```text
ProjectFragment.kt
```

Fragment responsible for displaying project-related information retrieved from the backend.

<br>

```text
HomeScreenFragment.kt
```

Provides the application's home-screen functionality and acts as one of the primary user-facing screens.

<br>

```text
ProfileFragment.kt
```

Handles the profile section of the Android application.

<br>

```text
CommunityFragment.kt
````

Provides the community-related section of the application.

<br>

```text
DomainFragment.kt
```

Provides domain-related application content.

<br>

```text
WhatWeOfferFragment.kt
```

Displays the offerings/services provided through the platform.

## Backend Integration

The Android application communicates with the Wegyanik backend through REST APIs.

The backend architecture uses:

```text
Android Application
        │
        │ HTTP / REST
        ▼
Wegyanik Backend
        │
        ▼
REST API
        │
        ▼
PostgreSQL Database
```

The Android client does not directly access the PostgreSQL database.

Instead:

```text
Android
   │
   ▼
REST API
   │
   ▼
Backend
   │
   ▼
PostgreSQL
```

This separation keeps database access on the server side and allows the Android client to communicate through defined API contracts.

## API Base URL

The application is configured to communicate with the Wegyanik backend.

Example base URL:

```kotlin
const val BASE_URL = "https://wegyanik.in/api/"
```

The exact API endpoints and server configuration may change depending on the backend deployment.

---

## Installation & Setup

### Prerequisites

Before running the project, make sure you have:

- Android Studio installed.
- Android SDK configured.
- JDK compatible with the project's Java/Kotlin configuration.
- An Android emulator or physical Android device.
- Internet access for API requests and Gradle dependencies.

### 1. Clone Repository

```bash
git clone https://github.com/aishwaryguptadz/WeGyanik.git
```

Move into the project directory:

```bash
cd WeGyanik
```

### 2. Open the Project

Open Android Studio.

Select:

```text
File
  ↓
Open
  ↓
WeGyanik
```

Allow Android Studio to index the project.

### 3. Sync Gradle

Android Studio should automatically detect the Gradle configuration.

If required:

```text
File → Sync Project with Gradle Files
```

Wait until dependency resolution and project synchronization are complete.

### 4. Configure the Backend

Wait until dependency resolution and project synchronization are complete.

Example:

```kotlin
const val BASE_URL = "https://wegyanik.in/api/"
```

### 5. Run the Application

Connect an Android device or launch an emulator.

Then select:

```text
Run → Run 'app'
```

The application will be built and installed on the selected Android device.

---

## Application Flow

A simplified user flow is:

```text
Splash Screen
      │
      ▼
Home
      │
      ├──────────────► Profile
      │
      ├──────────────► Community
      │
      ├──────────────► Domain
      │
      ├──────────────► What We Offer
      │
      ├──────────────► Projects
      │
      └──────────────► Shop
                         │
                         ▼
                  Product Listing
                         │
                         ▼
                    API Request
                         │
                         ▼
                  Product Response
                         │
                         ▼
                   RecyclerView
```

---

## Asynchronous Programming

Network requests are performed asynchronously using Kotlin Coroutines.

Instead of blocking the Android main thread:

```text
UI Thread
   │
   ├── UI rendering
   │
   └── Coroutine
          │
          ▼
      API request
          │
          ▼
      API response
          │
          ▼
      Update UI
```

This prevents long-running network operations from blocking the user interface.

---

## Image Loading

Product and other remote images are loaded using Glide.

General flow:

```text
Remote Image URL
       │
       ▼
     Glide
       │
       ├── Download
       │
       ├── Cache
       │
       └── Decode
       │
       ▼
   ImageView
```

Glide's caching capabilities help reduce unnecessary repeated image downloads.

---

## RecyclerView Implementation

The application uses RecyclerView for dynamic product and project lists.

### Product List

```text
API Response
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
     ├── Product Item
     ├── Product Item
     ├── Product Item
     └── Product Item
```

### Project List

```text
API Response
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

Using adapters allows the application to reuse the same item layout for dynamically retrieved data.

---

## Key Technical Concepts Demonstrated

This project demonstrates practical implementation of:

- Native Android development
- Kotlin programming
- XML-based UI development
- Activity lifecycle
- Fragment lifecycle
- Fragment-based navigation
- RecyclerView
- Custom RecyclerView adapters
- REST API integration
- Retrofit
- Gson
- Kotlin Coroutines
- Lifecycle-aware asynchronous operations
- JSON parsing
- Remote image loading
- Glide
- Disk caching
- Gradle dependency management
- Android resource management
- Git and GitHub

---

## Security Considerations

The application follows a client-server architecture where the Android client communicates with backend APIs instead of connecting directly to the database.

```text
Android Client
      │
      ▼
REST API
      │
      ▼
Backend
      │
      ▼
Database
```

Sensitive backend/database credentials should remain on the server and should not be embedded in the Android application.

For production deployment, additional measures such as HTTPS enforcement, secure authentication, token management, input validation, API authorization, and secure secret management should be implemented at the backend/client boundary as required.

---

## Future Improvements

The current application provides the foundation for further development.

Potential improvements include:

- [ ] MVVM architecture
- [ ] ViewModel-based state management
- [ ] Repository layer
- [ ] Android Navigation Component
- [ ] Dependency Injection using Hilt
- [ ] Paging for large product/project lists
- [ ] Search functionality
- [ ] Product detail screen
- [ ] Shopping cart
- [ ] Order management
- [ ] Persistent local storage
- [ ] Room database
- [ ] Offline-first caching
- [ ] Improved error handling
- [ ] Loading states and skeleton screens
- [ ] Network connectivity handling
- [ ] Automated unit testing
- [ ] UI testing
- [ ] CI/CD pipeline
- [ ] Release signing and production deployment

---

## Testing

The project is configured with Android testing dependencies including:

- JUnit
- AndroidX JUnit
- Espresso

Testing can be expanded to cover:

```text
Unit Tests
   │
   ├── API response parsing
   ├── Data models
   └── Business logic

UI Tests
   │
   ├── Fragment navigation
   ├── RecyclerView rendering
   └── User interactions

Integration Tests
   │
   └── API ↔ Android integration
```

---

## Scalability

The current separation between:

```text
UI
│
├── Fragments
│
├── Adapters
│
└── Activities

Networking
│
├── RetrofitInstance
│
├── ProductApiService
│
└── ProjectApiService

Models
│
├── ProductModels
│
└── Project
```

provides a foundation that can be extended into a more formal layered architecture.

A future architecture could evolve toward:

```text
Presentation Layer
        │
        ▼
    ViewModel
        │
        ▼
   Repository
        │
        ├──────────────► Remote Data Source
        │                       │
        │                       ▼
        │                   REST API
        │
        └──────────────► Local Data Source
                                │
                                ▼
                              Room
```

This would make the application easier to test, maintain, and scale.

---

## My Role

**Android Application Development**

Responsibilities included:

- Developing Android application screens using Kotlin and XML.
- Implementing Fragment-based UI components.
- Integrating REST APIs into the Android application.
- Working with Retrofit for network communication.
- Handling JSON responses using Gson.
- Implementing asynchronous API operations using Kotlin Coroutines.
- Creating RecyclerView adapters for dynamic content.
- Integrating Glide for remote image loading and caching.
- Connecting the Android client with the Wegyanik backend.
- Working with product and project data models.
- Managing Android resources and application components.
- Using Git and GitHub for source-code management.

---

## Organization

This project was developed under:

**Raman Research and Innovation Pvt. Ltd.**

Wegyanik is an initiative focused on technology education, innovation, and research-driven learning.

---

## Learning Outcomes

Through this project, the following practical development skills were applied:

- Building native Android applications with Kotlin.
- Designing Android UIs using XML.
- Understanding Activity and Fragment lifecycles.
- Consuming RESTful APIs from Android.
- Working with Retrofit.
- Parsing JSON using Gson.
- Performing asynchronous operations with Coroutines.
- Rendering dynamic data using RecyclerView.
- Implementing reusable RecyclerView adapters.
- Loading and caching remote images with Glide.
- Structuring Android source code into reusable components.
- Working with Gradle dependencies.
- Managing source code with Git and GitHub.
- Integrating a mobile client with a backend system.

---

## License

No explicit open-source license is currently specified in this repository.

---

## Acknowledgements

- Android SDK
- Kotlin
- AndroidX
- Material Components
- Retrofit
- Gson
- Kotlin Coroutines
- Glide
- Raman Research and Innovation Pvt. Ltd.
- Wegyanik

---

<p align="center"> <b>Built with Kotlin and Android</b> </p> <p align="center"> If you found this project useful, consider giving the repository a ⭐ </p>
