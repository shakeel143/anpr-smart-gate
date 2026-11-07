
# 🚧 ANPR Smart Gate (Test Prototype)

A single-file, browser-based prototype of a university gate system. It reads vehicle number plates from a live camera, checks them against an authorized list, and uses a hybrid auto/guard decision flow. The barrier is simulated with an on-screen message for now.

**Live demo:** https://shakeel143.github.io/anpr-smart-gate/

## Features

- Live camera plate scanning (rear camera on phones), with multi-frame voting
- OCR in the browser using Tesseract.js (no server needed)
- Authorized vehicle list (plate, owner, designation) with CSV import/export
- Hybrid decision flow:
  - **Exact match** → gate opens automatically
  - **Close match** (1 character off, or O/0, B/8 style confusions) → guard confirms
  - **Unknown** → guard rejects, or asks and verifies (one-time, 24-hour temporary, or permanent)
  - **Blocked** plates never auto-open
- Event log and manual plate entry for testing
- Everything is stored locally in the browser (localStorage)

## How to use

1. Open the live demo link on your phone (HTTPS is required for the camera).
2. Tap **Start camera** and allow permission.
3. Fit the number plate inside the dashed box.
4. Watch the decision banner. Try the dummy plates, e.g. `ABC-123` (allowed), `LEA-999` (blocked).

No camera? Use **Take photo** or the **Manual test** box.

## Limitations

- Uses generic OCR with no plate detector, so the plate must sit inside the box.
- Accuracy on Pakistani plates (fonts, hand-painted plates, night, glare) is limited.
- This is a flow and UX test, not a production system.

## Roadmap

- [ ] Plate detector (YOLO) plus fine-tuned OCR on local plates
- [ ] Python/FastAPI backend with a database and guard dashboard
- [ ] Real barrier control (relay via Arduino/ESP32/Raspberry Pi) with a loop or radar safety sensor
- [ ] Audit reports and privacy policy for stored plate images

## Tech

HTML, CSS, JavaScript, [Tesseract.js](https://github.com/naptha/tesseract.js)
