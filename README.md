# Lament

A 2D rogue-lite built in Unity as a final year project at the University of Southampton, where I acted as Lead Technical Designer and Programmer.

<table align="center">
  <tr>
    <td><img height="350" alt="LamentGameplay_1" src="https://github.com/user-attachments/assets/d2b86cfa-b0ff-4c15-8e70-332f9343bb50" /></td>
    <td><img height="350" alt="LamentGameplay_2" src="https://github.com/user-attachments/assets/5372302c-c912-41b2-a632-cf716427e62e" /></td>
  </tr>
  <tr>
    <td><img height="350" alt="LamentGameplay_3" src="https://github.com/user-attachments/assets/f0ca6567-0a82-4797-b44a-6068dc442e42" /></td>
    <td><img height="350" alt="LamentGameplay_4" src="https://github.com/user-attachments/assets/ca6026a0-84a6-4fbf-9afc-cf71624b2868" /></td>
  </tr>
</table>

https://github.com/user-attachments/assets/e0c3eb41-8a5d-4951-877c-54d833664c54


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

- Unity Version 2022.3
- C#
- Git for version control

## Team

- Design - [Anna Bonadio](https://www.linkedin.com/in/anna-bonadio-022412241/)
- UI + Art - [Aysa Atalay](https://www.linkedin.com/in/aysaatalay/)
- Programming + Art - [Xane El Deen Rashad](https://www.linkedin.com/in/xane-el-deen-r-444943338/)
- Art - [Riya Limbu](https://www.linkedin.com/in/xane-el-deen-r-444943338/)
- World Building - [Joshua Bates](https://www.linkedin.com/in/joshuabates05/)

## Running it

Downloadable .zip file on itch.io. Extract the file and run the executable.
