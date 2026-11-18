FPS controls

W/S: move forward/backward
A/D: strafe left/right
Arrow keys: look around
Space: jump (press again after landing)
Left mouse button: fire (hold for automatic fire)

The Player object uses a locked-rotation rigid body and a capsule collider.
FPSInput reads the controls and calls FPSMovement on the same Player. Its
Weapon field references the transform of an object with FPSWeapon.
FPSMovement drives Game Cam and exposes movement speed, jump speed, look speed,
eye height, and ground-check distance in the inspector.
The ground-check distance must reach slightly beyond the capsule's bottom.
The map uses a static mesh collider and the project's gravity.

The included Gun is a placeholder cube under Game Cam. Replace its model with
your gun mesh, or attach FPSWeapon to another gun object, parent it to Game Cam,
and assign that object's transform to FPSInput's Weapon field. The weapon's +Z
axis is its firing direction; adjust its Muzzle Offset to start shots outside
the player and gun. Damage, projectile speed, lifetime, scale, and firing
interval are adjustable on FPSWeapon. An optional AudioSource on the gun plays
when fired. FPSProjectile destroys itself on impact or when its lifetime ends.
It damages a hit object or ancestor with a Health script exposing IsDepleted()
and TakeDamage(amount). Prefabs/Target.aprefab has Health and FloatingTarget
scripts, a rigid body, and a collider; its health defaults to 100. Place a
FloatingTargetSpawner in the scene and assign that prefab. The existing Spawner
has Spawn On Start enabled and spawns within a sphere around its position; choose
a radius and position that keep targets inside the playable space. Enable Respawn
By Wave for repeated waves and use Max Alive to limit the number present.
Floating targets require a simulated rigid body with positive mass; unlock
rotation if they should tumble. An optional AudioSource plays on destruction.
Reopen the project if the editor already has an older version of the prefab
loaded. Let scripts finish compiling before entering Play mode.

The arrow-key actions are registered by the AnitoTracer engine. Rebuild and run
the updated engine before opening this project; older engine builds do not
register FPS_LOOK_LEFT, FPS_LOOK_RIGHT, FPS_LOOK_UP, or FPS_LOOK_DOWN.
Open FPS.aproject and enter Play mode to build and run the project scripts.
