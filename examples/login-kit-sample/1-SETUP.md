# 🔧 1. Setup & Prerequisites — Snapchat Login Kit Sample

> Get your tools ready to build and run the Login Kit Sample apps.

---

## ✅ Required Tools

| Tool | Purpose | Install |
|------|---------|---------|
| **Android Studio** | Build & run the Android sample | [Download](https://developer.android.com/studio) |
| **Xcode** (macOS only) | Build & run the iOS sample | [Mac App Store](https://developer.apple.com/xcode/) |
| **Node.js** | Required for React Native sample | `brew install node` or [Download](https://nodejs.org/) |
| **Yarn** | JS dependency management (React Native) | `brew install yarn` or `npm install -g yarn` |
| **CocoaPods** | iOS dependency management | `brew install cocoapods` or `gem install cocoapods` |
| **JDK 8+** | Android builds | `brew install --cask adoptopenjdk/openjdk/adoptopenjdk8` |
| **Git** | Version control | `winget install Git.Git` |
| **Snapchat App** | Required to test OAuth login | [App Store](https://apps.apple.com/app/snapchat/id447188370) / [Google Play](https://play.google.com/store/apps/details?id=com.snapchat.android) |

## 🔑 Snap Kit Developer Portal Registration

> **This is mandatory before running any sample app.**

1. Go to [Snap Kit Developer Portal](https://kit.snapchat.com/portal/)
2. Sign in with your Snapchat account
3. Create a **New Project** (or open an existing one)
4. You'll receive **two OAuth Client IDs**:

| OAuth Client ID | Usage |
|-----------------|-------|
| **Production** | Works with any Snapchat account (requires app approval) |
| **Staging/Development** | Works only with accounts listed under **Demo Users** (no approval needed) |

5. Under **Versions**, enable **Login Kit**
6. Under **User Permissions**, check the scopes you need:
   - ✅ Display Name
   - ✅ Bitmoji Avatar
   - ✅ External ID
7. Set up your **Redirect URI** (e.g., `snapkitexample://main/auth`)
8. Add your Snapchat username to **Demo Users** for testing

---

## 🚀 Clone & Initial Setup

```bash
# 1. Clone the repo
git clone https://github.com/Snapchat/login-kit-sample.git
cd login-kit-sample

# 2. The repo has 3 independent sample apps:
#    android/        → Native Android (Java)
#    ios/            → Native iOS (Swift)
#    react-native/   → React Native (TypeScript)
```

---

## 📱 Platform-Specific Setup

### Android Setup

```bash
cd android/

# Open in Android Studio
# File → Open → select the android/ folder

# Key files to configure:
# android/app/src/main/AndroidManifest.xml
#   → Set com.snapchat.kit.sdk.clientId
#   → Set com.snapchat.kit.sdk.redirectUrl
#   → Set intent-filter scheme/host/path
```

### iOS Setup

```bash
cd ios/

# 1. Install CocoaPods dependencies
pod install

# 2. Open the workspace (NOT the .xcodeproj)
open LoginKitSample.xcworkspace

# Key file to configure:
# ios/LoginKitSample/Info.plist
#   → Set SCSDKClientId
#   → Set SCSDKRedirectUrl
#   → Set URL Schemes
```

### React Native Setup

```bash
cd react-native/

# 1. Install JS dependencies
yarn install

# 2. iOS only: Install pods
cd ios && pod install && cd ..

# 3. Run the app
yarn android    # Android
yarn ios        # iOS Simulator
```

---

## ✅ Verify Everything Works

| Check | How |
|-------|-----|
| Android builds | Open in Android Studio → Build → Make Project |
| iOS builds | Open `.xcworkspace` in Xcode → Build (⌘B) |
| React Native runs | `yarn android` or `yarn ios` from `react-native/` |
| Snap login works | Tap "Login with Snapchat" → redirects to Snapchat → returns with user data |

---

*Next → [2-HIGH-LEVEL-DISCOVERY.md](2-HIGH-LEVEL-DISCOVERY.md)*
