# Home playback retention

Movies and series with unfinished playback, and recently completed series already
represented in Continue Watching, use the same last-playback clock:

- Under 30 days: Continue Watching.
- From 30 days until 60 days: Don't Forget About Me.
- At 60 days: neither row. Keep saved progress, watch history and saved lists.

New playback updates the shared `lastWatched` timestamp, returns the title to
Continue Watching and restarts both windows. Refreshing metadata or opening Home
does not renew the clock. The same synced playback state produces the same result
on each client. Completed movies remain excluded, as before.

Both live Home and the fast progress snapshot rebuild reminder membership from
the current SQLite index. Explicit IMDb/TMDB/TVDB aliases prevent duplicates and
the active card wins over reminder copies. Legacy unfinished progress without a
usable timestamp gets a durable local first-observed baseline; genuine playback
then supplies the shared timestamp. Unstarted saved titles do not enter Continue
Watching.

Existing season-finale reminders remain available for unplayed saved series.
Once a title has playback history, its inactivity window takes priority: seasonal
cards cannot duplicate active titles, reset expiry or resurrect expired titles.
Upcoming episode schedules continue to use their confirmed release dates.

Reminder cards preserve the resume/next-episode target and expose the same media
context actions as Continue Watching, including Remove from Don't Forget About
Me. Explicit removals remain suppressed until newer playback, using the existing
shared removal watermarks.

Released in app 1.8.101. The companion skin remains 0.1.25.
