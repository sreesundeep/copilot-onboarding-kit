# 🔄 4. End-to-End Flow Tracing — Snapchat Login Kit Sample

> Connect the dots. Trace real user scenarios through the entire system.

---

## Critical User Flows

This project has **4 key user flows**:

| # | Flow | Platforms |
|---|------|-----------|
| 1 | Login with Snapchat (OAuth2) | Android, iOS, React Native |
| 2 | Fetch User Profile Data | Android, iOS, React Native |
| 3 | Logout / Clear Token | Android, iOS, React Native |
| 4 | Phone Verification (Snapchat Verify) | React Native only |

---

## Flow 1: Login with Snapchat (OAuth2)

### What the User Does
User taps "Login with Snapchat" → app redirects to Snapchat → user approves access → Snapchat redirects back to the app with an authorization code → SDK exchanges it for an access token.

### Complete End-to-End Sequence

```mermaid
sequenceDiagram
    participant User
    participant SampleApp as Sample App
    participant SnapSDK as Snap Kit SDK
    participant SnapchatApp as Snapchat App
    participant SnapOAuth as Snapchat OAuth Server
    participant SnapAPI as Snapchat User API

    Note over User,SnapAPI: Phase 1: Initiate Login
    User->>SampleApp: Tap "Login with Snapchat" button
    SampleApp->>SnapSDK: login() / SnapLogin.getButton() click

    Note over User,SnapAPI: Phase 2: OAuth2 Authorization
    SnapSDK->>SnapchatApp: Open Snapchat via deep link
    Note over SnapSDK,SnapchatApp: If Snapchat not installed,<br/>falls back to web OAuth
    SnapchatApp->>User: "Allow [App] to access<br/>your display name, Bitmoji?"
    User->>SnapchatApp: Tap "Allow"
    SnapchatApp->>SnapOAuth: Submit authorization
    SnapOAuth-->>SnapchatApp: Authorization code

    Note over User,SnapAPI: Phase 3: Redirect Back
    SnapchatApp->>SampleApp: Redirect to app<br/>(via URL scheme / intent filter)

    Note over User,SnapAPI: Platform-Specific Handling
    alt Android
        SampleApp->>SnapSDK: SnapKitActivity receives intent
    else iOS
        SampleApp->>SnapSDK: AppDelegate.openURL → SCSDKLoginClient
    else React Native
        SampleApp->>SnapSDK: Native module handles redirect
    end

    Note over User,SnapAPI: Phase 4: Token Exchange
    SnapSDK->>SnapOAuth: Exchange auth code for access token
    SnapOAuth-->>SnapSDK: Access token + refresh token
    SnapSDK->>SnapSDK: Store tokens securely

    Note over User,SnapAPI: Phase 5: Notify App
    SnapSDK-->>SampleApp: Login succeeded callback
    SampleApp->>SampleApp: Update UI to logged-in state
```

### Entry Points by Platform

| Platform | Entry Point | Callback Handler |
|----------|------------|-----------------|
| Android | `SnapLogin.getButton()` click | `OnLoginStateChangedListener.onLoginSucceeded()` |
| iOS | `SCSDKLoginClient.login(from:completion:)` | Completion closure `(success, error)` |
| React Native | `LoginKit.login()` | `LOGIN_KIT_LOGIN_SUCCEEDED` event listener |

### OAuth Redirect Flow

```mermaid
flowchart TD
    TAP["User taps Login"] --> CHECK{"Snapchat<br/>installed?"}
    CHECK -->|Yes| DEEP["Deep link to Snapchat app"]
    CHECK -->|No| WEB["Open web-based OAuth"]
    DEEP --> CONSENT["User sees consent screen"]
    WEB --> CONSENT
    CONSENT --> APPROVE{"User approves?"}
    APPROVE -->|Yes| REDIRECT["Redirect back via URL scheme"]
    APPROVE -->|No| CANCEL["Return to app — login failed"]
    REDIRECT --> HANDLE{"Platform?"}
    HANDLE -->|Android| INTENT["SnapKitActivity<br/>intent-filter matches"]
    HANDLE -->|iOS| OPENURL["AppDelegate<br/>application:openURL:"]
    HANDLE -->|React Native| NATIVE["Native module<br/>handles deeplink"]
    INTENT --> TOKEN["SDK exchanges code for token"]
    OPENURL --> TOKEN
    NATIVE --> TOKEN
    TOKEN --> SUCCESS["Login succeeded ✅"]

    style TAP fill:#4CAF50,color:#fff
    style SUCCESS fill:#4CAF50,color:#fff
    style CANCEL fill:#f44336,color:#fff
```

---

## Flow 2: Fetch User Profile Data

### Trigger
Automatically called after a successful login.

### GraphQL Query
```graphql
{
  me {
    bitmoji { avatar }
    displayName
    externalId
  }
}
```

### Sequence

