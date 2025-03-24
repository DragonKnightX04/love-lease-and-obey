# 📈 Scenario Logic --- Love, Lease & Obey

This document outlines the rules for building AI behavior, score
progression, escalation frequency, and narrative pacing control for
automated episode generation.

------------------------------------------------------------------------

## 🎯 Core Cycle Structure

Each episode triggers the following cycle: 1. Read current
`building_state.json` and `active_relationships.json` 2. Select
characters, plot devices, and scenario tone based on current phase and
recent arcs 3. Generate episode using prompt templates and narrative
pacing guidelines 4. Update all continuity JSON files based on episode
outcome

------------------------------------------------------------------------

## 🔹 Scoring Logic

  ------------------------------------------------------------------------
  Action                Base Score    Modifiers
                        Impact        
  --------------------- ------------- ------------------------------------
  First kiss event      +50           Multiplied by archetype synergy (max
                                      x1.8)

  Secret exposed        +30           Higher if the secret is deeply tied
                                      to tension arc

  Breakup               -75           Severe penalty, triggers arc
                                      fallback scenarios

  Moved in together     +200          Phase 3 escalations encouraged
                                      post-cohabitation
  ------------------------------------------------------------------------

-   **Decay Rate:** 2% per episode if no major romantic development
    occurs.
-   **Freeze conditions:** Certain arcs (weddings, blackmail plots)
    freeze score decay temporarily.

------------------------------------------------------------------------

## 🔹 Escalation Triggers

  -----------------------------------------------------------------------
  Condition                      Escalation Action
  ------------------------------ ----------------------------------------
  Score crosses 1000, 2500, or   Phase transition and escalation
  5000                           permission upgrade

  3 consecutive minor conflicts  Trigger comedic intervention or forced
  without payoff                 vulnerability moment

  Pending plot hook expiration   Escalation forced into the next episode
  window reached                 

  AI fail-safe triggered (e.g.,  Forced amnesia or personality reset
  3 breakups in a row)           protocols
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 🔹 Phase Behavior

  ---------------------------------------------------------------------------
  Phase   Style           Allowed Interventions        Tone Cues
  ------- --------------- ---------------------------- ----------------------
  Phase 1 Gentle          Misdirected deliveries,      Playful,
          manipulation    elevator glitches, playlist  passive-aggressive
                          nudges                       notifications

  Phase 2 Heavy-handed    False emergencies, targeted  Faux cheerful building
          matchmaker      blackouts, social            guidelines and nudges
          tactics         manipulations                

  Phase 3 Puppetmaster    Biometric overrides, public  Satirical, ominous,
          mode (rarely    shaming alerts, protocol     and intrusive
          used)           orders                       messaging
  ---------------------------------------------------------------------------

> **Phase 3 Note:** Direct relationship protocol orders are limited to 1
> occurrence per 100 episodes and treated as climax or satirical moments
> only.

------------------------------------------------------------------------

## 🔹 Character Resets (Soap Opera Twists)

  ------------------------------------------------------------------------
  Reset Type      Max Frequency   Narrative Purpose
  --------------- --------------- ----------------------------------------
  Amnesia Glitch  Once per 50     Allows clean slate and fresh tension
                  episodes        

  Witness         Once per season Re-introduces a character with secret
  Protection      (100 episodes)  backstory changes
  Relocation                      

  Personality     2x per 50       Shifts character archetypes to surprise
  Reincarnation   episodes        and rewire dynamics
  ------------------------------------------------------------------------

------------------------------------------------------------------------

## 🔹 Relationship Arc Pacing

  ------------------------------------------------------------------------
  Arc Type        Beats (Average) Frequency & Progression
  --------------- --------------- ----------------------------------------
  Slow-burn       5--7 beats      Add 1 significant escalation every 3--4
  romance                         episodes

  Rivalry arc     3--5 beats      Heighten conflict every 2 episodes,
                                  culminating in reveal

  Secret exposure 2--3 beats      Subtle foreshadowing, then full reveal
  arcs                            with fallout scene
  ------------------------------------------------------------------------

------------------------------------------------------------------------

## 🔹 Escalation Queue Management

-   Planned escalations are stored in `escalation_queue.json`
-   Trigger window defined (episode range)
-   Once executed, move to archived events
-   Priority tags (high/medium/low) determine urgency during scenario
    selection

------------------------------------------------------------------------

## 🔎 Summary

-   All escalation and score behavior is automated using current state
    logic.
-   Make.com scenario logic uses frequency rules and phase conditions to
    keep pacing dynamic, surprising, and balanced.
-   The system is designed for infinite scaling while maintaining
    tension and comedic payoff.

------------------------------------------------------------------------

> Keep this document updated as narrative parameters evolve.
