# MOM, I'M LATE!!! — GAME DESIGN DOCUMENT

**Document status:** consolidated working specification  
**Project:** Mom, I'm Late!!!  
**Target platform:** Android  
**Engine:** Unity 6.6 / URP  
**Primary audience:** broad mobile-game audience  
**Budget constraint:** €0 initial development budget

This document records the current agreed vision. It distinguishes current requirements from deferred ideas and unresolved decisions. It is not a claim that these systems have already been implemented.

---

## 1. High concept

The player controls a school student who must reach the school gate before the morning deadline. The city is a compact, explorable labyrinth full of streets, alleys, obstacles and route choices. The player must navigate efficiently and collect the required student ID before arriving.

The central tension comes from **time, navigation, route choice and required objectives** — not from endless forward running.

### Core player promise

"Can you find the right way to school in time?"

## 2. Product and presentation

- Platform: Android mobile.
- Initial release direction: offline single-player.
- Orientation: landscape.
- Camera: third-person, positioned behind the protagonist.
- Art direction: colorful, playful, readable 3D cartoon visuals with a commercial mobile-game feel.
- The protagonist must have a distinct identity. During initial setup, the player chooses the character's first and last name.
- The first name change is free; later changes may cost XP. Exact price and rules are unresolved.
- Do not imitate the structure of Subway Surfers or Temple Run.

## 3. Narrative framing and daily schedule

The opening wake-up sequence is presented through comic panels / introductory presentation, not as playable gameplay.

Previously established story beats include:
- Wake-up time: 06:25.
- Alarm, mother, dog and bedroom chaos as comic events.
- Bus arrival reference: 06:30.
- The playable journey begins when the protagonist leaves home at **06:35**.

The playable objective is to reach the school gate by **07:55**. Arrival at 07:56 or later is a failure.

The maximum target duration for a real-time play session is approximately 15 minutes. Actual level timing and conversion between in-game time and real time must be tuned during playtests.

## 4. Main gameplay loop

1. Start the level and leave home at 06:35.
2. Identify the route through the urban labyrinth.
3. Explore streets, alleys, passages and shortcuts.
4. Locate and collect the required student ID.
5. Avoid collisions and unnecessary detours.
6. Reach the school gate no later than 07:55.
7. Evaluate the run and show the TEST result screen.
8. Continue to the next level or replay.

**Completion condition:** reach the gate by 07:55 **and** have the student ID.

## 5. Level and world structure

### Chapters and levels

- Long-term plan: approximately 10 chapters, each with approximately 100 levels.
- Chapter 1 is called **LA CITTÀ**.
- Levels are identified by number; do not add proper level names unless the owner decides otherwise.
- The first five levels are intended to teach the basic mechanics.
- The real challenge may begin around level 10 or earlier, subject to playtesting.
- Each level is an independent, complete labyrinth. The school position, start position and layout can vary between levels.
- There is no single fixed geometric shape for the world.
- Difficulty increases progressively.

Possible future chapter themes include real cities (Paris, Rome, New York, Tokyo) or environments such as ice, desert and fire. These are future possibilities, not first-prototype requirements.

### Labyrinth design

The city should feel like a plausible urban space, not a maze made of arbitrary invisible walls.

Possible route-shaping elements:
- Buildings and building blocks.
- Hedges and fences.
- Streets and intersections.
- Alleys and narrow passages.
- Rivers or other natural barriers.
- Shortcuts and alternate paths.

The level-generation workflow should generate a layout and then validate it. Invalid or impossible layouts must be corrected or rejected before play. The generator must ensure that required objectives and the finish are reachable.

No building interiors are required in the first playable build.

### Minimap

- Show the complete labyrinth, including areas the player has not explored yet.
- Show the player's position.
- Show the school with a continuously visible, blinking red marker.
- Rotate the minimap with the protagonist.
- The player should be able to understand their position and the overall route structure quickly.

### Traffic

