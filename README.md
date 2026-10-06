# Pocket of Us

A mobile-first, installable little love-note website. It is built as a static site with no external libraries or tracking.

## Personalize before sharing

1. Open `index.html` in a text editor.
2. Find `CREATOR_WHATSAPP_NUMBER` in the inline script and replace the empty string with your international number, digits only. For example, an Indian number starts with `91` followed by the phone number, with no `+`, spaces, or dashes.
3. Optionally edit the starter love notes and comforting quotes near the top of the script to make them more personal.
4. Host the folder over HTTPS, then share the link. Static hosting is enough; no database or server is required for the current version.

The WhatsApp button opens a pre-filled WhatsApp message. She must still tap **Send** in WhatsApp. If you leave the number blank, she can set it in **Make it yours** on her device.

## Run locally

From this folder, run:

```bash
python3 -m http.server 4173 --bind 0.0.0.0
```

Then open `http://localhost:4173`. For installation/offline caching on a phone, serve the site over HTTPS and use the browser's **Add to Home Screen** option.

## Passphrase and love note

The page now asks for the secret phrase on every load and whenever **Lock your space** is used. Each successful unlock opens a fresh love note (it avoids repeating the immediately previous one). The phrase is represented by a salted PBKDF2 verifier rather than plain text in the HTML.

**This is only a casual front-end gate, not real site authentication.** The repository and static site are public, and a visitor can inspect or alter client-side code to bypass the screen. Do not rely on it to protect highly private information. Real access control requires a protected host or server-side authentication; never put a secret in a public page and expect it to stay secret.

## Privacy and storage

Themes, layout, uploaded backdrop, memories, and journal entries are saved in that browser's local storage. They persist across visits on the same browser, but are not uploaded, encrypted, or synced to other devices. Anyone with access to the browser's site data may be able to read them, and clearing the browser's site data can erase them. Photos are resized in the browser before being stored locally.

The WhatsApp number is present in the website source if you set it there, so treat the folder/source as shareable with that in mind.