```mermaid
sequenceDiagram
    participant App as Sample App
    participant SDK as Snap Kit SDK
    participant API as Snapchat API

    App->>SDK: fetchUserData(query)
    Note over App,SDK: Query: {me{bitmoji{avatar},displayName,externalId}}
    SDK->>SDK: Attach access token to request
    SDK->>API: POST GraphQL query
    API->>API: Validate token + check scopes
    API-->>SDK: Response JSON
    SDK-->>App: UserData / UserDataResponse

    alt Success
        App->>App: Extract displayName
        App->>App: Extract bitmoji avatar URL
        App->>App: Load avatar image (Glide / URLSession / Image)
        App->>App: Display name + avatar in UI
    else Failure
        App->>App: Show error message / log error
    end
```

### Data Retrieved

| Field | Type | Where Displayed |
|-------|------|-----------------|
| `displayName` | String | Name label on profile view |
| `externalId` | String | External ID label (Android only shows this) |
| `bitmoji.avatar` | URL (String) | Avatar image view (loaded async) |

---

## Flow 3: Logout / Clear Token

### Sequence

```mermaid
sequenceDiagram
    participant User
    participant App as Sample App
    participant SDK as Snap Kit SDK

    User->>App: Tap "Log Out" / "Sign Out"

    alt Android
        App->>SDK: SnapLogin.getAuthTokenManager(ctx).clearToken()
        SDK->>SDK: Remove stored OAuth tokens
        SDK-->>App: onLogout() callback
        App->>App: resetUserInfo() — clear UI fields
    else iOS
        App->>SDK: SCSDKLoginClient.clearToken()
        App->>App: displayForLogoutState() — show login button
    else React Native
        App->>SDK: LoginKit.clearToken()
        App->>App: setUserData({}) + setRefreshAccessToken('')
    end
```

---

## Flow 4: Phone Verification (React Native Only)

### Trigger
User taps "Verify" or "Verify & Login" button.

### Complete Flow

```mermaid
sequenceDiagram
    participant User
    participant App as App.tsx
    participant SDK as LoginKit SDK
    participant VerifyAPI as api.snapkit.com

    User->>App: Tap "Verify" or "Verify & Login"
    App->>App: Show modal dialog
    User->>App: Enter country code + phone number
    User->>App: Tap "OK"

    alt Verify Only
        App->>SDK: LoginKit.verify(phone, countryCode)
    else Verify & Login
        App->>SDK: LoginKit.verifyAndLogin(phone, countryCode)
    end

    SDK-->>App: VerifyResponse {phoneId, verifyId}

    App->>VerifyAPI: POST /v1/phoneverify/verify_result
    Note over App,VerifyAPI: Query params: phone_number_id,<br/>phone_number_verify_id,<br/>phone_number, region

    VerifyAPI-->>App: {verified: true/false}

    alt Verified
        App->>App: Show "Phone Verified? true" (green)
    else Not Verified
        App->>App: Show "Phone Verified? false" (red)
    end

    User->>App: Tap "OK" to dismiss modal
```

---

## Error Handling Across Platforms

| Scenario | Android | iOS | React Native |
|----------|---------|-----|-------------|
| Login fails | `onLoginFailed()` → sets text "not logged in" | Completion closure `error` → displays in `messageLabel` | `LOGIN_KIT_LOGIN_FAILED` event → updates `lastLoginState` |
| User data fetch fails | `onFailure(isNetworkError, statusCode)` → logs error | `failure(error, isUserLoggedOut)` → prints error | `.catch(error)` → sets `userData` to error |
| Verify fails | N/A | N/A | `.catch(error)` → sets `verifyError` + shows in modal |
| No Bitmoji | Checks `meData.getBitmojiData() != null` | Returns empty string → no image loaded | Checks `userData?.bitmojiAvatar` → shows "No Bitmoji avatar" |

---

## Configuration & Environment

### OAuth Configuration (Required Before Running)

```mermaid
flowchart LR
    PORTAL["Snap Kit<br/>Dev Portal"] -->|"1. Register App"| CLIENT["Get OAuth<br/>Client ID"]
    CLIENT -->|"2. Configure"| CONFIG["Update Config Files"]
    CONFIG --> ANDROID_CFG["AndroidManifest.xml<br/>• clientId<br/>• redirectUrl<br/>• scopes"]
    CONFIG --> IOS_CFG["Info.plist<br/>• SCSDKClientId<br/>• SCSDKRedirectUrl<br/>• SCSDKScopes"]
    CONFIG --> RN_CFG["Both Android +<br/>iOS configs"]
    PORTAL -->|"3. Add Demo Users"| DEMO["Add Snapchat<br/>usernames for testing"]
    PORTAL -->|"4. Enable Login Kit"| ENABLE["Enable Login Kit<br/>on version"]
    PORTAL -->|"5. Activate"| ACTIVATE["Set Active<br/>on Staging"]

    style PORTAL fill:#FFFC00,color:#000
```

---

*Next → [5-REUSABLE-PROMPTS.md](5-REUSABLE-PROMPTS.md)*
