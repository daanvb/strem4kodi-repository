# Strem4Kodi 1.8.100 / player skin 0.1.25

Shield profile copies now include per-media Auto Play preferences, retry limits,
portable fullscreen Back/seek/control timing, subtitle preferences, skip/chapters
options, pre-roll enablement and FEL-label visibility. Hardware, power/display,
custom remote keymaps, local paths and temporary source filters stay local.
Older saved profiles remain valid and leave newly included settings unchanged.
Update all clients before importing an expanded master.

The companion skin requires Aerial (screensaver.atv4 3.0.3) from Kodi's official
repository. Approved profile imports selecting the companion appearance also
select Aerial at a safe app-shell entry, keeping the current inactivity timeout.
Durable backup, readback, retry and Undo cover the previous screensaver. Disabled
or missing Aerial remains pending. Its own configuration opens through Skin
Settings / General; native power/CEC and Aerial defaults remain device-specific.
To apply these defaults on the Shield itself, import the profile there too.

The private setup website now uses original Strem4Kodi branding and responsive
phone/desktop layouts, clearer source/receiving approval states, a manual TV-code
entry and collapsed advanced tools. Private preference values never render.
Owner authentication, secure cookies, Origin and CSRF checks remain intact.
The service is already deployed and retains the existing private master profile.

Validation: all 1,661 automated tests passed on Windows; 31 focused setup/dashboard
checks passed. Browser checks covered six states at 1280x900 and 390x844, layout,
images, primary controls, advanced tools, invalid codes and synthetic approval.
Live HTTPS login/dashboard/assets and stored-profile preservation passed.
Release packages, repository listings and credentials were checked separately.
No physical Kodi device was attached; native Aerial activation/playback still
requires device verification. Update all clients, copy a fresh Shield master,
import on each device including the Shield, then restart Kodi.
