# Runtime-generated poster progress follow-up — 1.8.56

The latest device report still showed the white poster line after 1.8.55. Inspection found a missed rendering path: `home_layout.build_layout()` calls `cinematic_cards.posters()`, which discards every child of the source item and focused layouts. `catalogue_layout.add_layouts()` independently builds the wide alternatives. Both builders still used the opaque white `cinematic/solid.png` progress background. The previous source XML fix and tests therefore did not cover the actual generated cards.

Both builders now use `poster_progress.append()`: a dark capsule image immediately followed by a progress fill with identical geometry and visibility, control-level theme colouring, explicit transparent background and overlay assets, empty end caps and no reveal mode. The new module participates in the generated Home layout digest, invalidating existing cached layouts on update.

Regression tests build and inspect the final Home XML that Kodi opens: three rows, poster and wide alternatives, focused and unfocused states, and the Discover grid in all five themes. They also verify compact-card alignment and invalidation when the progress renderer changes. Static info-page controls retain the 1.8.55 fix.

The latest supplied device report measured 0.56 seconds finding, 0.90 seconds preparing and 6.23 seconds opening/buffering: 7.69 seconds total. Playback handoff was 0.08 seconds and resolver wait was 0.68 seconds. This supports the improvement from the independent resolver requests in 1.8.55. This release changes no playback behavior or timing limits.

Validation: 1,131 automated tests passed. Release packages are checked for integrity, agreement with source files, Python/XML parsing and known credential signatures. App version 1.8.56; existing player skin 0.1.16 and repository installer 1.0.4 are retained unchanged. Actual poster appearance still needs confirmation on Kodi; these checks validate generated controls and assets rather than claiming a native render.
