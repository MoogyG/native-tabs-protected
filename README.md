# `Stack.Protected` under `NativeTabs` is silently ignored

Minimal reproduction for Expo Router 58.0.23 (Expo SDK 58), created with `npx create-expo-app@latest --template blank-typescript`, then Expo Router added following the manual installation guide.

`src/app/_layout.tsx` declares a `NativeTabs` layout with two triggers. The `settings` trigger is wrapped in `<Stack.Protected guard={true}>`.

## Steps

1. `npm install`
2. `npx expo start`, then open the project in Expo Go (iOS simulator).

## Expected

`guard` is `true`, so both tabs, **Home** and **Settings**, are shown. If `.Protected` is not supported under `NativeTabs`, a development warning says so.

## Observed

- Only the **Home** tab is shown.
- Tapping **Go to /settings** does nothing.
- Nothing is logged in the Metro console or in the app.

Removing the `Stack.Protected` wrapper shows both tabs, and the link opens **Settings**.
