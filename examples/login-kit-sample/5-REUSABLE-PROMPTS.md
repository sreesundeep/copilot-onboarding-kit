# 📋 5. Reusable Prompts — Snapchat Login Kit Sample

> Copy-paste these project-specific prompts into GitHub Copilot Chat. They are pre-filled for the `login-kit-sample` codebase.

---

## 🏠 Project Overview Prompts

### Quick Overview
```
@workspace Give me a complete overview of the Snapchat Login Kit Sample project:
1. What does each platform sample (android, ios, react-native) do?
2. What Snap Kit SDK version does each platform use?
3. How do the three samples differ in features?
4. What OAuth2 scopes are requested?
Create a comparison table of all three platforms.
```

### New Developer Survival Guide
```
@workspace I'm a new developer joining this project. Give me a survival guide:
1. The 5 most important files I should read first (and why)
2. How does Snapchat OAuth2 login work at a high level?
3. What do I need from the Snap Kit Developer Portal before I can run anything?
4. Common gotchas when setting up OAuth client IDs and redirect URLs
5. How to test if login is working correctly
```

---

## 🔍 Platform-Specific Prompts

### Android Deep-Dive
```
@workspace Analyze the Android sample in the android/ directory:
1. Explain what MainActivity.java does step by step
2. How does SnapLogin.getButton() work vs. a custom login button?
3. What does the OnLoginStateChangedListener handle?
4. How is the GraphQL user data query constructed and executed?
5. How does Glide load the Bitmoji avatar?
6. What is the SnapKitActivity and why does it need singleTask launch mode?
```

### iOS Deep-Dive
```
@workspace Analyze the iOS sample in the ios/ directory:
1. Explain the flow from AppDelegate.swift to LoginViewController.swift
2. How does SCSDKLoginClient.application(_:open:options:) handle the OAuth redirect?
3. What does SCSDKUserDataQueryBuilder do and how is it used?
4. How does the Bitmoji avatar get loaded and displayed?
5. What Info.plist keys are critical and what happens if they're wrong?
6. Why does it use xcworkspace instead of xcodeproj?
```

### React Native Deep-Dive
```
@workspace Analyze the React Native sample in react-native/:
1. Explain App.tsx component state management
2. How do the NativeEventEmitter / DeviceEventEmitter listeners work for login events?
3. What's the difference between LoginKit.verify() and LoginKit.verifyAndLogin()?
4. How does the phone verification flow work with the Snap Kit Verify API?
5. What native Android/iOS configuration is needed beyond the JS code?
```

---

## 🔄 Flow Tracing Prompts

### OAuth Login Flow
```
@workspace Trace the complete OAuth2 login flow across all platforms:
1. What happens when the user taps the login button?
2. How does the app open Snapchat? (deep link vs. web fallback)
3. How does Snapchat redirect back to the app?
4. How does each platform handle the redirect URL callback?
5. How is the auth code exchanged for an access token?
Create a Mermaid sequence diagram showing the cross-app flow.
```

### User Data Fetch Flow
```
@workspace Trace how user profile data is fetched after login:
1. What GraphQL query is sent? ({me{bitmoji{avatar},displayName,externalId}})
2. How does each platform call fetchUserData?
3. What data structure is returned?
4. How is the Bitmoji avatar URL turned into a displayed image?
5. What happens if the user has no Bitmoji connected?
```

### Token Lifecycle
```
@workspace Explain the OAuth token lifecycle in this project:
1. How are access tokens stored by the SDK?
2. How is the access token refreshed?
3. What does clearToken() do on each platform?
4. How does isUserLoggedIn check work internally?
5. What happens when a token expires mid-session?
```

---

## 🔧 Configuration Prompts

### OAuth Setup
```
@workspace List all OAuth configuration points in this project:
1. Where is the OAuth client ID set on each platform?
2. Where is the redirect URL set on each platform?
3. Where are the OAuth scopes defined?
4. What URL scheme / intent filter setup is needed?
5. What happens if any of these are misconfigured?
Format as a cross-platform comparison table.
```

### Redirect URL Deep-Dive
```
@workspace Explain how redirect URLs work across platforms:
1. Android: How do intent-filter scheme/host/path map to the redirect URL?
2. iOS: How does CFBundleURLSchemes relate to SCSDKRedirectUrl?
3. React Native: How is the redirect URL configured for both platforms?
4. What are common mistakes that cause "redirect not working" errors?
```

---

## 🛡️ Security & Auth Prompts

### OAuth Security
```
@workspace Analyze the security aspects of Login Kit integration:
1. How does the SDK prevent CSRF attacks during OAuth?
2. How are tokens stored securely on each platform?
3. What scopes are requested and what data do they expose?
4. Is there a token refresh mechanism?
5. What happens on the backend when clearToken() is called?
```

---

## 🧪 Testing Prompts

### Test the Integration
```
@workspace How would I test the Snapchat Login Kit integration?
1. What test files exist in this project?
2. How do I test OAuth login without a real Snapchat account?
3. What are the Demo Users and how do they work?
4. How do I switch between Staging and Production client IDs?
5. What error scenarios should I test?
```

---

## 🐛 Debugging Prompts

### Common Issues
```
@workspace What are the most common issues when integrating Snapchat Login Kit?
1. "Login button doesn't appear" — what could cause this?
2. "Snapchat opens but doesn't redirect back" — debugging steps?
3. "User data returns null" — what to check?
4. "Login works on staging but not production" — why?
5. How do I check if my OAuth client ID and scopes are correct?
```

### Platform-Specific Debugging
```
@workspace For Android: What do I check if SnapKitActivity doesn't receive the redirect?
Focus on:
1. AndroidManifest.xml intent-filter correctness
2. scheme, host, path matching the redirect URL
3. singleTask launch mode requirement
4. Queries tag for Android 11+ package visibility
```

---

## 💡 Tips for These Prompts

| Tip | Example |
|-----|---------|
| **Reference specific files** | `Explain #file:android/app/src/main/java/com/snap/androidloginkitdemo/MainActivity.java` |
| **Compare platforms** | "How does the login flow differ between Android and iOS?" |
| **Ask about errors** | "What error does `onFailure(isNetworkError, statusCode)` return and why?" |
| **Ask about the SDK** | "What does `@snapchat/snap-kit-react-native` LoginKit.login() do internally?" |

---

*Next → [6-OUTPUT-TEMPLATES.md](6-OUTPUT-TEMPLATES.md)*
