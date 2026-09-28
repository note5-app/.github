# NOTE5

A notebook that encrypts your notes in the browser and syncs them, if you want,
to a private GitHub repository.

### → [Open the app](https://note5-app.github.io/note5-frontend/)

---

## What it is

NOTE5 is a single-page web app for taking notes. It stores everything locally
in your browser by default, and offers optional cloud sync so you can access
your notes from multiple devices and keep an encrypted backup in the cloud.

Encryption happens entirely on your device. Your master password is never sent
anywhere.

The app is in **alpha**. See the *Status* section below for what that means.

---

## How it works

1. You choose a username and a master password.
2. Your browser derives an encryption key from them.
3. Notes are encrypted on your device.
4. If you enable cloud sync, the encrypted blob is pushed to a **private
   GitHub repository**.
5. On another device, entering the same username and password re-derives the
   same key, pulls the blob from the repository, and decrypts it locally.

The GitHub repository only ever stores ciphertext. Your notes are unreadable
to anyone who does not know your master password.

---

## Features

- Three note types: **chat threads**, **plain text files**, **credentials**
- Full-text search with scoped prefixes
- Pin, custom icons, dark and light themes
- Local autosave with unsaved-changes warnings
- Optional automatic cloud sync (12h / daily / weekly / monthly)
- Versioned backups — a failed upload never overwrites the previous one
- Manual export / import of encrypted backup files (`.note5`)
- Progressive Web App: installs on Android, iOS and desktop, works offline

---

## Privacy

- Your **master password never leaves your browser**.
- Your **notes are encrypted** before they are uploaded anywhere.
- **No accounts, no email, no OAuth, no tracking, no analytics, no ads.**
- If you never enable cloud sync, nothing ever leaves your device.

---

## Open source, with one exception

The entire frontend is open source and inspectable. You can read every line of
code that runs in your browser, audit the cryptography, and verify there is no
hidden data collection:

**→ [github.com/note5-app/note5-frontend](https://github.com/note5-app/note5-frontend)**

You can also run your own copy of the frontend — the README explains how.

The one component that is not published is the small **Cloudflare Worker**
that relays encrypted blobs to GitHub. It is intentionally kept closed because
it holds the credential that writes to the backup repository. Everything that
handles your password or your notes is in the open frontend and never touches
the Worker.

---

## Master password

Choose a master password of **at least 12 characters**. This recommendation follows NIST SP 800-63B and OWASP guidance
for user-chosen passwords, and is designed to resist offline attacks against
your encrypted backup.

**Your password is the only thing protecting your notes.** There is no
password reset, by design.

---

## Getting started

1. Open the app: **https://note5-app.github.io/note5-frontend/**
2. Choose a username and a strong master password.
3. Start taking notes. Everything is saved locally on your device.
4. Optional: open **Settings → Cloud backup** to sync across devices and keep
   a copy in the cloud. This requires no GitHub account and no setup from you.
5. Optional: install as an app from your browser menu.

---

## Cost

Free. The app runs entirely on free infrastructure:

- **GitHub Pages** for the app itself
- **GitHub** for encrypted backup storage
- **Cloudflare Workers** for the relay that writes to GitHub

No subscriptions, no ads, no data sales.

---

## Status

NOTE5 is in **alpha**. That means:

- Features may change without notice.
- Bugs can exist. Some may affect your data.
- Backups (local exports) are your responsibility.
- Feedback is welcome via GitHub issues.

If you use it, keep an encrypted export (`.note5`) somewhere you control.

---

## License

All rights reserved. Personal project.
