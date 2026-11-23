<h1 align="center">UserGithub</h1>

<p align="center">
  Android app to browse GitHub users, view profiles, and explore followers/following via the GitHub REST API.<br>
  <strong><a href="#usage">Explore UserGithub usage Â»</a></strong>
  <br><br>
  <a href="https://github.com/7z1x/UserGithub/issues/new?labels=bug">Report bug</a>
  Â·
  <a href="https://github.com/7z1x/UserGithub/issues/new?labels=enhancement">Request feature</a>
  Â·
  <a href="https://github.com/7z1x/UserGithub">Repository</a>
</p>

<p align="center">
  <a href="https://kotlinlang.org/"><img src="https://img.shields.io/badge/Kotlin-1.9-purple?logo=kotlin&logoColor=white" alt="Kotlin"></a>
  <a href="https://developer.android.com/"><img src="https://img.shields.io/badge/Android-SDK%2034-green?logo=android&logoColor=white" alt="Android"></a>
  <a href="https://square.github.io/retrofit/"><img src="https://img.shields.io/badge/API-Retrofit-blue" alt="Retrofit"></a>
  <a href="https://developer.android.com/topic/libraries/architecture/viewmodel"><img src="https://img.shields.io/badge/Arch-MVVM-orange" alt="MVVM"></a>
</p>

---

## Overview

**UserGithub** is an Android application that consumes the public GitHub REST API to search
users, display detailed profiles, and list followers/following. The app is built with
**Kotlin**, uses **Retrofit** for networking, and follows the **MVVM** pattern with
**LiveData** and **ViewModel** for lifecycle-aware state management.

### How it works

1. **Search** â€” `MainViewModel` calls `ApiService` via Retrofit to fetch GitHub users.
2. **Display** â€” results are rendered in `UserAdapter` inside `MainActivity`.
3. **Detail** â€” tapping a row opens `DetailActivity` with `DetailViewModel` loading profile data.
4. **Follow lists** â€” `FollowFragment` + `SectionsPagerAdapter` (ViewPager2) show
   followers/following in swipeable tabs.

---

## Files

- **[README.md](README.md)** â€” the file you are currently reading.
- **[app/build.gradle.kts](app/build.gradle.kts)** â€” module config and dependencies.
- **app/src/main/java/com/dicoding/usergihub/**
  - `data/response/` â€” `UserResponse.kt`, `DetailUserResponse.kt` (API models).
  - `data/retrofit/` â€” `ApiConfig.kt`, `ApiService.kt` (Retrofit setup + endpoints).
  - `ui/UserAdapter.kt` â€” RecyclerView adapter.
  - `ui/main/` â€” `MainActivity.kt`, `MainViewModel.kt`.
  - `ui/detail/` â€” `DetailActivity.kt`, `DetailViewModel.kt`.
  - `ui/follow/` â€” `FollowFragment.kt`, `FollowViewModel.kt`, `SectionsPagerAdapter.kt`.
- **app/src/main/res/layout/** â€” XML layouts (`activity_main`, `activity_detail`,
  `fragment_follow`, `item_row_user`).
- **app/src/main/res/drawable/** â€” icons and launcher assets.

---

## Requirements

- **Android Studio** (Giraffe or newer)
- **JDK 17**
- **Android SDK 34** (minSdk 24, targetSdk 33)

| Package | Purpose |
|---|---|
| [Retrofit 2](https://square.github.io/retrofit/) + Gson converter | REST API calls |
| [Glide](https://github.com/bumptech/glide) | Image loading & caching |
| [OkHttp Logging Interceptor](https://square.github.io/okhttp/) | Debug network logs |
| [CircleImageView](https://github.com/hdodenhof/CircleImageView) | Rounded avatars |
| [ViewPager2](https://developer.android.com/jetpack/androidx/releases/viewpager2) | Followers/following tabs |
| AndroidX Lifecycle ViewModel | MVVM state holder |

---

## Installing

```bash
git clone https://github.com/7z1x/UserGithub.git
cd UserGithub
```

Open the project in **Android Studio**, let Gradle sync, then run on an emulator or device:

```bash
./gradlew assembleDebug
```

---

## Usage

1. Launch the app â€” the main screen lists GitHub users.
2. Tap any user to open the **detail** screen (avatar, name, followers, following).
3. Open the **followers/following** tab and swipe between pages.
4. Rotate the device to verify configuration changes are handled by ViewModel + LiveData.

---

## Acknowledgements

Built as a Dicoding submission using the free
[GitHub REST API](https://docs.github.com/en/rest) and
[Android Jetpack](https://developer.android.com/jetpack) libraries.
