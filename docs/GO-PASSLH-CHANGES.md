# Go-PassLH changes (relative to the uploaded KeePassDX-master)

Branch `go-passlh-redesign`. Baseline commit c313ba9. Presentation-only changes; no crypto, database, manifest, package or ID changes.

## Branding
- `app/src/main/res/values/donottranslate.xml`: app_name = Go-PassLH (non-translatable, so identical in every language), wordmark parts "Go-Pass" + "LH", theme registration strings.
- `app/src/main/res/values-*/strings.xml` (54 files): brand token replaced inside existing translations. Nothing removed. License headers and the "KeePassDX © Kunzisoft" credit kept (GPLv3).

## Design system (new files, additive)
- `values/gopasslh_colors.xml`: midnight ink / warm ivory / antique gold palette, light and night. Single file to retune.
- `values/gopasslh_tokens.xml`: spacing, radii, elevation, type scale, motion durations, theme name array.
- `values/styles_gopasslh.xml`: KeepassDXStyle.GoPassLH (+ .Night): rounded shapes, medium-weight titles, flat hairline cards, transitions.
- `anim/gopasslh_*.xml` (4): activity transitions (fade + 3% slide). System animation scale applies; 0 disables them.

## Wiring
- `activities/stylish/Stylish.kt` (only Kotlin file changed): maps the new theme names to the new styles; new default for fresh installs; existing saved themes keep working.
- `xml/preferences_appearance.xml`: Go-PassLH listed first, default value updated.

## Not changed on purpose
NAME_OF_HMAC_KEY, applicationId, packages, Room schemas, database/ and crypto/ modules, manifest, notification channel name, default database name, launcher icon (no logo confirmed; no logo invented).

## Verification
See `GO-PASSLH-VERIFICATION.md`. Nothing has been built or run: no Android SDK in the authoring environment.