Cars may move along roads as part of the city environment. Traffic behavior and collision rules need to be developed and tested carefully; they are not a prerequisite for the first basic prototype.

## 6. Player controls and movement

### Current control direction

- Virtual joystick on the left side of the screen.
- Jump button and camera button were part of the broader control concept, but manual jumping is **deferred** from the first prototype.
- Camera should remain behind the protagonist and provide understandable orientation.
- The player moves only while the joystick is being pushed.
- When the joystick returns to neutral, the character stops.
- No sprint mechanic for now.

### Deferred mechanics

- Manual jumping: not in the first prototype.
- Stamina: a possible design was automatic recovery while not in use, but stamina gameplay is currently inactive.
- Movement upgrades and equipment: future progression only.

Avoid automatic camera behavior that makes lateral movement confusing. The player must be able to understand the relationship between joystick direction, character movement and camera orientation.

## 7. Required item: student ID

The student ID is mandatory to complete a level.

- It is collected as a world item.
- Its position is randomized on each attempt among a set of predefined valid positions.
- The 3D card floats slightly and has a subtle glow to make it readable.
- Once collected, its icon disappears from the minimap.
- Reaching the gate without the ID does not complete the level.

Older design notes mentioned several possible gate checks and additional required objects. The current confirmed first-prototype requirement is the **student ID only**. Do not add other mandatory items without a new decision from the owner.

## 8. School subjects and books

The weekday-based subject schedule currently defined is:

| Weekday | Required subject |
|---|---|
| Monday | English |
| Tuesday | Mathematics |
| Wednesday | History |
| Thursday | Geography |
| Friday | Physical Education + Vocabulary |

The in-game date should follow a real-world calendar-style date (example previously discussed: Wednesday, 12 May 2027).

The required subject book is part of the broader game design and TEST evaluation. Its exact role in the first prototype is not yet finalized. Do not make it a blocker for the first playable build unless the owner explicitly requests it.

Example result wording: **"Libro di storia"** for a History book.

## 9. TEST result screen

The result screen is called **TEST**. A school report / PAGELLA presentation is deferred to a possible future feature.

### Grade

- Grade range: 0–10.
- 0–5: fail.
- 6–10: pass / level completed.
- 6 is the minimum passing grade when arriving at the last acceptable moment.
- 10 represents a run with no mistakes.
- 9 represents an excellent run with a possible time improvement.
- 8 represents a completed run with one significant shortcoming, such as timing or missing the required subject book.
- 7 represents a lower pass.
- Arrival exactly at 07:50 is **not** the maximum time score. Maximum time performance requires arriving before 07:50.
- Arrival from 07:50 through 07:55 incurs a time-related penalty.
- Arrival at 07:56 or later fails the level.

### Penalty categories

The design calls for exactly four penalty categories. Three are currently identified:
1. Missing required subject book.
2. Accidents / collisions.
3. Arrival between 07:50 and 07:55.

The fourth category is not confirmed in the available decisions. **Do not invent it.** Keep the scoring model configurable until the owner defines it.

Scoring examples from the current design:
- Approximately two penalties should commonly result in 8/10.
- One typical issue should commonly result in 9/10.
- 10/10 should require a clean run, but should not be so rare that it feels unattainable.

The precise scoring formula and thresholds still need implementation design and playtesting.

### Visual direction

- Clean game UI, not a notebook-page imitation.
- White / clean background.
- Player name and surname at top-left.
- "TEST DI [materia]" at top-center.
- XP reward displayed in blue (example: "XP: +80").
- Positive indicators green; negative indicators black / marked.
- Relevant icons for book, road, time and ID.
- Key answer values in bold.
- Example values previously discussed: "7 min 52 sec", "3.1 km", "Raccolta" for ID, "Libro di storia".
- Avoid underlines and blue ruled-paper lines.
- Handwritten visual treatment may be explored later, but should remain readable and not obstruct information.
- Buttons: replay at bottom-left and next level at bottom-right.
- Stars animate one by one.
- A 10/10 result can show "PERFETTO!" with a normal star animation.
- Show the current result; do not display the previous record on this screen.

