# Education-I'll build the LearnEasy project as real files and zip it for you.

Some of those writes didn't go through, so I'm re-sending them.

Cleaning up the Search screen's imports before I move on.

Two small fixes: moving logout out of the nav host and into a ViewModel, and giving `q()` an explicit return type.

The LearnEasy project is in `LearnEasy.zip`: about 3,600 lines of Kotlin across 40 files. I couldn't compile or run it here because there's no Android SDK, so Android Studio may flag a small typo or missing import on first sync.

All 12 features and the design requirements are in:
- **Navigation and design:** bottom navigation bar, blue and white theme, and light/dark/system mode.
- **Firebase:** email login, Firestore data, and PDFs from Storage. PDFs can be viewed in the app or downloaded to `Downloads/LearnEasy`.
- **Extras:** a quiz timer that auto-submits at zero, and in-app error messages for things like wrong password, no internet and a missing PDF.
- **Structure:** MVVM, with repositories handling the Firebase calls.

To run it:
1. Create a Firebase project and register the Android app with package name `com.learneasy.app`. Put the downloaded `google-services.json` in the `app/` folder.
2. Enable Email/Password sign-in, create Firestore and Storage, and paste in `firestore.rules` and `storage.rules`.
3. Open the folder in Android Studio, sync, and run on Android 10 or newer.
4. Register an account, then tap **Settings → Load sample data**. This adds 4 courses, 4 quizzes and 3 notifications.
5. Upload any PDFs to Storage under `notes/`, named `kotlin_basics.pdf`, `kotlin_functions.pdf`, `algebra_basics.pdf`, `geometry_formulas.pdf`, `motion_and_forces.pdf` and `grammar_rules.pdf`.

The Firestore rules let any signed-in user write course content so the sample-data button works. Change those `write` rules to `false` before you release the app.

The README has the testing checklist, debug and signed-release APK steps, and a troubleshooting table. Unit tests run with `./gradlew test`.