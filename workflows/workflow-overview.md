# 📚 Love, Lease & Obey --- Workflow Overview

This document explains the automated storytelling system workflow for
generating infinite, interconnected episodes using Make.com, GPT, and
structured JSON files.

------------------------------------------------------------------------

## 🗂 Folder Structure

  ----------------------------------------------------------------------------
  Folder                 Purpose
  ---------------------- -----------------------------------------------------
  `global_continuity/`   Contains all dynamic JSON files for score,
                         relationships, active arcs, pending hooks, escalation
                         queue, and recent episodes.

  `episodes/`            Stores all generated episode JSON files.

  `characters/`          Houses all character profiles as JSON, updated
                         dynamically as needed.

  `building/`            Contains lore, AI phases, point systems, and building
                         behavior rules.

  `workflows/`           Stores prompt templates, scenario logic guides,
                         workflow diagrams, and automation documentation.
  ----------------------------------------------------------------------------

------------------------------------------------------------------------

## ✅ Workflow Process Diagram (Visual Reference)

> Refer to the included diagram image `workflow-visual.png` for a
> high-level visual flow.

------------------------------------------------------------------------

## ✅ Workflow Steps (Detailed)

### **1. Trigger New Episode Generation**

-   Trigger: Scheduled automation or completion of previous episode
    cycle.\
-   Pulls current state from:
    -   `building_state.json`
    -   `active_relationships.json`
    -   Recent entries from `recent_episodes.json`
    -   `pending_plot_hooks.json`
    -   `arc_tracker.json`

------------------------------------------------------------------------

### **2. Choose Plot Device**

-   Selects a random category from `plot_devices.json` based on:
    -   Current AI phase (pulled from `building_state.json`)
    -   Character archetypes
    -   Frequency constraints (from `narrative_guidelines.json`)

------------------------------------------------------------------------

### **3. Load Episode Template**

-   Pulls structure from `episodes-template.json`.\
-   Fills each section (hook, reaction, escalation, vulnerability,
    cliffhanger) based on:
    -   Characters featured
    -   Plot device selected
    -   Current relationship dynamics\
    -   Arc progress cues

------------------------------------------------------------------------

### **4. Episode Generation via GPT**

-   Uses dynamic prompt with:
    -   Episode template structure
    -   Characters featured
    -   Current phase + building tone
    -   Continuity seeds and recent callbacks\
-   Generates a fully written 1000-word episode draft.

------------------------------------------------------------------------

### **5. Update Continuity**

-   After episode generation:
    -   `building_state.json` updated (score changes, phase transitions
        if applicable)
    -   `recent_episodes.json` updated with episode metadata
    -   `active_relationships.json` adjusted based on romantic/conflict
        outcomes
    -   `pending_plot_hooks.json` marked resolved or queued
    -   `arc_tracker.json` advances progress beats
    -   Escalation queue entries triggered or re-scheduled in
        `escalation_queue.json`

------------------------------------------------------------------------

### **6. Archive Data (Seasonal)**

-   Every 100 episodes:
    -   Move old entries from `recent_episodes.json` to
        `episode_history/`
    -   Move completed arcs from `arc_tracker.json` to
        `relationship_archive/`
    -   Perform cleanup and save backup states.

------------------------------------------------------------------------

## ✅ Prompt Layers Used in GPT Calls

-   Pull from `narrative_guidelines.json` for tone, forbidden elements,
    pacing targets.\
-   Reference `episodes-template.json` for scene structure.\
-   Reference `plot_devices.json` with twist instructions for fresh
    scenario generation.

------------------------------------------------------------------------

## 🔎 Summary

> This workflow ensures consistent tone, pacing, and continuity while
> enabling infinite episode creation at scale.\
> All components are designed to be modular, maintainable, and dynamic.

------------------------------------------------------------------------

## ➡️ Suggested Files in `workflows/`

  -------------------------------------------------------------------------
  File Name                Contents
  ------------------------ ------------------------------------------------
  `workflow-overview.md`   This document

  `workflow-visual.png`    The diagram visual

  `prompt-templates.md`    Pre-built GPT prompt structures for Make.com

  `scenario-logic.md`      Detailed explanation of escalation logic,
                           scoring updates, and narrative timing controls
  -------------------------------------------------------------------------

------------------------------------------------------------------------
