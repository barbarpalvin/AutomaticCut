# Automatic Cut Lite

Automatic Cut Lite is a free, open source Adobe Premiere Pro extension that automatically detects and removes silences, breaths, and long pauses from your videos.

> **TR:** Automatic Cut Lite, videolarınızdaki sessizlikleri, nefesleri ve uzun boşlukları otomatik olarak tespit edip kesen ücretsiz ve açık kaynaklı bir Adobe Premiere Pro eklentisidir. [Türkçe dökümantasyon için buraya tıklayın (Read in Turkish)](README-tr.md)

---

## Key Features

* **Smart Silence Detection:** Uses FFmpeg to detect exact silence/breath intervals based on customizable dB thresholds.
* **Multi Track Slicer:** Cuts all video and audio tracks precisely without using Nested Sequences.
* **Auto Backup:** Preserves your original sequence by automatically duplicating it before applying cuts.
* **Custom Padding:** Allows you to leave natural breathing room (padding) before and after words to avoid robotic jump cuts.

## Prerequisites

* **Windows OS**
* **Adobe Premiere Pro** (Compatible with modern versions, built for 2026/24.x)
* **FFmpeg** (Must be installed and added to Windows System PATH)

---

## Installation Guide

### Step 1: Install FFmpeg

1. Download FFmpeg for Windows. I used the [BtbN version](https://github.com/BtbN/FFmpeg-Builds/releases) but it will not matter.
2. Extract the folder to your `C:` drive (e.g., `C:\ffmpeg`).
3. Open the Windows Start Menu, search for **Environment Variables**.
4. Select **Edit the system environment variables** -> Click the **Environment Variables** button.
5. Under *System variables*, find **Path**, click **Edit**, and add a new line: `C:\ffmpeg\bin`
6. Open Command Prompt (`cmd`) and type `ffmpeg -version` to verify it's working.

### Step 2: Enable Premiere Pro Debug Mode

*(Required for unsigned extensions)*

1. Open the Windows Start Menu and type `regedit` to open Registry Editor.
2. Navigate to: `HKEY_CURRENT_USER\Software\Adobe\CSXS.12`
*(Note: The number might be 11, 12, or 13 depending on your Premiere version. Do this for the highest number).*
3. Right click on the right panel -> **New** -> **String Value**.
4. Name it `PlayerDebugMode` and set its value to `1`.

### Step 3: Install the Extension

1. [Download this repository.](https://github.com/barbarpalvin/AutomaticCut/releases/tag/v1.0.0)
2. Copy the `Automatic Cut Lite` folder.
3. Paste it into the Adobe CEP extensions folder. Try the first path; if it doesn't exist or work, use the second:
* `C:\Program Files (x86)\Common Files\Adobe\CEP\extensions\`
* **OR** `C:\Program Files\Common Files\Adobe\CEP\extensions\` *(This one works for me, not sure the difference)*



---

## How to Use

1. Open Premiere Pro.
2. Go to the top menu: **Window** -> **Extensions** -> **Automatic Cut Lite**.
3. In your sequence, select the **MAIN AUDIO** clip (the one with the speaking voice). *Do not select all tracks, just the main audio.*
4. Adjust the Silence Threshold (dB) and paddings in the extension panel. *(Default profile is working fine)*
5. Click **"1. Analyze"**. Wait for the silence list to populate.
6. Click **"2. Apply Cuts"**.
7. The extension will backup your current sequence and create a perfectly cut timeline!

---

## Known Issues & Workarounds

* **Micro Gaps Between Cuts:** Occasionally, tiny gaps might remain between cuts in the newly generated sequence.
**Workaround:** You can easily clean these up by selecting `Sequence` -> `Close Gaps` from the Premiere Pro top menu.
* **Minor Sync Drifts in Multi Cam:** When working with multiple camera angles, one of the tracks might experience very minor synchronization drifts in certain parts of the timeline.
**Workaround:** You can manually re-sync those specific parts by using the cut points of the other clip as a reference. *I am currently working on an update to fix this issue in future releases.*
