# JOMS Media Studio

A new public, browser-local media studio built with HTML, CSS and vanilla JavaScript. No account, backend, API key, CDN, npm install or runtime cloud service is required. Photographs, fonts, scripts and styles are included locally.

## Open it

1. Download and extract the project ZIP.
2. Open **JOMS-Standalone.html** in a regular browser for the self-contained local edition. It embeds the application and its assets.
3. Alternatively open **index.html** from the extracted folder, retaining `js/`, `css/` and `assets/` beside it.
4. Import your own media from **Settings → Import media**.

Some Android file viewers are restricted embedded webviews. Use a full browser with JavaScript and storage enabled. Cryptography, microphone, PiP and native encoders depend on the browser and security context. The application detects unsupported operations rather than simulating them.

## Implemented systems

- Arabic/English UI, RTL/LTR, responsive layouts, 12 themes, 32 actual locally stored photographs, two bundled OFL fonts, and user-imported Arabic/Latin font files.
- IndexedDB library; file/folder import; content-based duplicate detection; original filenames; real covers/thumbnails; search, negative/quoted terms, filters, multi-key artist sorting, stars, color labels, favorites, pinned files, notes, playlists, smart rules and recoverable trash.
- Audio player, persistent queue, previous/next, volume, speed, repeat off/all/one, A–B loop, sleep timer, Media Session integration and a floating player.
- Web Audio EQ with 5/10/15/20 controls, actual frequency-response display, presets, preamp, channel balance, mono/swap and a compressor limiter. Real-time sound visualizers can be disabled.
- Local audio trim/render, WAV PCM16/24/Float32, sample-rate conversion, fades, gain, DC removal, normalization, gate, basic compression, high/low-pass, reverse, mono, channel swap and joining. Native compressed recording formats are offered only when the browser advertises them.
- Native video playback, ±10 seconds, fullscreen/PiP where supported, screenshots, SRT/VTT/LRC parsing, subtitle offset, chapter markers, video contact sheets and histogram-based scene-cut analysis.
- Native video re-recording with range, dimensions, frame-rate/bit-rate targets, speed, pixel color effects, watermark and burned captions. Keep the page visible; this export runs near real time, not an arbitrary-speed FFmpeg transcode.
- Image editor with actual pixel processing, draw/erase/text, crop, rotate/flip, resize, layers, opacity/blending, undo/redo, saved layer projects, export compression/target-size search, batch recipes, image conversion, watermarks, comparison and contact sheets. Histogram, perceptual hash and perspective functions are provided as engine APIs; not all have a user-facing panel.
- Actual embedded metadata writing for MP3, FLAC, RIFF WAV, non-fragmented MP4/M4A/MOV, JPEG XMP and PNG XMP. This is not merely renaming a library label. Edited output is read back for verification.
- AES-GCM encrypted vaults with PBKDF2-wrapped random data keys, encrypted file metadata/covers, authenticated chunks, idle/background lock, encrypted export/import, password changes and separate recovery keys. Wrong recovery keys are authenticated before any credential is overwritten.
- A local command assistant for supported Egyptian Arabic, Arabic and English commands; quoted text is retained, parameters and durations are parsed, actions are allowlisted, and 12,000 unique generated grammar/parameter fixtures are tested. This is not an unrestricted offline LLM.
- 50 real built-in `.jomsx` recipe extensions: 20 image recipes, 6 EQ recipes, 12 complete themes and 12 smart-library recipes. Imported script pages run in opaque, network-restricted iframes with a limited metadata bridge.
- ZIP library backup/merge/restore, local font assets in backups, workspace snapshots, CSV/JSON exports and real usage statistics.

## Important scope boundaries

This release **does not implement every one of the 320 proposed extensions**. The numbered scope ledger in `docs/FEATURES.csv` preserves the requested items and their status. UI controls are wired to implemented operations; absent advanced processors are not represented as working AI buttons.

Not shipped: universal all-codec conversion or MP3/FLAC encoding; neural super-resolution, neural frame interpolation, speech transcription or object segmentation; a general offline language model; full multitrack NLE/multicam/keyframe export; an arbitrary model loader; biometric unlocking; complete HEIC/TIFF/GIF animation editing; sample-accurate universal gapless playback; direct linked-file storage; automatic folder watching. Those require additional actual codecs/models/implementation and device testing, not just a JavaScript menu. No remote service is silently substituted.

Native APIs vary: background playback can be interrupted by the operating system, native encoding formats vary, and storage persistence is a browser decision. No software can guarantee every browser/device, unlimited files or zero defects. Image/audio operations use explicit processing budgets to avoid uncontrolled memory allocation.

## Edited download contract

The original blob is retained. An edited download contains rendered image/audio/video changes when applied. Supported metadata formats are rewritten and then read back. Tag-only audio/video changes preserve the media payload. Format limitations are disclosed rather than claiming unsupported fields were embedded. WAV INFO fields and image metadata are not displayed by every external player.

Vault exports are encrypted `.jomsv` packages. A normal file downloaded after unlocking is an intentionally decrypted copy. Losing both password and recovery key prevents recovery. A password-only visual overlay is never used as cryptography.

## Offline installation

The single-file edition has all required app assets embedded and does not register a service worker. A hosted HTTPS edition can cache its local assets through `sw.js` for subsequent offline visits. User media remains in IndexedDB, not the service-worker cache. No runtime fonts, media processors, analytics or assistants are fetched from a third party.

## Source layout

- `js/core.js`, `binary.js`, `tags.js`, `store.js`, `vault.js`: shared services and binary persistence.
- `js/audio.js`, `image.js`, `video.js`: actual processing engines.
- `js/assistant.js`, `plugins.js`: local commands and extension packages.
- `js/ui.js`, `views-*.js`, `app.js`: separated presentation and interaction.
- `css/studio.css`: responsive visual system and themes.
- `assets/`: local photographs, previews, fonts, icons and full attribution/licenses.
- `tests/`: optional development checks. They are not needed to use the app.
- `scripts/`: optional packaging helpers. They are not runtime dependencies.

## Validation

See `docs/QA.md`. The developer tests use Node's built-in modules plus an independently installed FFmpeg/ffprobe for format validation. No Node/npm is needed by visitors. Synthetic test media is generated during QA; users' personal files are not included in the repository.

## References

- [ID3 native frames](https://id3.org/id3v2.4.0-frames)
- [FLAC format](https://xiph.org/flac/format.html)
- [Apple media atoms](https://developer.apple.com/documentation/quicktime-file-format/atoms)
- [Web Crypto](https://www.w3.org/TR/webcrypto/)
- [Web Audio](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
- [MediaRecorder](https://developer.mozilla.org/en-US/docs/Web/API/MediaRecorder)
- [FontFace](https://developer.mozilla.org/en-US/docs/Web/API/FontFace)
- Photography and font attribution: `assets/ASSETS.md`, `assets/CREDITS.json`, and the included license files.
