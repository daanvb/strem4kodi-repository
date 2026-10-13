# Strem4Kodi 1.8.95

The latest private report from the client running Kodi 21.3 and addon 1.8.94
ended its previous session at `search.closed`, focus 601. Its final Kodi log
entries at 19:24:39 on 13 October were `search.select` and `search.closed`,
with no subsequent title allocation marker. The user saw the underlying left
menu, followed by Kodi exiting. No SIGSEGV, SIGABRT, out-of-memory marker or
selection-time Python traceback was captured. Earlier service/up-next shutdown
tracebacks are not treated as proof of the current crash's cause.

Inspection of Kodi 21.3's native source found that `Window::GetControlById`
creates a ControlEdit wrapper for an XML edit, but writes its alignment through
ControlButton. Those classes have different member layouts. This is an unsafe
native path used by our previous Search control; it is a credible cause,
not a confirmed stack diagnosis from the affected Fire TV.

Primary source references:
- https://github.com/xbmc/xbmc/blob/21.3-Omega/xbmc/interfaces/legacy/Window.cpp#L311
- https://github.com/xbmc/xbmc/blob/21.3-Omega/xbmc/interfaces/legacy/Control.h#L992
- https://github.com/xbmc/xbmc/blob/21.3-Omega/xbmc/interfaces/legacy/Control.h#L2341

Search now keeps its raw input in Python and uses a button for the query field.
Selecting that field opens Kodi's keyboard, which retains phone paste support.
The existing on-screen remote keyboard and debounced suggestions remain.
Polling must retain trailing spaces so it cannot concatenate words while typing.
No XML edit control is accessed or wrapped by Search.

After doModal returns, the poller is joined without holding the render lock.
The next view waits for the specific native search dialog to become invisible.
A worker or dialog timeout aborts the handoff instead of opening another view
over an incomplete teardown. Network workers return data only and do not block
this retirement. Fixed numeric checkpoints distinguish close returning, modal
return, worker stop, native retirement and timeout in future private reports.
Python process bitness is included to help separate Android builds.

No native Kodi execution is available in the automated tests. Device retesting
is still required; this release must not be described as a confirmed Fire TV
crash fix until that succeeds. Restart Kodi after installing 1.8.95; player skin remains 0.1.23.

Release validation: all 1,587 automated tests passed on the integrated Windows
checkout with Python 3.12 and Pillow 12.3.0. Source credential scanning,
package/source agreement, Python/XML parsing, ZIP integrity and staged-feed
checks passed. Physical-device confirmation is still required.
