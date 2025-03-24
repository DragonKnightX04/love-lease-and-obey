# love-lease-and-obey
Experimental AI from a failed dating app takes over a smart apartment complex

# 🛠 Master Scenario Flow & Reference Guide — *Love, Lease & Obey*

This document outlines the entire workflow from trigger to deployment for Make.com scenario automation.  
Use this guide step-by-step to build your scenario logic confidently.

---

## ✅ Full Scenario Flow (In Order)

### **1. Trigger**
- **Method:** Scheduled trigger (daily/weekly) OR manual webhook.
- **Purpose:** Start a new episode generation cycle.

---

### **2. Load Continuity Data**
- **Pull from:**
  - `building_state.json` (current phase, score)
  - `active_relationships.json` (current character relationships)
  - `recent_episodes.json` (last 5–10 episodes for rotation logic)
  - `pending_plot_hooks.json` (hooks that should be resolved)
  - `arc_tracker.json` (ongoing arcs)
- **Why:**  
  - This informs character selection, escalation potential, and story continuity.

---

### **3. Character Selection**
- **Data accessed:**
  - `relationships.json` (anchor couples, tension arcs)
  - `recent_episodes.json` (avoid recent repetition)
- **Logic:**
  - Priority: rotate anchor couples not featured in the last 3 episodes.
  - Fallback: select random pairing weighted toward unresolved arcs or tension potential.

---

### **4. Select Plot Device**
- **File used:** `plot_devices.json`
- **Logic:**
  - Random selection with weighting:
    - Favor devices not recently used.
    - Adjust weighting by current phase (phase 1 = light glitches, phase 3 = stronger interventions).
  - Optional freshness bias: deprioritize devices used in the past 5 episodes.

---

### **5. Select Building Location**
- **File used:** `building_locations.json`
- **Logic:**
  - Random selection, weighted to cycle between:
    - Common spaces
    - Specialty spaces
    - Hidden/uncommon locations every 5 episodes
  - Exclude recently used locations.

---

### **6. Assemble Prompt**
- **Use:**
  - `episodes-template.json` for structure.
  - `prompt-templates.md` for writing style and formatting.
  - Inject:
    - Selected characters’ quirks and secrets (pulled from `characters/` JSON profiles).
    - Plot device.
    - Building location.
    - Current phase tone rules (from `narrative_guidelines.json`).
    - Phase-appropriate manipulation guidance.

---

### **7. Send Prompt to GPT**
- **API Call:** OpenAI GPT completion with temperature ~0.9 for creative variance.
- **Tokens:** Set output length for ~1000 words.

---

### **8. Parse GPT Output**
- Separate:
  - Episode Title
  - Story body
  - Metadata (characters featured, plot device used, location, score impact)
- Optional fallback: if output is incomplete, retry once.

---

### **9. Save Episode Markdown File**
- **Format:**  
  - File name: `E###-episode-title.md`
  - Markdown structure:
    - `# Episode Title`
    - Story body with scene breaks `---`
- **Save to:** `episodes/` folder.

---

### **10. Update Continuity Files**
- Update:
  - `building_state.json` (score increase, potential phase shifts)
  - `recent_episodes.json` (log new episode ID, characters, device, location)
  - `active_relationships.json` (tension or attraction adjustments)
  - `pending_plot_hooks.json` (mark resolved hooks; add new hooks if cliffhanger)
  - `arc_tracker.json` (advance arcs or mark milestones)
  - `escalation_queue.json` (schedule future big moments if escalation threshold met)

---

### **11. Commit & Push to GitHub**
- Commit:
  - New markdown episode
  - All updated JSON files
- Include descriptive commit message:
  - “Episode E### — [Title] generated. Continuity files updated.”

---

### **12. Optional Post-Publish Actions**
- Trigger webhook to Cloudflare Pages (if needed) to refresh content.
- Send Slack/Telegram notifications with episode summary.

---

## ✅ Reference: File Purposes

