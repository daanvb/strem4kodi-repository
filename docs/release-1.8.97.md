# Strem4Kodi 1.8.97

Private device setup copies an allowlisted master configuration from the Shield
without placing API keys in the public installer. Each export/import requires
an expiring pairing code and authenticated owner approval. New clients link
their Stremio account on its official device page, then import account add-ons.

Profile application journals the original values before mutation. Retry resumes
the same profile; Cancel stops further changes; Undo restores applied values
while preserving later user changes. Provider selections are included. Display,
audio hardware and custom Kodi keymaps are excluded. Skin changes wait until a
safe app-shell entry. Existing authenticated clients are not prompted on startup.

The private backend uses bounded requests/concurrency, authenticated device
polling, owner CSRF protection and no-store responses. Its runtime configuration
and stored profiles remain outside the addon repository; server deployment code
is excluded from the addon ZIP.

Validation: all 1,612 automated tests passed on Windows with Python 3.12 and
Pillow 12.3.0. Tests cover profile validation, backup/retry/undo/cancellation,
synthetic HTTP approval/authentication routes, expiry and controller startup.
Package integrity and credential checks passed. Docker health and the private
HTTPS health/login routes were verified. A real Shield export and second-device
enrollment have not yet been tested. Player skin remains 0.1.23.
