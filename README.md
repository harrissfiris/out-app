# Out! — Plan Outings with Friends

Out! is a cross-platform mobile app, built with Flutter and Firebase, for discovering activities and organising outings with friends. Users pick their interests, browse activities near them, turn an activity into a plan, invite friends or a whole group, and keep track of everything on a shared calendar.

Developed for the *Human–Computer Interaction* course, School of Electrical and Computer Engineering, NTUA.

| Welcome | Home | Login |
|---|---|---|
| ![Welcome](assets/IMG_0452%202.PNG) | ![Home](assets/IMG_0454%202.PNG) | ![Login](assets/IMG_0453.PNG) |

## Features

- **Accounts:** sign-up, login and password reset with Firebase Authentication, plus onboarding with personal interests.
- **Discover:** a home feed of activities that match your interests and use the device's location, and search by activity name or organiser.
- **Plans:** create a plan from an activity, add participants, confirm it, and see the arranged plans.
- **Groups:** create groups of friends, add members, and plan outings with the whole group.
- **Calendar:** a monthly calendar with all upcoming plans.
- **Friends:** find friends, view their profiles, and add them by scanning their profile QR code.
- **Profile:** avatar selection, profile settings, and a personal QR code.

**Stack:** Flutter (Dart), Firebase Authentication, Cloud Firestore, Firebase Storage, `table_calendar`, `qr_flutter`, `mobile_scanner`, `geolocator`.

Data lives in Firestore collections for `users`, `activities`, `plans` and `group`. Images are stored in Firebase Storage. `lib/admin_functions/` contains Node.js scripts (Firebase Admin SDK) for managing activities and users.

## Project structure

```
lib/
  main.dart, main_app.dart   app entry point and routes
  screens/
    login_pages/             welcome, login, sign-up, password reset, interests
    main_pages/              home, search, calendar, groups, profile
    plan_pages/              activity details, plan creation, participants, confirmation
    team_pages/              groups and members
    profile_pages/           friends, avatar, settings, QR scanner
  widgets/                   shared UI components
  admin_functions/           Firebase Admin scripts
assets/                      images, icons and screenshots
```

## Running locally

Requirements: the [Flutter SDK](https://docs.flutter.dev/get-started/install) and an emulator or a device.

The app needs your own Firebase project with **Authentication** (email and password), **Cloud Firestore** and **Storage** enabled. The repository does not include any Firebase configuration files or credentials.

```bash
git clone https://github.com/harrissfiris/out-app.git
cd out-app
flutter pub get

# Connect your Firebase project (generates lib/firebase_options.dart and the platform config files)
dart pub global activate flutterfire_cli
flutterfire configure

flutter run
```

To use the admin scripts, download a service account key from your Firebase project into `lib/admin_functions/serviceAccountKey.json`. The file is git-ignored.
