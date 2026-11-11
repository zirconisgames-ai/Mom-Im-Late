# MOM, I'M LATE!!!

**Official development repository** for *Mom, I'm Late!!!*, a 3D cartoon mobile game for Android developed with Unity.

> **Project status:** early development / repository setup.  
> **Current priority:** build and playtest a small, working first prototype before expanding the game's systems.

## The game in one sentence

Reach the school gate before the 07:55 deadline, find the correct route through an explorable urban labyrinth, and make sure you have collected your student ID.

## Core identity

- **Genre:** third-person urban exploration, timed labyrinth and route-finding.
- **Platform:** Android.
- **Engine:** Unity 6.6, Universal Render Pipeline (URP).
- **Visual direction:** colorful, readable, funny 3D cartoon style.
- **Camera:** third-person camera behind the protagonist.
- **Orientation:** landscape.
- **Design constraint:** this is not an endless runner. Each level is an explorable urban environment with multiple possible routes.

## Repository map

- `Documentation/GAME_DESIGN.md` — consolidated game vision, rules and design decisions.
- `Documentation/DEVELOPMENT_ROADMAP.md` — development phases, priorities and acceptance criteria.
- `Documentation/AI_COLLABORATION.md` — working protocol for ChatGPT, Claude and the human project owner.
- `UnityProject/` — reserved for the actual Unity project. It will be populated from the working project on the developer's PC; it is not a substitute for that local project.

## First playable milestone

Create one small, complete and testable city level:

1. A controllable third-person character.
2. A simple cartoon urban environment with several route choices.
3. A student ID placed at one valid location.
4. A school gate / finish point.
5. A clear success or failure condition based on reaching the gate by 07:55 while carrying the ID.

The first prototype deliberately excludes manual jumping, sprinting, stamina gameplay, building interiors and complex progression systems.

## Development principles

1. **Working prototype before feature expansion.**
2. Preserve the project's non-runner identity.
3. Do not invent or silently change agreed design decisions.
4. Keep the first build small enough to test frequently.
5. Prefer automated, reproducible Unity workflows where practical.
6. Protect existing Unity scenes, assets and manually created objects when generating content.
7. Keep documentation synchronized with implemented behavior; clearly label ideas that are not implemented.

## Important

The design document is the consolidated reference for the current vision. If a later user decision conflicts with an older note, the later explicit decision takes precedence. Unresolved details must remain marked as unresolved rather than being guessed.

See the [game design](Documentation/GAME_DESIGN.md), [roadmap](Documentation/DEVELOPMENT_ROADMAP.md) and [AI collaboration protocol](Documentation/AI_COLLABORATION.md).
