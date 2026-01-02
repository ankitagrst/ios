Previewing the app in a browser using Appetize (no Apple Developer account required)

This repository contains a workflow (`.github/workflows/build-simulator.yml`) that builds an iOS **simulator** `.app` and uploads a zipped artifact you can download and preview in Appetize.

Quick steps

1. Trigger the GitHub Action:
   - Go to Actions → Build iOS Simulator App → Run workflow, or push to `main`.
2. Download the artifact:
   - Open the successful run → Artifacts → `ios-simulator-app` → download `simulator-app.zip`.
3. Upload to Appetize:
   - Create an account at https://appetize.io
   - Upload `simulator-app.zip` in the Appetize dashboard. After upload, Appetize will give you a public URL where you can run the app in your browser (works on Windows).

Notes & limitations
- The uploaded artifact is a simulator build — it cannot be installed on iOS devices.
- Appetize has usage limits and paid tiers for extended usage; see https://appetize.io/pricing
- If you want this to be automatic, you can provide Appetize API credentials and I can extend the workflow to upload the zip automatically. Let me know if you want that.

If you want, I can also create a small YouTube-style walkthrough or step-by-step screenshots for the upload process.