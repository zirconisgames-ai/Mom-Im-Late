# DEVELOPMENT ROADMAP

**Status:** working plan — update as milestones are completed.  
**Priority:** a playable, testable prototype over a large amount of unfinished infrastructure.

## Guiding rule

Build the smallest complete version of the core game loop, test it, then expand. A feature is not complete because code exists: it is complete only after it has been tested in the intended Unity scene and its behavior is documented.

## Phase 0 — Repository and project foundation

**Goal:** make the project understandable and safe to collaborate on.

- [x] Create the GitHub repository.
- [x] Verify ChatGPT can read the private repository.
- [ ] Add and maintain core project documentation.
- [ ] Confirm the actual Unity project folder and its current state.
- [ ] Establish a reliable Unity-to-Git workflow.
- [ ] Add appropriate Unity `.gitignore` rules before uploading the full project.
- [ ] Confirm that large generated / cache folders are excluded.

**Exit criteria:** the repository has clear documentation and a verified, reproducible workflow for the actual Unity project.

## Phase 1 — First playable city block

**Goal:** prove the central navigation loop in the simplest possible environment.

Tasks:
1. Inspect the current Unity project before editing.
2. Create or identify a clean prototype scene without deleting existing work.
3. Build a small cartoon urban environment.
4. Add a third-person character and a camera that stays understandable.
5. Add the left virtual joystick.
6. Ensure neutral joystick input stops the character.
7. Add several route choices with plausible city obstacles.
8. Add the student ID pickup.
9. Add a school gate / finish trigger.
10. Add a simple deadline and success / failure state.

**Out of scope:** jump, sprint, stamina, building interiors, complex traffic, shops, progression and online systems.

**Exit criteria:**
- The player can start, move, stop and navigate.
- The ID can be collected.
- The finish can be reached.
- Finishing without the ID does not count as success.
- Arrival after the deadline fails.
- The complete loop can be replayed without restarting the Unity Editor.

## Phase 2 — First playtest and usability pass

**Goal:** determine whether the core loop is understandable and fun.

Test:
- Can a new player understand the joystick and camera?
- Are route choices visually legible?
- Is the school destination easy to identify?
- Is the ID discoverable without being trivial?
- Does the timer create pressure without feeling unfair?
- Are collisions and blocked paths understandable?

Record observations and make focused changes. Do not add new systems to compensate for unclear level design.

**Exit criteria:** the owner can complete multiple runs and identify specific, reproducible improvements.

## Phase 3 — Level and labyrinth foundations

**Goal:** move from a hand-authored test level toward repeatable level creation.

- Define level data structures.
- Define valid start, objective and finish placement.
- Generate plausible urban route layouts.
- Validate that required locations are reachable.
- Reject or repair invalid layouts.
- Support multiple routes with meaningful differences.
- Add the full minimap behavior: complete layout, player position and blinking red school marker; rotate with the protagonist.

**Exit criteria:** generated layouts pass automated checks and can be completed in playtests.

## Phase 4 — Core game systems

Develop in controlled increments:
- Student ID randomized among predefined valid positions.
- ID visual presentation and minimap removal after pickup.
- In-game date and weekday subject schedule.
- Subject-book behavior once its first-release role is decided.
- TEST result screen and configurable scoring.
- XP and incremental star progression.

Do not implement the unknown fourth penalty category until the owner defines it.

## Phase 5 — Content and progression

Only after the core loop is stable:
- Tutorial sequence (first five levels).
- Progressive difficulty.
- Independent levels with varying starts, finishes and school positions.
- Chapter 1: LA CITTÀ.
- Additional chapters and themed environments.
- Cosmetic character customization.
- Carefully balanced future transport / equipment ideas.

## Phase 6 — Android quality and release preparation

- Test on representative Android devices.
- Tune touch controls and camera.
- Profile performance and memory.
- Validate landscape orientation and UI safe areas.
- Test offline behavior.
- Prepare store assets and privacy / platform requirements when release planning begins.

Advertising, online features and monetization are future decisions, not prototype dependencies.

## Definition of done for any feature

A feature is complete only when:
1. Its intended behavior is clear.
2. It fits the agreed game design.
3. It is implemented in the correct Unity project / scene.
4. It has been tested in Unity.
5. Relevant errors and regressions are checked.
6. Documentation is updated.
7. The exact files and validation results are reported.

## Working priority

When choosing between tasks, use this order:
1. Fix blockers preventing the prototype from running.
2. Complete the core movement / navigation / objective loop.
3. Playtest and improve clarity and feel.
4. Build reusable level foundations.
5. Add secondary systems.
6. Add content and polish.

Avoid premature architecture, speculative systems and documentation that does not support the next implementation or test.
