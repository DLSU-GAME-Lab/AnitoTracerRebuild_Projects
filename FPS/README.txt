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
and TakeDamage(amount), as in the Spaceship project; add such a script to targets
in this project if damageable targets are needed.

The arrow-key actions are registered by the AnitoTracer engine. Rebuild and run
the updated engine before opening this project; older engine builds do not
register FPS_LOOK_LEFT, FPS_LOOK_RIGHT, FPS_LOOK_UP, or FPS_LOOK_DOWN.
Open FPS.aproject and enter Play mode to build and run the project scripts.