| File Name                  | Purpose                                                   |
|----------------------------|-----------------------------------------------------------|
| `building_state.json`      | Holds current phase, score, escalation thresholds         |
| `active_relationships.json`| Tracks current attraction and rivalry intensities         |
| `relationships.json`       | Maps existing connections, archetypes, and relationship arcs|
| `plot_devices.json`        | Master list of plot devices with category weighting       |
| `building_locations.json`  | Master list of locations with usage rotation logic        |
| `episodes-template.json`   | Episode structural blueprint for GPT prompt               |
| `prompt-templates.md`      | Style, pacing, tone instructions for prompt assembly      |
| `pending_plot_hooks.json`  | Unresolved hooks that must be addressed                   |
| `arc_tracker.json`         | Progress tracking for long-term relationship arcs         |
| `recent_episodes.json`     | Log of most recent episodes for rotation checks          |

---

> This guide is your master reference for building each module and automating the entire episode generation cycle in Make.com.


----

# 📂 Global Continuity — Love, Lease & Obey  
This folder contains the live memory files that power narrative continuity, relationship tracking, and plot arc progression for the AI-generated story universe.

## 📑 File Overview

### **1. `building_state.json`**  
- Stores current building score, active AI phase, total episode count, and the most recent escalation event.  
- Updated every episode to reflect score changes and phase transitions.  
- **Used by:** The AI to determine tone, allowed interference levels, and escalation scale.

---

### **2. `active_relationships.json`**  
- Tracks only the **active, high-intensity relationships** between characters (romantic tension, enmity, protector dynamics).  
- Includes intensity ratings (0–1 scale) and recent interactions to influence scene writing.  
- **Used by:** The AI to build natural callbacks and deepen relationship arcs.  
- **Archived relationships** are moved to `relationship_archive/` seasonally.

---

### **3. `recent_episodes.json`**  
- Contains metadata of the last 50 episodes (ID, timestamp, characters featured, plot devices used, score impacts).  
- After each new episode, the oldest entry is dropped, and the latest added.  
- **Used by:** The AI to create continuity callbacks, references, and subtle foreshadowing.

---

### **4. `pending_plot_hooks.json`**  
- Holds unresolved secrets, upcoming twists, or narrative setups not yet paid off.  
- Each hook has an assigned episode window and status (`pending` or `resolved`).  
- **Used by:** Make.com scenario logic to ensure hooks get resolved on schedule.

---

### **5. `arc_tracker.json`**  
- Monitors long-term relationship arcs (both romantic and rivalry-based).  
- Tracks progress (beats completed), next episode targets, and current intensity.  
- **Used by:** The AI to structure slow-burn plots and tension arcs over dozens of episodes.

---

### **6. `escalation_queue.json`**  
- Contains planned escalation events with assigned characters and trigger windows.  
- Escalations are marked as `executed` and archived after activation.  
- **Used by:** The scenario logic to schedule future building manipulations.

---

## 🛠️ Update Cycle & Management Rules
| Event                | Action                                                  |
|----------------------|---------------------------------------------------------|
| After each episode   | Update `building_state.json`, `recent_episodes.json`, `active_relationships.json` |
| Every 10 episodes    | Add new plot hooks or escalate unresolved ones in `pending_plot_hooks.json` |
| After arc resolution | Move closed arcs to `relationship_archive/` folder, update `arc_tracker.json` |
| Phase transition     | Update `building_state.json` and escalate planned events in `escalation_queue.json` |

---

## 🗄️ Archival Structure (Seasonal)
| Archive Folder               | What It Stores                                         |
|------------------------------|--------------------------------------------------------|
| `relationship_archive/`      | Completed arcs, long-past tensions or resolved enmities |
| `episode_history/`           | Full metadata for all episodes beyond the last 50      |

---

## 🔎 Querying Advice for Make.com
- Pull only the **latest entries** from `recent_episodes.json` (last 5–10 episodes) for AI prompting.  
- Reference `arc_tracker.json` and `pending_plot_hooks.json` every generation cycle to ensure ongoing continuity.  
- Use `building_state.json` to dynamically adjust escalation and narrative tone.

---

> **Tip:** Periodically back up the `global_continuity/` folder after major plot arcs resolve or at season-end milestones.
