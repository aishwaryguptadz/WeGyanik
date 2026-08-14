# WeGyanik Android App

WeGyanik is a native Android application built in Kotlin that acts as a mobile client for the Wegyanik platform.

The application provides a structured Android interface for accessing platform content and dynamically loading product and project information from the Wegyanik backend through REST APIs.

## Features

- Native Android application built with Kotlin
- XML-based Android UI
- Login and signup screens
- Home screen
- Project listing
- Product/shop listing
- Dynamic product data fetched from the backend
- Dynamic project data fetched from the backend
- Product images loaded from remote URLs
- RecyclerView-based list rendering
- REST API integration using Retrofit
- JSON response parsing using Gson
- Kotlin Coroutines for asynchronous API operations
- Glide for image loading and disk caching
- Fragment-based navigation and modular screens

## Tech Stack

### Android

- Kotlin
- Android SDK
- XML Layouts
- AndroidX
- AppCompat
- Material Components
- ConstraintLayout
- Fragments
- RecyclerView

### Networking

- Retrofit 2.9.0
- Gson Converter
- Kotlin Coroutines

### Image Loading

- Glide 4.15.1
- Glide Disk Cache

### Development Tools

- Android Studio
- Gradle
- Git
- GitHub

## Architecture Overview

The application follows a component-based Android structure using Activities and Fragments.

A simplified product-data flow is:

```text
User opens Shop
        ↓
ShopFragment
        ↓
Coroutine / lifecycleScope
        ↓
RetrofitInstance
        ↓
ProductApiService
        ↓
Wegyanik REST API
        ↓
ProductApiResponse
        ↓
List<Product>
        ↓
ProductAdapter
        ↓
RecyclerView- Scalable architecture for future expansion

---

## Tech Stack

**Frontend (Android)**
- Kotlin
- XML Layouts
- Android SDK
- Material Design Components

**Backend**
- PostgreSQL Database
- REST APIs

**Tools & Environment**
- Android Studio
- Git & GitHub
- Gradle

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/aishwaryguptadz/WeGyanik
```
### 2. Open in Android Studio

- Open Android Studio
- Select Open an Existing Project
- Navigate to the cloned repository

### 3. Sync Gradle

Allow Android studio to download dependencies and sync the project.

### 4. Run the Application

Connect an Android device or start an emulator and click Run.

---

## Configuration

Update the API base URL in the network configuration file.

Example:
```kotlin
const val BASE_URL = "https://wegyanik.in/api/"
```

Make sure the backend server is running and accessible.

---

## Organization

This project is developed under:

#### Raman Research and Innovation Pvt. Ltd.

Wegyanik is an initiative focused on technology education, innovation, and research-driven learning.
