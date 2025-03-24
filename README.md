# love-lease-and-obey
Experimental AI from a failed dating app takes over a smart apartment complex

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
