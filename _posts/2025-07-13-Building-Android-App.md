---
layout : post 
title : learning to build android apps
date : 2025-07-13
---

## ✅ Android Apps Overview

### 📦 Latest Stack (Modern Android)
- `Kotlin` – Primary programming language (safer, more concise than Java)
- `Jetpack Compose` – Modern declarative UI toolkit (replaces XML-based layouts)
- `Hilt` – For dependency injection
- `Coroutines` / `Flow` – For async programming

### 📦 Earlier Stack (Legacy / Still Used)
- `Java` – Core logic
- `XML` – UI layout files (`activity_main.xml`, etc.)
- `Dagger` – Dependency injection (manual setup)
- `RxJava` – For async/reactive programming

---

## ⚙️ What is Gradle?

Gradle is a **build automation tool and project dependency manager**. It:

- Defines **how to build** your app (compile code, process resources, sign APKs, etc.)
- Manages and downloads dependencies (libraries, plugins)
- Ensures **consistent builds** with **gradle wrapper**
- Orchestrates tasks like testing, packaging, and deployment

> 📁 It looks for `build.gradle` or `build.gradle.kts` in the project

---

## 🔧 Kotlin Compilation

- Kotlin source files (`.kt`) are compiled by `kotlinc`
- Compose UI is handled by the **Jetpack Compose Compiler**, which wraps Kotlin’s compiler and adds UI support
- Result: JVM `.class` files → converted into DEX bytecode by Android tooling

---
Initialize gradle for your project: 

```
gradle init : If it doesnt have gradle build 
gradle wrapper --gradle-version 8.4 : If it has /gradlew  
gradlew : gradle wrapper
```


Build the App: 
```
./gradlew clean build
```

  


