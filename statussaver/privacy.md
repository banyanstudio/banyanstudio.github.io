# Privacy Policy

**App:** Status Saver
**Publisher:** Banyan Studio
**Contact:** banyanstudio.dev@gmail.com
**Last updated:** 2026-07-29

This Privacy Policy describes how the Status Saver Android application ("the App", "we", "us") handles information when you use it. Please read it together with our [Terms & Conditions](terms.md).

The App does not sell or share your personal data, and does not use it to build a profile of you or to serve advertising. Statutory rights under the EU GDPR, UK GDPR, California CCPA/CPRA, and India's Digital Personal Data Protection Act, 2023 are preserved to the extent they apply to you.

## Summary

- The App **does not collect your personal information** — no name, email, phone number, or account. It never sells your data or shares it for advertising.
- The App collects **anonymous usage statistics and crash reports** to help us improve it. **You can turn this off at any time** in Settings → Privacy → "Share anonymous usage data".
- The App **has no ads, no accounts, and no sign-up**.
- **The photos and videos you view and save never leave your device** — the App does not upload your media anywhere.

If any of the above ever changes, this policy will be updated **before** the change ships to the Play Store, and the "Last updated" date above will be revised.

## 1. Information the App does not collect

The App does **not** collect or request any of the following:

- Personal identifiers such as your name, email, or phone number
- Account credentials or contact lists
- Location data (beyond the coarse country-level information described in section 4)
- The content of any photos or videos you view, save, or share

The App shows no ads and contains no advertising or ad-attribution SDKs. The App does not sell your data or share it for advertising.

## 2. Information the App accesses locally on your device

To do its job, the App reads media files that are already present on your device. This access is **scoped, local, and never leaves your phone**:

- **Status folder access (SAF tree URI).** When you first open the App, Android asks you to grant access to the folder where your chat app stores recently viewed statuses. The App stores **only the granted folder URI** in its own private app storage (Android DataStore) so you do not have to re-grant access every time. The URI itself is just a pointer — no media content is copied or uploaded by storing it.
- **Reading status media.** The App reads photo and video files inside the folder you granted access to, in order to display them inside the App. Files are read on-demand for display and are not duplicated, uploaded, or transmitted. Status media is **ephemeral**: the underlying chat app typically keeps status files on your device for only about 24 hours after you view them, and removes them automatically when the status expires. If you have not used the App to save a copy before that happens, the file is gone and the App cannot recover it.
- **Saving media to your gallery.** When you tap save, the App writes a copy of the selected file to your device's public media storage via Android's MediaStore API:
  - Photos → `Pictures/StatusSaver`
  - Videos → `Movies/StatusSaver`
  Saved files become part of your normal device gallery and are managed by Android, not by the App.
- **Sharing.** When you tap share, the App hands the selected file to Android's standard share sheet via a `FileProvider`. The destination app (gallery, messaging app, etc.) is chosen by you. The App does not see or record what you share or whom you share it with.

The App requires **no `MANAGE_EXTERNAL_STORAGE`** and **no broad storage permission**. It can only read files in the folder you explicitly granted access to.

## 3. Permissions used

| Permission / capability | Why it's used |
|---|---|
| Storage Access Framework (SAF) folder grant | To read status media from the folder you select |
| MediaStore write (scoped, no runtime permission on Android 10+) | To save a copy of the file you chose into your gallery |
| FileProvider (in-process) | To hand a file to another app when you tap share |

The App does **not** request location, contacts, camera, microphone, or background-execution permissions.

## 4. Network activity, anonymous usage data, and crash reports

The App does not upload the photos or videos you view or save — that media never leaves your device. The App contains no advertising network and does not sell your personal data or share it for advertising.

### Anonymous usage data and crash reports

To understand which features are used and to find and fix crashes, the App uses two services provided by Google LLC as our processors:

- **Google Analytics for Firebase** — anonymous usage statistics
- **Firebase Crashlytics** — crash reports

**What is collected:** app interaction events (for example: completing first-time setup, saving, sharing, or reposting a status — never the media itself or its file names), device model, operating system version, country, app version, crash stack traces, and a randomly generated app-instance identifier. This identifier is not tied to your name, email, phone number, or any account — the App has none of those — and we make no attempt to identify you from it.

**What is never collected:** the content of your photos and videos, file names, anything you type, your contacts, or your precise location.

**Opt-out:** you can turn collection off at any time in **Settings → Privacy → "Share anonymous usage data"**. The switch takes effect immediately, covers both services, and persists until you turn it back on.

**Retention:** analytics event data is retained on Google's servers for at most 14 months and is then deleted automatically. Crash reports follow Firebase's standard retention (90 days). Google's handling of this data is described in the [Google Privacy Policy](https://policies.google.com/privacy) and [Firebase Privacy and Security](https://firebase.google.com/support/privacy) documentation.

**Legal basis (where GDPR applies):** our legitimate interest in understanding aggregate feature usage and keeping the App free of crashes, balanced by the anonymous nature of the data and the always-available opt-out.

The Google Play Store itself may collect aggregate install or crash information independently of the App. That collection is governed by Google's own Privacy Policy and is outside our control.

## 5. Children's privacy

The App is rated for general audiences and is not directed specifically at children. The App does not knowingly collect personal data from children under 13 in the United States, or under the equivalent minimum age of digital consent in your country (which is up to 16 in parts of the European Union).

## 6. Data retention

We do not hold your personal data on any server of our own. Anonymous usage statistics and crash reports are retained by Google on our behalf for the periods described in section 4 (14 months for analytics events, 90 days for crash reports) and are then deleted automatically.

Locally, the App stores the following on your device only:

- The SAF folder URI you granted, in the App's private DataStore
- Your theme and analytics preferences, in the App's private DataStore
- Files you explicitly save, in your device's public Pictures / Movies folders

You can remove the SAF URI at any time by clearing the App's data in **Settings → Apps → Status Saver → Storage → Clear data**, or by uninstalling the App. Saved files in your gallery are yours and remain on your device until you delete them.

## 7. Your rights

The App does not sell or share your personal data, and you retain full control over the media on your own device. If you have a question or request about your data, contact us at banyanstudio.dev@gmail.com.

If you believe this policy has been violated or you have questions about it, contact us at banyanstudio.dev@gmail.com.

## 8. Independence from messaging services

Status Saver is an independent utility. It is **not affiliated with, endorsed by, sponsored by, or otherwise associated with** WhatsApp LLC, Meta Platforms, Inc., or any other messaging service, social network, or their owners. WhatsApp is a trademark of WhatsApp LLC; any reference to it is descriptive (nominative) use only, to identify the chat app whose already-downloaded status media the App can help you save. All trademarks belong to their respective owners.

## 9. Changes to this policy

If this policy is updated, the new version will be made available at the same URL where you obtained this one before the change reaches users. Continued use of the App after a change becomes effective constitutes acceptance of the updated policy.

## 10. Contact

Questions about this policy can be sent to: banyanstudio.dev@gmail.com
