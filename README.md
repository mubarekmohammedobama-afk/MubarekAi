# Mubarek AI

An Android AI chat assistant (Java, Material 3, Room, OkHttp). You bring your own API key.

**Status: Phases 1-2 of 5.** Working now: onboarding, light/dark/system theme, home screen with quick actions,
chat with Markdown rendering, streaming with Stop, edit / resend / regenerate / copy, encrypted API-key storage,
provider settings with Test connection, chat history (search, rename, pin, archive, delete), offline detection.
Providers: Anthropic, OpenAI, DeepSeek, any OpenAI-compatible endpoint.

Coming next: Gemini + custom headers, model manager, personalities, export/share, image/file attachments,
speech-to-text, text-to-speech voices, voice chat.

## Build
1. Open the folder in Android Studio (Ladybug or newer) with JDK 17 and let Gradle sync
   (Studio creates the Gradle wrapper for you).
2. Run on a device or emulator with Android 7.0 (API 24) or newer.
3. Or push to GitHub: the workflow in `.github/workflows/build.yml` builds a debug APK and uploads it as an artifact.

## Configure
Open the app > Settings > AI provider. Pick a provider, paste your API key, check the Base URL and Model ID,
tap **Save**, then **Test connection**. Model IDs change often, so they are editable and never hardcoded in logic.

## Security
- Keys are stored with EncryptedSharedPreferences (Android Keystore). They are never in source, Gradle files,
  strings.xml, logs or error messages.
- HTTPS only. A determined attacker with a rooted device may still extract keys; for production, use a backend proxy.

## Signed release
Copy `keystore.properties.example` to `keystore.properties`, fill it in, then run `gradle assembleRelease`.
