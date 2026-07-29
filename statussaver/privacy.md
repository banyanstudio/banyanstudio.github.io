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
- Location data — the App requests no location permission and cannot read your position. Google derives an approximate *country* from your device's IP address, as described in section 4
- The content of any photos or videos you view, save, or share

The App shows no ads and contains no advertising or ad-attribution SDKs. The App does not sell your data or share it for advertising.

## 2. Information the App accesses locally on your device

To do its job, the App reads media files that are already present on your device. This access is **scoped, local, and never leaves your phone**:

- **Status folder access (SAF tree URI).** When you first open the App, Android asks you to grant access to the folder where your chat app stores recently viewed statuses. The App stores **only the granted folder URI** in its own private app storage (Android DataStore) so you do not have to re-grant access every time. The URI itself is just a pointer — no media content is copied or uploaded by storing it.
- **Reading status media.** The App reads photo and video files inside the folder you granted access to, in order to display them inside the App. Files are read on-demand for display and are not duplicated, uploaded, or transmitted. Status media is **ephemeral**: the underlying chat app typically keeps status files on your device for only about 24 hours after you view them, and removes them automatically when the status expires. If you have not used the App to save a copy before that happens, the file is gone and the App cannot recover it.
- **Saving media to your gallery.** When you tap save, the App writes a copy of the selected file to your device's public media storage via Android's MediaStore API:
  - Photos → `Pictures/Status Saver Images`
  - Videos → `Movies/Status Saver Videos`
  Saved files become part of your normal device gallery and are managed by Android, not by the App.
- **Sharing.** When you tap share, the App hands the selected file to Android's standard share sheet via a `FileProvider`. The destination app (gallery, messaging app, etc.) is chosen by you. The App does not see or record what you share or whom you share it with.
- **Reposting.** When you tap repost, the App hands the selected file to WhatsApp specifically — again through a `FileProvider` — which opens WhatsApp's own status composer with the file attached. You post it, or cancel, from inside WhatsApp. The App does not post anything on your behalf, cannot see whether you went on to post, and receives nothing back. This requires WhatsApp to be installed; if it is not, the App tells you so and does nothing else.

The App requires **no `MANAGE_EXTERNAL_STORAGE`** and **no broad storage permission**. It can only read files in the folder you explicitly granted access to.

## 3. Permissions used

| Permission / capability | Why it's used |
|---|---|
| Storage Access Framework (SAF) folder grant | To read status media from the folder you select |
| MediaStore write (scoped, no runtime permission on Android 10+) | To save a copy of the file you chose into your gallery |
| FileProvider (in-process) | To hand a file to another app when you tap share or repost |

The App does **not** request location, contacts, camera, microphone, or background-execution permissions.

## 4. Network activity, usage data, and third-party services

The App does not upload the photos or videos you view or save — that media never leaves your device. The App contains no advertising network and does not sell your personal data or share it for advertising.

### Anonymous usage data and crash reports

To understand which features are used and to find and fix crashes, the App uses two services provided by Google LLC as our processors:

- **Google Analytics for Firebase** — anonymous usage statistics
- **Firebase Crashlytics** — crash reports

**What the App itself records.** Five app interaction events, and nothing else: completing first-time setup (and whether it succeeded), saving a status (including whether it was a photo or a video, and whether the save succeeded), sharing a status, reposting a status, and switching this setting off.

**What the Firebase SDK records on its own.** Beyond those five, Google's SDK automatically records a standard set of events that we do not choose individually and cannot disable one by one — for example first opening the App, the start and length of a session, app updates, operating-system updates, and uninstalls. It also records standard device and app attributes: device model, operating system version, approximate country, app version, and device language. Crashlytics adds crash stack traces and the device state at the moment of a crash.

**Identifiers.** A randomly generated app-instance identifier distinguishes one installation from another. It is not tied to your name, email, phone number, or any account — the App has none of those — and we make no attempt to identify you from it. Clearing the App's data or uninstalling it resets the identifier.

**IP address.** As with any network request, Google's servers receive your device's IP address, and Google uses it to derive the approximate country above. The IP address is not included in the reports available to us — we only ever see the country — and the App neither stores nor transmits it anywhere else. It is called out here because under the GDPR an IP address can itself be personal data.

**What is never collected.** The content of your photos and videos, their file names, anything you type, your contacts, or your precise location. Events record only that an action happened and its outcome, chosen from a fixed set of values — never the media involved.

**On the word "anonymous".** We call this data anonymous because it is never linked to your identity and we have no means of working out who you are from it. In strict data-protection terms it is more accurately *pseudonymous*: the app-instance identifier tells one installation apart from another, and under the GDPR that can count as personal data even though it names nobody. We therefore treat it as personal data and give you the legal basis and the rights set out below, rather than claiming the rules do not apply.

**Opt-out.** You can turn collection off at any time in **Settings → Privacy → "Share anonymous usage data"**. The switch takes effect immediately, covers both services and the automatic events described above, and persists until you turn it back on. Turning it off records one final event, so that we can see how many people opt out; nothing is collected after that.