## 10. Progression, XP and stars

- Stars per level: 1–10.
- Only improvement over the player's previous best awards incremental stars.
- Example: improving from 2 to 5 stars awards +3; an equal or worse result awards 0 additional stars.
- Maximum total for a level is 10 stars.
- XP is awarded for results; exact economy and balancing remain to be specified.
- Name changes: first change free; subsequent changes may cost XP, with the exact cost unresolved.

## 11. Cosmetics and monetization direction

Initial game direction:
- Offline game.
- Future online functionality may include advertising.
- Cosmetic purchases / rewards only; cosmetics must not provide gameplay advantages.

Possible cosmetics:
- Clothes, shoes, backpacks, trousers, shirts, hoodies, jackets, caps and hats.
- Themed skins (an astronaut outfit is one example).
- Animations.

Future progression ideas may include equipment or transport options (for example a bicycle, scooter, motorbike, rollers or other movement-related items). These ideas need careful balancing and are not part of the first prototype.

Vehicle examples previously discussed:
- Free old bicycle from Uncle Franco: slow, medium resistance.
- Gigi's new scooter: fast, but performs poorly on grass, dirt or damaged sidewalks.
- Personal motorbike: possible later unlock.

Do not implement pay-to-win advantages. Do not rush upgrades that maximize speed, stamina, visibility or carrying capacity.

## 12. First playable prototype — strict scope

The first prototype should be intentionally small.

### Must have

- One simple city level.
- A third-person player controller.
- Camera behind the character.
- Left-side virtual joystick.
- Character stops when input is neutral.
- A small, readable urban layout with multiple route choices.
- Student ID pickup.
- School gate / finish trigger.
- Basic timer / deadline logic.
- Success and failure feedback.
- Android landscape build target, after editor playtesting.

### Must not have yet

- Manual jump.
- Sprint.
- Active stamina system.
- Building interiors.
- Complex traffic simulation.
- Full chapter / level progression.
- Full cosmetics shop or monetization.
- Online features.
- Every planned TEST scoring detail.
- Complex vehicles and upgrades.

The first prototype should prove that navigating a small city labyrinth under time pressure is enjoyable and understandable.

## 13. Technical project context

Known development environment:
- Unity 6.6.
- Universal Render Pipeline (URP), package version 17.6.0.
- Windows development PC.
- Visual Studio Code.
- Unity Personal.
- Generated assets have been used in the project, including a generated materials folder named `Assets/MomImLateGeneratedMaterials`.
- A generated bedroom root has been named `MIL_CompleteBedroom_Generated`.

Technical safety rules for changes:
- Do not delete manually created scene roots or assets.
- Generators should create their own clearly named roots and should not destroy unrelated objects.
- Avoid generic object names such as Cube, Plane, Sphere or Cylinder for project-specific generated objects.
- Keep scripts modular and explain where they belong.
- Before changing scenes, prefabs, project settings or packages, inspect the existing project structure and current state.
- Never assume that a script has been tested or that a build succeeds without running the relevant validation.

## 14. Open decisions / unresolved details

The following must remain open until explicitly decided:
- Fourth TEST penalty category.
- Exact grade formula and penalty weights.
- Exact XP reward formula.
- Exact in-game / real-time clock conversion.
- Exact level-generation algorithm and validation constraints.
- Exact traffic and collision behavior.
- Whether the subject book is mandatory in the first playable prototype.
- Detailed controls and camera tuning.
- Price of later character-name changes.
- Future online, ads and monetization implementation.
- Detailed vehicle / equipment progression.

## 15. Design change policy

When the owner makes a new explicit decision:
1. Record the decision and date in the relevant documentation.
2. Update any affected sections and dependent documents.
3. Identify which older decision is superseded.
4. Do not silently change unrelated systems.
5. If a decision is ambiguous, ask one focused clarification rather than inventing a rule.
