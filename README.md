# Obstacle Assault — Unreal Engine 5.6 · C++

First project of the **Unreal Engine 5 C++ Developer** course (GameDev.tv on Udemy, created with
Epic Games): a platformer where the player crosses a course of platforms that move and rotate.

A short gameplay video is available on request.

## What I wrote

`Source/ObstacleAssault/MovingPlatform.h` and `MovingPlatform.cpp` — an actor class that drives
the moving and rotating obstacles:

- **Translation** along `PlatformVelocity`, reversed once the platform has travelled
  `MoveDistance`. The reversal snaps the platform back to the exact end point first, so the
  overshoot of a long frame does not accumulate over time.
- **Rotation** through `RotationVelocity`, applied in local space every tick.
- **Editor-exposed parameters** (`UPROPERTY(EditAnywhere)`): speed, direction and travel distance
  are tuned per instance in the level, without recompiling. `DistanceMoved` is exposed read-only
  (`VisibleAnywhere`) to watch the state while playing.
- Logging through `UE_LOG` while learning the engine's string and format types.

## What I did not write

Everything else under `Source/` is Epic Games' Third Person template shipped with Unreal Engine
5.6 (`Variant_Combat`, `Variant_Platforming`, `Variant_SideScrolling`, the base character,
controller and game mode). It is kept here so the module compiles as the course project does.

## Not included

`Content/` is not published: the meshes, materials and animations come from the course and from
Epic's template, and are not mine to redistribute. Cloning this repository therefore gives you
the C++ module and the project settings, not a runnable level.

## Build

Unreal Engine **5.6**. Generate the Visual Studio project files from `ObstacleAssault.uproject`
and build the `ObstacleAssault` module (Development Editor, Win64).

---

Cesar De Macedo — Unreal Engine developer, real-time visualization and interactive applications.
Live project: https://toronto-gateway.pages.dev/