**Where the data is processed.** Google processes this data on its own infrastructure, which includes servers in the United States and other countries outside your own. If you are in the EU, the UK, or India, that means the data may be transferred out of your jurisdiction. Those transfers rely on the safeguards in Google's data-processing terms — standard contractual clauses and, for the United States, the EU–US Data Privacy Framework. We operate no servers of our own and hold none of this data ourselves.

**Retention.** Analytics event data is retained on Google's servers for at most 14 months and is then deleted automatically. Crash reports follow Firebase's standard retention (90 days). Google's handling of this data is described in the [Google Privacy Policy](https://policies.google.com/privacy) and [Firebase Privacy and Security](https://firebase.google.com/support/privacy) documentation.

**Legal basis (where GDPR applies).** Our legitimate interest in understanding aggregate feature usage and keeping the App free of crashes, balanced by the limited and pseudonymous nature of the data and the always-available opt-out. Because we rely on legitimate interest, you have the right to object to this processing at any time: the Settings switch above *is* how you exercise that right, it works immediately, and you do not need to contact us or give a reason.

### In-app review prompt

The App may ask whether you would like to rate it, using **Google Play's in-app review** service (provided by Google LLC). The prompt is drawn by Google Play, not by the App. Any rating or review you submit goes to Google Play under Google's own terms — the App never sees it, and receives no personal data back. Reviewing or dismissing makes no difference to how the App works.

To decide whether to show the prompt at all, the App keeps three values in its own private storage on your device: when you first launched it, when it last showed the prompt, and a count of successful saves, shares, and reposts. The prompt appears only after at least five such actions *and* at least 180 days have passed since your first launch (or since the prompt was last shown). These three values never leave your device and are not sent to Google or to us.

The Google Play Store itself may collect aggregate install or crash information independently of the App. That collection is governed by Google's own Privacy Policy and is outside our control.

## 5. Children's privacy

The App is rated for general audiences and is not directed specifically at children. The App does not knowingly collect personal data from children under 13 in the United States, or under the equivalent minimum age of digital consent in your country (which is up to 16 in parts of the European Union).

## 6. Data retention

We do not hold your personal data on any server of our own. Anonymous usage statistics and crash reports are retained by Google on our behalf for the periods described in section 4 (14 months for analytics events, 90 days for crash reports) and are then deleted automatically.

Locally, the App stores the following on your device only:

- The SAF folder URI you granted, in the App's private DataStore
- Your theme and analytics preferences, in the App's private DataStore
- The three review-prompt values described in section 4 — first-launch time, last-prompt time, and a count of successful saves, shares, and reposts — in the App's private DataStore
- Files you explicitly save, in your device's public Pictures / Movies folders

Nothing in that list is transmitted anywhere. It is the complete set of data the App writes outside of the analytics and crash reporting described in section 4.

You can remove the SAF URI at any time by clearing the App's data in **Settings → Apps → Status Saver → Storage → Clear data**, or by uninstalling the App. Saved files in your gallery are yours and remain on your device until you delete them.

## 7. Your rights

The App does not sell or share your personal data, and you retain full control over the media on your own device. Depending on where you live, data-protection law gives you the rights below. We honour them regardless of whether they are legally enforceable in your country.

- **Object / opt out.** Stop the analytics and crash reporting at any time with **Settings → Privacy → "Share anonymous usage data"**. This is the fastest and most complete route, it is immediate, and it needs no request to us.
- **Access.** Ask what categories of data have been collected about your installation. Section 4 is the full answer; we hold no additional data to disclose.
- **Correction.** Ask us to correct inaccurate data. In practice there is nothing to correct — the data is event counts and device attributes, not statements about you.
- **Deletion.** Ask us to delete data associated with your installation. Because the app-instance identifier is the only handle that exists and it is not linked to you, please include it or contact us from the device; alternatively, clearing the App's data or uninstalling resets the identifier and the existing data expires on the schedule in section 4.
- **Portability.** Ask for a copy of the data in a portable format.
- **Withdraw consent / non-discrimination.** The App is not gated on data collection. Opting out changes nothing about how it works, and we will never degrade the App or charge you for exercising any of these rights.

To exercise any of these, email banyanstudio.dev@gmail.com. We aim to respond within 30 days. We will not ask you to create an account or supply identifying information you have not already given us.

**Complaints.** If you think we have handled your data unlawfully, you may complain to us at the address above, and you also have the right to complain to a data-protection authority directly — your national supervisory authority in the EU or the UK, or the Data Protection Board of India — without going through us first.

**Controller.** For the purposes of the GDPR and equivalent laws, the data controller is Banyan Studio, contactable at banyanstudio.dev@gmail.com. Google LLC acts as our processor for the services named in section 4.

## 8. Independence from messaging services

Status Saver is an independent utility. It is **not affiliated with, endorsed by, sponsored by, or otherwise associated with** WhatsApp LLC, Meta Platforms, Inc., or any other messaging service, social network, or their owners. WhatsApp is a trademark of WhatsApp LLC; any reference to it is descriptive (nominative) use only, to identify the chat app whose already-downloaded status media the App can help you save. All trademarks belong to their respective owners.

## 9. Changes to this policy

If this policy is updated, the new version will be made available at the same URL where you obtained this one before the change reaches users. Continued use of the App after a change becomes effective constitutes acceptance of the updated policy.

## 10. Contact

Questions about this policy can be sent to: banyanstudio.dev@gmail.com
