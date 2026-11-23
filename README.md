# Maputnik #1294 sprite picker visuals

UI screenshots produced with the authored MIT-licensed sprite fixtures in the feature commit. No external map, tile, sprite service or personal data is used.

- before.png: unmodified upstream 2296b77c37f650a20f81f94d586b8634e4a7a4cb; four text options without previews.
- after.png: feature 945ac551cd8df205e1d71d35622907ae0565a11e; ordinary/SDF/retina previews in a searchable menu.
- after-sdf.png: SDF preview alongside the actual MapLibre render of the selected fixture. The catalog uses a neutral black silhouette, not a simulation of data/zoom-dependent paint or halos.

Environment: Node 26.13.1, npm 11.20.0, Playwright 1.65.1 / Chromium 159.0.8154.6, software WebGL using the project's test settings.

To inspect the UI, use the sprite-style.json and sprite-atlas fixtures from the feature's e2e/fixtures directory, with its existing MaputnikDriver response mocks. Open the symbols layer, scroll icon-image into view and clear the field to show all four options. Select sdf-circle for the final view. For the historical visual control, use the same sprite URL without the query parameter so that the older metadata loader also lists the four options.

Full feature verification: 199 official E2E tests and 55 unit tests pass, ESLint/SCSS lint/type-checked production build pass. The thumbnail assertion fails on the unmodified base. Deliberately wrong expected pixels and a disabled stale-response guard also fail, and those mutations were restored before the successful full run.

This isolated artifact branch is not part of the feature PR's source diff.

## Usage video

[Watch the 36-second MP4](usage-demo.mp4) (1280×900, H.264, no audio). Recorded at feature commit945ac551cd8df205e1d71d35622907ae0565a11e using the actual UI and authored assets served as real local files, without route mocks.

The video shows searching/selecting an icon, changing the Sprite URL in Style Settings from the first atlas to a second atlas, and changing it back. Both the autocomplete list and thumbnails update; the selected symbol is rendered on the map. The recording scenario also checks the stored URL/ID and actual preview pixels. This demonstrates URL/source changes; it does not claim automatic detection of files changing behind an unchanged URL.
