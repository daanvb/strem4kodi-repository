# Private device setup

Use the Shield as the master configuration. Its settings are copied through the
app, rather than retrieving its userdata over your home network. This works for
remote clients once the setup service has an HTTPS route.

On the Shield, open Settings → Account & Stremio → Copy setup profile from this
device. Scan the QR code, log into your private setup dashboard and confirm the
code displayed on the Shield. The export includes allowlisted S4K preferences,
API keys, private sync credentials and provider role selections. The service
never receives Stremio sessions, cached streams, user files or custom Kodi keymaps.
Temporary source filters and hardware-sensitive settings are excluded.

App 1.8.100 also exports per-media Auto Play profiles, retry limits,
fullscreen Back/seek/control timing, subtitle preferences, skip/chapters options,
pre-roll enablement and FEL label visibility. After installing app 1.8.100 and skin 0.1.25 on the
Shield, run Copy setup profile from this device again to replace the saved master.
Update receiving devices before importing the expanded profile. Older saved
profiles remain valid and leave these newly included options unchanged.

On a new device, install the repository, install/open Strem4Kodi, and select
Use my private setup profile. Approve its code on your phone. If sign-in is needed,
the same phone page links to Stremio's official device sign-in. Stremio supplies
the installed private AIO add-ons and library. Existing authenticated devices can
also import the profile from Account & Stremio. Pairing is required each time;
the public repository contains no private keys.

The companion skin remains an addon dependency. The profile remembers whether
the master uses the Strem4Kodi player skin. Kodi appearance is applied at the
next safe app-shell entry, before Home/sign-in allocation. Kodi may require its
normal skin confirmation. Audio, display, remote keymaps and OS permissions
remain device-specific. This does not install Kodi itself or bypass Kodi's
repository/install confirmations.

Approved profile imports also configure Kodi to enable event logging, HTTP
control with username `kodi` and no password/authentication, remote control from
applications on this system, and unknown sources. The existing HTTP port is
retained (Kodi's default is 8080). Remote access from other systems is not enabled
by this profile. Kodi's own confirmation dialogs still apply. Unsupported or
declined settings remain pending and are reported instead of marked successful.

When the profile selects the Strem4Kodi skin, Kodi's Home categories are reduced
to Add-ons and Favourites, with category widgets enabled. Skin changes wait for
that skin to be active; these do not alter the S4K app's navigation menu. Undo
device setup includes these native Kodi and skin settings, preserving subsequent
user edits. The private local backup can contain the previous HTTP password and
must not be included in diagnostic exports.

The companion skin requires Kodi's official Aerial add-on (`screensaver.atv4`
3.0.3 or newer). Profile setup selecting the companion appearance also selects
Aerial as Kodi's screensaver, preserving the previous selection for Undo and
keeping Kodi's existing inactivity timeout. Skin Settings → General → Aerial
screensaver settings opens its own configuration. Aerial's standard settings are
retained, including its default 4K/HDR/HEVC choices; display power/CEC and local
download paths are not copied from another device. If Aerial is disabled or
unavailable, setup reports that setting as pending rather than claiming success.

Client changes are backed up before mutation and retries retain that backup.
Undo device setup restores values still matching the applied profile and keeps
subsequent user changes. Skin undo is queued for the next safe shell entry. Network
failure, rejection, expiration and Cancel do not fabricate successful sign-in.

The Docker setup service uses a separate private admin key, expiring device
requests, per-device secrets stored as hashes, authenticated owner approval,
CSRF protection, no-store responses and bounded request sizes/concurrency.
Successful enrollment can be retried until acknowledged; completed requests
discard their delivery payload. The master profile stays in the private Docker
volume. Enrollment secrets and master keys never appear in QR URLs or logs.

The service's intended origin is https://setup.battleship.live. Route Caddy to
192.168.1.200:8011. The private compose and admin .env are kept separately under
C:/Users/danie/Documents/Codex/s4k-setup; never commit them. The dashboard will
show setting names, not secret values. First copy the Shield profile; empty
profiles cannot silently configure a new device.

The private Docker service and its HTTPS route have been verified, and the user
confirmed that importing the profile applied the restricted Kodi Home menu.
The expanded profile and Aerial changes are included in app 1.8.100 / skin
0.1.25. Update the Shield and all receiving devices, capture a fresh Shield master,
then import it on each device including the Shield and restart Kodi. Existing
master data stays intact until the user explicitly approves a new capture.
Native Aerial activation still requires a physical-device check after release.

The setup dashboard uses Strem4Kodi branding and responsive phone/desktop layouts.
QR approval pages distinguish saving a master from configuring a receiving device
and show the TV code, request state and next action. The hub also accepts a manually
entered eight-character code. JSON profile import and setting-name inspection are
inside Advanced profile tools; values are never displayed. Branding assets use a
fixed same-host whitelist, with no external fonts or scripts. Origin checks, signed
secure cookies and CSRF-protected approval forms remain in place.
