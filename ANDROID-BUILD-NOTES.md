# LineGuard Android build handoff

This is the original LineGuard Expo app source, prepared for an Android APK build. It preserves the original app's four-tab navigation:

- Feed
- My Cases
- Community
- Profile

It does not include a Reels screen or Google Sign-In. Do not merge in the separate Reels-style native prototype; it is not the app the user asked to reproduce.

## Build an APK with GitHub Actions

The repository includes `.github/workflows/android-apk.yml`.

1. Upload/push this complete project to the user's GitHub repository (keep the root folder contents at repository root, including `pnpm-workspace.yaml`, `pnpm-lock.yaml`, `lib/`, `artifacts/`, and `.github/`).
2. In GitHub, open **Actions → Build LineGuard Android APK → Run workflow**.
3. When the workflow completes successfully, open the run and download the `lineguard-android-apk` artifact. The APK is inside that downloaded artifact.

The workflow has not yet been run from this environment, so no newly built APK is being claimed here.

## Important production limitations to resolve before public release

- The recovered original `artifacts/lineguard/context/AppContext.tsx` uses local AsyncStorage demo accounts. It is not Firebase Authentication and does not sync accounts between devices. Do not use real or reused passwords with this demo auth.
- The recovered source contains payment-related UI/data fields, but no verified Stripe checkout/server integration was found in this source archive. Preserve/restore the original Stripe backend integration from its authoritative source before claiming live payments work. Never put Stripe secret keys in the mobile app.
- The Firebase Web config supplied separately belongs to project `lineguard-68bb0`, but this original source does not currently initialize Firebase Authentication. Merely inserting the Firebase web config does not convert the local demo auth into Firebase auth.

## Verification still required

After building, install on a physical Android device and verify the four tabs, sign-up/sign-in/sign-out, report submission, media/location permissions, community membership/posts, case details, profile, and any restored payment flow. Treat the APK as a test build until these checks pass.
