# Privacy Policy

**App:** Nodi (attendance tracker)  
**Publisher:** Banyan Studio  
**Contact:** banyanstudio.dev@gmail.com  
**Last updated:** 2026-10-03

This Privacy Policy describes how the Nodi Android application ("the App", "we", "us") handles information when you use it. Please read it together with our [Terms & Conditions](terms.md).

The App does not collect, sell or share your personal data. Statutory rights under the EU GDPR, UK GDPR, California CCPA/CPRA, and India's Digital Personal Data Protection Act, 2023 are preserved to the extent they apply to you.

## Summary

- **Nodi has no internet access.** The App does not request Android's internet permission, so it cannot send anything from your device to us or to anyone else.
- **Your attendance records stay on your device.** We never receive them, and we hold no copy on any server.
- The App has **no account, no sign-up, no ads, no analytics and no crash reporting**.
- The only copies of your data that can leave the App are the ones **you** make: a backup file you choose to export, and Android's own device backup if you have it turned on (see [section 3](#copies)).

If any of the above ever changes, this policy will be updated **before** the change ships to the Play Store, and the "Last updated" date above will be revised.

## 1. Information the App does not collect

The App does **not** collect, request or transmit:

- Personal identifiers such as your name, email address or phone number
- Account credentials — there is no account
- Location — the App requests no location permission, and a check-in records a time, not a place
- Contacts, photos, files, camera or microphone input
- Usage statistics, analytics events, advertising identifiers or crash reports

The App contains no advertising, analytics, crash-reporting or tracking SDKs.

## 2. Information the App stores on your device

To work as an attendance tracker, the App keeps the following in its own private storage on your device. Other apps cannot read it.

- **Attendance records.** For each day you record: the date, the day's status (Present, Half day, Absent or Holiday), and your check-in and check-out times, if any. These are kept in a local database.
- **Your settings.** Week start day, workday length, 12- or 24-hour time, whether seconds are shown, reminder on/off and lead time, theme, how times are entered, and whether you have finished first-run setup.

Check-in and check-out times come from your device's own clock. Nothing is looked up online.

Some of this information is also **shown** outside the App, by Android, on your own device:

- The **home-screen widget**, if you add one, shows today's status and punch times on your home screen.
- The **checkout reminder** is an ordinary Android notification ("Time to check out"). Whether it appears on your lock screen is controlled by your device's notification settings.

## 3. Copies of your data you can choose to make

### Backup files you export

Settings → Backup → **Export backup** writes your attendance records to a JSON file at a location **you** pick in Android's file picker. The file contains your attendance records only — dates, statuses and punch times — and none of your settings. It is plain, unencrypted text, so anyone who has the file can read it. If you save it to a cloud storage provider through the picker (for example Google Drive), that provider's terms and privacy policy apply to the copy stored there. The App keeps no record of where you saved it.

**Import backup** reads a file you pick in the same way. The App checks the whole file before anything changes, asks you to confirm, then merges the file's days into your records: on a day present in both, the file's version wins; days only in the App are kept.

### Android's device backup

The App allows Android's built-in backup. If you have turned on backup for your device (for example, Google One / "Backup by Google" in your device settings), Android may include the App's attendance database and settings in that backup, and restore them when you set up a new device or reinstall the App. The same data moves when you transfer apps directly from one device to another. This backup is run by Android and your backup provider, under your account and their privacy policy — **we cannot access it**. You can turn it off in your device's backup settings.

## 4. Permissions used

| Permission | Why it's used |
|---|---|
| Notifications (`POST_NOTIFICATIONS`) | To show the checkout reminder. Requested during first-run setup or when you turn reminders on; you can refuse it and the rest of the App works normally. |
| Alarms & reminders (`SCHEDULE_EXACT_ALARM`) | To fire the checkout reminder at the right minute. If you don't allow it, Android may deliver the reminder a little late. |
| Run at startup (`RECEIVE_BOOT_COMPLETED`) | To set today's checkout reminder again after your phone restarts, since Android clears alarms on reboot. |
| Background work (`WAKE_LOCK`, `FOREGROUND_SERVICE`, `ACCESS_NETWORK_STATE`) | Added automatically by Android's WorkManager library, which the home-screen widget uses to redraw itself. `ACCESS_NETWORK_STATE` only lets the library check whether a connection exists; with no internet permission, the App still cannot send or receive anything. |

The App does **not** request internet, location, contacts, camera, microphone, phone, calendar or storage permissions. Backup files go through Android's file picker, which needs no storage permission.

## 5. Third parties

The App shares no data with any third party, because it sends no data at all. Google Play, through which you install the App, may collect information about your installation (such as aggregate install numbers and crash information) under Google's own Privacy Policy; that collection happens outside the App and outside our control. The same applies to Android's device backup and to any cloud storage provider you pick when saving a backup file (section 3).

## 6. Children's privacy

The App is a general-audience productivity tool and is not directed at children. It collects no personal data from anyone, including children.

## 7. Data retention and deletion

We hold no data about you, so there is nothing for us to retain. On your device, your records and settings stay until you remove them:

- Clear a single day from the day sheet in the App.
- Remove everything with **Settings → Apps → Nodi → Storage → Clear storage**, or by uninstalling the App.
- Backup files you exported are ordinary files: they remain wherever you saved them until you delete them.
- A copy in Android's device backup is kept and deleted according to your backup provider's policy.

Because your records exist only where you keep them, we cannot restore them if they are lost, and we are not responsible for any loss of your data or any damage to your device. See sections 5, 7 and 11 of the [Terms & Conditions](terms.md), and keep a backup.

## 8. Your rights

Because your data never reaches us, you exercise most rights directly on your device, without asking us:

- **Access and portability.** Everything the App holds is visible in the App, and **Export backup** gives you a complete copy in a documented, machine-readable JSON format.
- **Correction.** Edit any day's status or punch times from the day sheet.
- **Deletion.** See section 7.

If you have any privacy question or request, email banyanstudio.dev@gmail.com. We aim to respond within 30 days. Since we hold no data about you, we will not ask you for identifying information.

**Complaints.** You have the right to complain to a data-protection authority — your national supervisory authority in the EU or the UK, or the Data Protection Board of India — without contacting us first.

## 9. Changes to this policy

If this policy is updated, the new version will be published at this same URL before the change reaches users, with a new "Last updated" date. If an update ever changes what the App collects, it will be described in the summary above.

## 10. Contact

Questions about this policy can be sent to: banyanstudio.dev@gmail.com
