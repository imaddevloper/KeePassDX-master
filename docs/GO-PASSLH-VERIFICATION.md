# Go-PassLH verification record

Status legend: EXECUTED = run here with evidence. NOT EXECUTED = not run; do it before release.

## Environment limits (checked on 2026-10-28)
JDK 21 present. No Android SDK, no Gradle distribution or cache, no network. Gradle 8.14.2 and AGP 8.13.2 must be downloaded.
Result: the app has NOT been built and NO runtime test has been run in this environment.

## Protected, unchanged (verify with `git diff c313ba9 -- '*.kt' '*.kts' '*.java'` -> must be empty or UI-only)
NAME_OF_HMAC_KEY, applicationId (com.kunzisoft.keepass, suffix .libre), package names, Room schemas,
`database/` and `crypto/` modules, kdbx format code, manifest permissions/services.

## Commands (on a machine with Android Studio / SDK 36)
    ./gradlew :app:assembleLibreDebug
    ./gradlew :app:testLibreDebugUnitTest :database:test :crypto:test
    ./gradlew :app:lintLibreDebug
    adb install -r app/build/outputs/apk/libre/debug/*.apk

## Checklist
| # | Check | Status |
|---|-------|--------|
| 1 | assembleLibreDebug succeeds | NOT EXECUTED |
| 2 | Open and unlock a .kdbx made by original KeePassDX (use a COPY) | NOT EXECUTED |
| 3 | Entries, groups, attachments intact; save and reopen; original file untouched | NOT EXECUTED |
| 4 | Biometric / device unlock | NOT EXECUTED |
| 5 | Autofill and credential provider in another app | NOT EXECUTED |
| 6 | Passkeys (Android 14+ device) | NOT EXECUTED |
| 7 | Light and dark themes, legacy themes, launcher icon | NOT EXECUTED |
| 8 | logcat clean of crashes, resource errors, secrets | NOT EXECUTED |
| 9 | Unit tests and lint | NOT EXECUTED |
| - | Resource XML well-formed (python xml parse, 54 strings files + tokens) | EXECUTED |
| - | Kotlin changed ONLY in Stylish.kt (theme lookup, 8 added lines); R.string/R.style refs exist (script check) | EXECUTED |
| - | 220 new resource references resolve; theme arrays have equal length (10/10/10) | EXECUTED |
| 10 | Fresh install defaults to Go-PassLH; existing users keep their saved theme (Forest etc.) | NOT EXECUTED |
| 11 | Settings > Appearance lists Go-PassLH first and selecting it switches light/dark correctly | NOT EXECUTED |
| 13 | Cards show hairline border, titles medium weight, palette contrast (light and night) on every screen | NOT EXECUTED |
| 12 | Screen transitions animate; disabled when system animation scale is 0 | NOT EXECUTED |

Test only with copies of real databases. Existing installs update in place only if the signing key and applicationId match.
