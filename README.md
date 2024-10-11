# GODOT-TEST

Folder Structure

/project-root
├── .ADDONS
│   ├── links/
│   ├── plugins/
├── .ASSETS
│   ├── animations/
│   ├── fonts/
│   ├── images/
│   ├── sounds/
├── .DOCS
│   ├── README.md
│   ├── CONVENTIONS.md
│   ├── CONTRIBUTING.md
├── .SCENES
│   ├── enemies/
│   ├── levels/
│   ├── main/
│   ├── player/
│   ├── ui/
├── .SCRIPTS
│   ├── core/
│   ├── player/
│   ├── enemies/
│   ├── managers/
│   ├── ui/
│   ├── utils/
├── .GIT
│   ├── GODOT-TEST/
│       ├── README.md
│   ├── gitignore
├── project.godot
Essential Files

1. README.md (/docs/README.md)
# Godot Platformer Starter Project

## Project Overview
This starter file is designed for creating platformer games in Godot. It contains a structured folder layout for assets, scripts, and scenes, along with boilerplate code for player movement, basic platformer mechanics, and documentation to guide you through development.

## How to Run
1. Open the project in Godot.
2. Navigate to `scenes/levels/Level1.tscn`.
3. Run the scene.

## Folder Structure
- `assets/`: Stores all assets such as images, sounds, and fonts.
- `scenes/`: Pre-built game scenes like levels, players, and enemies.
- `scripts/`: All gameplay logic, split into core components, player control, enemies, and UI.
- `docs/`: Documentation on conventions, contribution, and project guidelines.

## Attribution & License
- The source code is licensed under MIT.
- Any external assets should follow their respective licenses.

2. CONVENTIONS.md (/docs/CONVENTIONS.md)
# GDScript Conventions for This Project

## Naming Conventions
- **Variables:** Use `snake_case` for variables (e.g., `player_speed`).
- **Constants:** Use `UPPERCASE_SNAKE_CASE` for constants (e.g., `MAX_JUMP_HEIGHT`).
- **Functions:** Use `snake_case` for function names (e.g., `move_player()`).
- **Classes:** Use `PascalCase` for class names (e.g., `PlayerCharacter`).

## Indentation
- Use **tabs** for consistent indentation.

## Line Length
- Keep line length under **80 characters** for better readability.

## Comments
- Use `#` for inline comments.
- Write meaningful docstrings to explain the functionality of functions when necessary.

## File Naming
- Use **lowercase and underscores** for file names (e.g., `player_movement.gd`).
- Assets should use a descriptive naming system (`background_music.wav`, `player_sprite.png`).

## Scene Naming
- Use `PascalCase` for scene names (`Player.tscn`, `Level1.tscn`).

3. CONTRIBUTING.md (/docs/CONTRIBUTING.md)
# Contributing to the Platformer Project

## Branching Strategy
- **Main Branch:** Production-ready code.
- **Feature Branches:** Use `feature/[name]` for new features (e.g., `feature/player-jump`).
- **Hotfix Branches:** Use `hotfix/[name]` for urgent bug fixes.

## Commit Guidelines
- Follow this format:
  - `feat: [brief description]` for new features.
  - `fix: [brief description]` for bug fixes.
  - `chore: [brief description]` for maintenance work.

## Pull Requests
- Ensure your changes align with the conventions outlined in `CONVENTIONS.md`.
- Provide a description of your changes and the issue they address.

4. Player Movement Script (/scripts/player/Player.gd)
extends KinematicBody2D

const SPEED = 200
const JUMP_FORCE = -500
const GRAVITY = 900
var velocity = Vector2.ZERO

func _physics_process(delta):
    velocity.y += GRAVITY * delta
    velocity.x = 0

    if Input.is_action_pressed("ui_right"):
        velocity.x = SPEED
    elif Input.is_action_pressed("ui_left"):
        velocity.x = -SPEED

    if is_on_floor() and Input.is_action_just_pressed("ui_up"):
        velocity.y = JUMP_FORCE

    velocity = move_and_slide(velocity, Vector2.UP)

5. Platform Setup (/scenes/levels/Level1.tscn)
Create a StaticBody2D with CollisionShape2D and an Image for platforms.
Use a basic platform sprite (e.g., platform.png) to form the platforms.

6. Coin Collection (/scripts/ui/Coin.gd)
extends Area2D

signal collected

func _ready():
    connect("body_entered", self, "_on_body_entered")

func _on_body_entered(body):
    if body.name == "Player":
        emit_signal("collected")
        queue_free()

7. Game Manager (/scripts/core/GameManager.gd)
extends Node

var score = 0

func _ready():
    $Player.connect("player_died", self, "_on_player_died")
    $Coin.connect("collected", self, "_on_coin_collected")

func _on_coin_collected():
    score += 10
    print("Score: ", score)

func _on_player_died():
    print("Game Over")

8. Version Control (/.gitignore)
# Ignore Godot import/export files
.import/
.export/

# Ignore system files
.DS_Store
.idea/
.vscode/
