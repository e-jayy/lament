# Lament

A 2D rogue-lite built in Unity as a final year project at the University of Southampton, by a team of five across design, programming, and art.

<img width="2453" height="1344" alt="LamentGameplay_1" src="https://github.com/user-attachments/assets/4c18c39a-5308-4bf7-9b13-f9811ec1bb3e" />
<img width="1625" height="908" alt="LamentGameplay_4" src="https://github.com/user-attachments/assets/283eae9a-5216-41e7-9d3e-5a53a20b7664" />
<img width="2417" height="1327" alt="LamentGameplay_3" src="https://github.com/user-attachments/assets/2ab4dcbb-f01f-4504-914b-8af0c6f89118" />
<img width="1632" height="911" alt="LamentGameplay_2" src="https://github.com/user-attachments/assets/548ad9b6-954e-40ef-b12f-38a94c03e633" />


[**Play it on itch.io →**](https://e-jayy.itch.io/)

## What it is

A run-based dungeon crawler where every descent is procedurally generated and permanent choices in the skill tree carry over between runs.

## My contribution

I designed and programmed two of the game's core systems:

### Procedurally Generated Dungeon System
- **Algorithm:** Used a grid-based, breadth-first expansion algorithm with pseudo-random number generators and rule-based room placement.
- **Design:** Rooms would instantiate outwards from a "starter room" from arrays of rooms with entrances leading to the room it came from, repeated until either a certain number of rooms or generations was reached. This would then spawn a boss gateway in the last instantiated room.

### Skill Tree

- **Data-driven skills:** Each skill is a `SkillSO` ScriptableObject with a name, icon, max level and cost. Each button in the tree has a `SkillSlot` component that points to one of these assets.
- **Prerequisites:** Each slot has a list of prerequisite slots, set in the Inspector. A skill unlocks once every skill in its list is unlocked and at max level.
- **Event-driven unlocking:** When a skill is maxed, `SkillSlot` fires an `OnSkillMaxed` event. `SkillTreeManager` listens for it, re-checks every locked slot and unlocks any that now meet their prerequisites.
- **Currency:** Upgrades cost Terra Shards. `SkillTreeManager` checks the player can afford a skill before upgrading it, then takes the cost off their balance.
- **Saving progress:** Unlocked skills and their levels are kept in `PlayerStatsManager`, which persists across scenes, so the tree rebuilds its state each time it opens.
- **Stat effects:** `SkillManager` listens for upgrades and applies each skill's effect, such as max health, move speed, damage, shard drop rate or unlocking the boss key.

I also acted as technical lead, which meant leading technical decisions and coordinating communication across design, programming, and art disciplines.

## Tech

- Unity
- C#
- Git for version control

## Team

Design - [Anna Bonadio](https://www.linkedin.com/in/anna-bonadio-022412241/)
UI + Art - [Aysa Atalay](https://www.linkedin.com/in/aysaatalay/)
Programming + Art - [Xane El Deen Rashad](https://www.linkedin.com/in/xane-el-deen-r-444943338/)
Art - [Riya Limbu](https://www.linkedin.com/in/xane-el-deen-r-444943338/)
World Building - [Joshua Bates](https://www.linkedin.com/in/joshuabates05/)

## Running it

Downloadable .zip file on itch.io. Extract the file and run the executable.
