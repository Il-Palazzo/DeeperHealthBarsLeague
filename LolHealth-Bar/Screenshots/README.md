# Background Screenshots Directory

This directory stores clean League of Legends gameplay screenshots or replay frames (.png / .jpg) that serve as background terrain for the synthetic training pipeline in `DataSetGenerator.ipynb`.

---

## ⚠️ CRITICAL REQUIREMENT: No In-Game Health Bars or GUI

> [!IMPORTANT]
> The screenshots placed in this directory **MUST NOT contain in-game health bars or GUI elements**.

### Why?
The synthetic data generator pastes freshly rendered, perfectly labeled health bars onto these background images. If the background screenshots already have native health bars:
1. New health bars may overlap with existing ones.
2. The preexisting health bars will not be labeled in the YOLO ground-truth files, teaching the model to ignore valid health bars as "background noise".

---

## 🎮 How to Capture Clean Background Screenshots in League of Legends

### Method 1: Using Replay Mode (Recommended)
1. Open any match replay from the League of Legends client.
2. Press **`U`** to toggle off the replay timeline, scoreboards, and player interface.
3. In League settings (**Esc** → **Interface**):
   - Under **Health and Resource Bars**, uncheck:
     - ❌ *Show Health Bars*
     - ❌ *Show Summoner Names*
   - Or toggle off champion/minion health bar keybinds.
4. Run `ScreenshotCollector.ipynb` to capture clean frames while the replay plays.

### Method 2: In-Game (Practice Tool or Custom Game)
1. Launch a **Practice Tool** game.
2. Press **`Ctrl + Shift + H`** to toggle off the entire in-game HUD/GUI.
3. Disable health bars in **Interface** settings.
4. Walk around lanes, river, jungle, and bases while `ScreenshotCollector.ipynb` records background frames.

---

## Technical Specifications
- **Recommended Resolution:** `1920x1080` (or native monitor resolution).
- **Formats:** `.png`, `.jpg`, `.jpeg`.
- **Quantity:** 50–200 unique screenshots provide sufficient background diversity for training.
- **Git Tracking:** All image files in this directory are ignored by `.gitignore` so your personal captures are never uploaded to GitHub.
