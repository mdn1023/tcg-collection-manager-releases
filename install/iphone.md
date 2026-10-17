# Install on an iPhone

**Status: the store owner's own iPhone only.**

iPhone apps can't be downloaded from a website. Without a paid Apple
Developer account, the app is built on the owner's Mac and installed onto
an iPhone plugged into that Mac, signed with a free Apple ID. A button in
the source repo does the building and installing.

**The catch with a free Apple ID:**
- The app **stops opening after 7 days.** Run the install again to renew it.
- No automatic updates. Running the install again also updates it.
- Only phones that have been plugged into that Mac can get it.

Other people's phones would need TestFlight, which needs a paid Apple
Developer account.

## First time

On the iPhone:

1. Plug it into the Mac, unlock it, and tap **Trust**.
2. **Settings → Privacy & Security → Developer Mode** → on. The phone
   restarts; tap **Turn On** when it asks.
3. Install **Tailscale** from the App Store and sign in. The app reaches
   its server through it.

## Install (and every 7 days)

1. Plug the iPhone into the Mac and unlock it. After the first time, being
   on the same Wi-Fi as the Mac is usually enough.
2. In the source repo on GitHub: **Actions → install on iPhone →
   Run workflow**. It takes a few minutes.
3. **First install only:** on the iPhone, open **Settings → General →
   VPN & Device Management**, tap the developer app, and tap **Trust**.
4. Open **TCG Collection Manager** and sign in.

## If it fails

- **"No iPhone connected to the Mac":** plug it in, unlock it, and run
  the install again.
- **The app won't open after a week:** the 7 days are up. Run the
  install again.

## Remove

Press and hold the app icon → **Remove App**.
