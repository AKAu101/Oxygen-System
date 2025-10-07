# Unity Oxygen System

A dynamic oxygen management system for Unity that tracks player oxygen levels with visual feedback and safe zone mechanics.

## Includes 
First-Person-Character-Controller-3D for test purposes -> https://github.com/AKAu101/First-Person-Character-Controller-3D

## Features

- **Oxygen Depletion**: Oxygen gradually depletes over time when the player is outside safe zones
- **Sprint Mechanics**: Oxygen depletes faster when the player is sprinting
- **Safe Zones**: Designated areas where oxygen automatically restores
- **Visual Feedback**: Real-time UI slider showing current oxygen levels
- **Death State**: Player enters a death state when oxygen is fully depleted

## Requirements

- Unity 2021.3 or higher
- Unity Input System package
- Character Controller component
- UI Slider component

### Safe Zone Setup

1. Create a GameObject for your safe zone (e.g., a cube or trigger volume)
2. Add a Collider component (Box Collider, Sphere Collider, etc.)
3. Check **"Is Trigger"** on the collider
4. Create a new tag called `OxygenArea` and assign it to the GameObject

## Configuration

### Oxygen Script Parameters

| Parameter | Description | Default |
|-----------|-------------|---------|
| Oxygen Level | Starting oxygen amount (set in code) | 15 |
| Oxygen Max Capacity | Maximum oxygen capacity | Set in Inspector |
| Normal Depletion Rate | Oxygen loss per second while walking | 1.0 |
| Sprint Depletion Rate | Oxygen loss per second while sprinting | 2.5 |

### Restoration Rate

Oxygen restores at 2x the normal depletion rate when inside a safe zone. You can modify this in the code:

```csharp
oxygenLevel += Time.deltaTime * 2f; // Change 2f to adjust restoration speed
```

## How It Works

1. **Oxygen Depletion**: When outside safe zones, oxygen decreases based on the current depletion rate
2. **Sprint Detection**: The system checks if the player is sprinting via the `FirstPersonController` and adjusts depletion accordingly
3. **Safe Zone Detection**: Uses trigger colliders to detect when the player enters/exits oxygen areas
4. **UI Update**: The slider value is updated every frame to reflect current oxygen percentage
5. **Death State**: When oxygen reaches zero, the `isDead` flag is set and oxygen stops depleting


## License

This system is provided as-is for educational and commercial use.
