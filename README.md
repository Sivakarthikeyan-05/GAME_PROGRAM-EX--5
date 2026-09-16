# GAME_PROGRAM-EX--5

### NAME    : Sivakarthikeyan V 

### REG. NO.: 212225220098

---

# EXP: 5

## Making the Player Collect Ammo and Increase the Bullet Spawn Count

## Aim

To implement a gameplay feature where the player collects **ammo pickups** in the game world. When the player collects ammunition, the **AmmoCount** increases, allowing the player to spawn and fire more bullets.

---

## Procedure

### 1. Setup Player Character

* Open the `PlayerCharacter` Blueprint.
* Add a new **Integer** variable named:

`AmmoCount`

* Set an initial default value, for example:

`AmmoCount = 10`

* Ensure that the shooting mechanism uses `AmmoCount` to determine whether the player can fire a bullet.

---

### 2. Create Ammo Pickup Blueprint

* Open the **Content Browser**.
* Right-click → **Blueprint Class** → Select **Actor**.
* Name the Blueprint:

`BP_AmmoPickup`

### Add Components

Add the following components:

* **Static Mesh** — Represents the ammunition, such as a bullet or ammo crate.
* **Sphere Collision** — Detects when the player enters the pickup area.

### Event Graph

In the Event Graph of `BP_AmmoPickup`:

1. Add the `OnComponentBeginOverlap` event for the Sphere Collision.
2. Cast the overlapping actor to `PlayerCharacter`.
3. If the cast is successful, increase the player's `AmmoCount`.

For example:

`AmmoCount = AmmoCount + 5`

4. Optionally play a pickup sound or visual effect.
5. Destroy the `BP_AmmoPickup` actor after it has been collected.

---

### 3. Update Shooting Logic

Before spawning a bullet, check whether the player has available ammunition:

`AmmoCount > 0`

If the condition is true:

1. Spawn the bullet.
2. Decrease the ammo count by `1`.

Example:

`AmmoCount = AmmoCount - 1`

If `AmmoCount` is `0`, prevent the player from spawning another bullet until additional ammunition is collected.

---

### 4. Place Ammo Pickups in the World

* Drag instances of `BP_AmmoPickup` from the **Content Browser** into the game level.
* Position the ammo pickups at suitable locations.
* Adjust the Static Mesh and collision size as required.
* Place multiple ammo pickups throughout the level to allow the player to collect additional ammunition.

---

## Gameplay Flow

```text
Player starts
     ↓
AmmoCount = 10
     ↓
Player shoots
     ↓
AmmoCount decreases by 1
     ↓
AmmoCount reaches 0
     ↓
Player collects ammo pickup
     ↓
AmmoCount increases by 5
     ↓
Player can fire additional bullets
```

---

## Output

### Ammo Pickup

![Ammo Pickup](https://github.com/user-attachments/assets/ad7eefea-575c-44ae-9eca-6e9a623a8ef4)

<br>

### Ammo Collection Blueprint

![Ammo Collection Blueprint](https://github.com/user-attachments/assets/e82640a3-06c3-48e0-9abd-11a2e60640ba)

<br>

### Shooting and Ammo Logic

![Shooting and Ammo Logic](https://github.com/user-attachments/assets/ca2adaf2-d5b2-42fc-a40e-a81d6d69d965)

<br>

### Final Gameplay Output

![Final Gameplay Output](https://github.com/user-attachments/assets/e28cfc27-f127-40cf-94ba-e95d5fa1901f)

---

## Result

Successfully implemented an **ammo collection system** in Unreal Engine.

* The player starts with a limited number of bullets.
* When the player overlaps with an ammo pickup, the ammunition is collected.
* The player's `AmmoCount` increases.
* Each bullet fired decreases the `AmmoCount` by `1`.
* The player can fire additional bullets after collecting ammunition.
* The ammo pickup is automatically destroyed after collection.

Thus, the **player ammo collection and bullet spawn count system** was successfully implemented.
