# Strem4Kodi 1.8.61: manual sync follow-up

Manual sync previously constructed a notification inside the settings input
callback, with initially empty XML labels and a separate closing thread. A late
onInit could leave the box blank; construction failure could escape the settings
handler. Notifications now have pre-populated first-frame text and unique layouts.
One bounded worker constructs, displays and closes them. Duplicate messages
coalesce, window errors are contained and temporary layouts are removed.

The sync action no longer rebuilds settings rows after requesting background work.
The status watcher checks that its rows still belong to the open account page
before updating them. Repeated onInit does not create duplicate status watchers.
Progress-worker thread-start failures leave the service alive and schedule a retry.

Regression coverage exercises worker ownership, text before initialisation,
duplicate requests, failed construction, unchanged sync focus, closed/replaced
settings rows and thread-start failure. All 1,194 local tests passed. The full suite and exact-commit GitHub
checks gate publication. Package checks cover source agreement, XML/Python,
ZIP integrity, credential signatures and feed checksums.

This fixes observed code-level failure paths, not a reproduced native Kodi crash.
No Shield or crash log is attached to this environment. Player skin remains
0.1.17. The release retains all 1.8.60 changes; restart Kodi after updating.
