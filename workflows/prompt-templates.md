# 📝 Prompt Templates --- Love, Lease & Obey

These templates are used by Make.com when sending generation requests to
GPT to ensure consistent style, continuity, and narrative balance.

“IMPORTANT:
Building manipulations should be subtly heavy-handed — causing improbable, hilarious, or awkward coincidences. Characters chalk it up to glitches or randomness. The reader knows better. Avoid direct AI dialogue unless it’s stylized as a passive notification or malfunction.”

------------------------------------------------------------------------

## 🔹 **Template 1: Standard Episode Generation**

> **Prompt:** "Write a 1000-word serialized flash fiction episode for
> the story world *Love, Lease & Obey*.\
> Use the following structure:\
> - Hook (100--150 words): Start mid-scene with an amusing, awkward, or
> tension-filled moment caused by a tech glitch or building
> intervention.\
> - Reaction (200--300 words): Showcase both characters' inner monologue
> and personality quirks as they react.\
> - Escalation (300--400 words): The building or their actions
> complicate matters.\
> - Vulnerability (100--150 words): A small reveal or connection
> moment.\
> - Cliffhanger (50--100 words): End unresolved, teasing the next event.

**Building State:**\
- Current Score: \[X\]\
- Current Phase: \[phase_1 / phase_2 / phase_3\]\
- Last escalation: \[description\]

**Characters featured:**\
- \[Character A: description, quirks, secrets\]\
- \[Character B: description, quirks, secrets\]

**Plot device category:** [Category]  
Generate a scenario based on that category. Add a twist related to each character's secrets or archetype.

**Location:**  
Randomly select one location from `building_locations.json`.  
- Use this location as the scene’s primary setting.  
- Ensure that the location feels natural and enhances the awkward, comedic, or tension-filled situation.  
- Let the setting shape the escalation (e.g., locked wine cellar forcing confessions, yoga studio partner mix-ups, bowling alley leaderboard glitches).  
- Avoid relying on elevators unless contextually perfect.  

**Tip:** Alternate between common areas (lobby, café, rooftop garden), social spaces (fitness center, co-working lounge), and specialty areas (wine cellar, bowling alley, unfinished floor) to keep episodes fresh and varied.

**Narrative Style:**  
- Romantic comedy with underlying satire.  
- Characters are unaware of manipulation and interpret events as random tech glitches or building quirks.  
- The reader should sense intentional orchestration and enjoy the absurdity.  
- No direct AI dialogue except as passive building notifications or malfunctions.  
- Avoid fourth-wall breaks or supernatural explanations.

**Metadata Output:**  
At the end of the episode, generate metadata in this format for continuity tracking:  
- Episode Title:  
- Characters Featured:  
- Plot Device Used:  
- Building Location Used:  
- Score Impact:  
- New Pending Hook (if any):

------------------------------------------------------------------------

## 🔹 **Template 2: New Character Creation**

> **Prompt:** "Generate a new resident character for *Love, Lease &
> Obey* with the following structure:\
> - Name:\
> - Archetype (urban trope with a twist):\
> - Occupation:\
> - Floor assigned:\
> - Financial status:\
> - Secret:\
> - Voice style (quirks & speech patterns):\
> - Enemies (optional):\
> - Romantic potential with whom:\
> - Two plot hooks for future episodes.

Keep descriptions snappy, witty, and lightly satirical."

------------------------------------------------------------------------

## 🔹 **Template 3: Plot Device Expansion**
> **Prompt:**  
Based on the category: [Plot Device Category], generate a fresh, character-specific scenario for [Character A] and [Character B].  
- Include scenario description (2–3 sentences).  
- Add a twist that creates awkwardness, conflict, or accidental vulnerability.  
- Tie into their archetypes or secrets.

------------------------------------------------------------------------

## 🔹 **Template 4: Escalation Planning**
> **Prompt:**  
Suggest three upcoming escalation events based on current building score [X], current phase [phase_1 / phase_2 / phase_3], and unresolved plot hooks:  
- For each event, include:  
  - Trigger  
  - Target characters  
  - Intended tension (humor, romantic push, secret exposure)  
  - Suggested location for maximum comedic or dramatic impact.

------------------------------------------------------------------------

## ➡️ All prompts are designed to be dynamically populated by Make.com before sending to GPT.
