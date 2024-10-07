# GODOT-TEST

Folder Structure

/project-root
├── assets/
│   ├── images/
│   ├── sounds/
│   ├── fonts/
├── scripts/
│   ├── core/
│   ├── player/
│   ├── enemies/
├── scenes/
│   ├── levels/
│   ├── player/
│   ├── enemies/
├── docs/
│   ├── README.md
│   ├── CONVENTIONS.md
│   ├── CONTRIBUTING.md

2. README.md Example
# Godot Platformer Starter Project

## Project Overview
This is a starter file setup for platformer projects in Godot. It includes folders for assets, scripts, and scenes, along with boilerplate code for a player character.

## How to Run
1. Open the project in Godot.
2. Run the scene `scenes/levels/Level1.tscn`.

## Folder Structure
- `assets/`: Contains game assets (images, sounds, etc.).
- `scripts/`: All game logic scripts.
- `scenes/`: Predefined game scenes.
- `docs/`: Documentation for coding conventions and contributions.

## Attribution & License
All code is MIT licensed, and external assets must be attributed based on their original license.


3. CONVENTIONS.md Example
# GDScript Conventions

## Naming Conventions
- **Variables:** Use `snake_case` (e.g., `player_health`).
- **Constants:** Use `UPPERCASE_SNAKE_CASE` (e.g., `MAX_JUMP_HEIGHT`).
- **Functions:** Use `snake_case` (e.g., `move_player()`).
- **Classes:** Use `PascalCase` (e.g., `PlayerCharacter`).

## Indentation
- Use **tabs** for indentation.

## Line Length
- Limit lines to **80 characters** for readability.

## Comments
Use `#` for single-line comments and docstrings (`""" """"`) for function descriptions.

4. CONTRIBUTING.md Example
# Contributing to This Project

## Branching Strategy
- **Main Branch:** Contains the production-ready code.
- **Feature Branches:** Create new features on branches named `feature/[name]` (e.g., `feature/player-jump`).
- **Hotfix Branches:** For bug fixes, use `hotfix/[name]`.

## Commit Guidelines
- Use the conventional commit format:
  - `feat: [description]`
  - `fix: [description]`
  - `chore: [description]`

## Pull Requests
- Ensure your changes follow the conventions laid out in the `CONVENTIONS.md` file.
Provide detailed descriptions of the changes.




5. Sample GDScript (Player Movement)
# scripts/player/Player.gd
extends KinematicBody2D

const SPEED = 200

func _physics_process(delta):
    var velocity = Vector2.ZERO
    if Input.is_action_pressed("ui_right"):
        velocity.x += SPEED
    elif Input.is_action_pressed("ui_left"):
        velocity.x -= SPEED

    velocity = move_and_slide(velocity)

6. Boilerplate Files
Create a basic Level1.tscn in scenes/levels/, and a corresponding script for any core functionality (e.g., game manager).
7. Version Control Setup
Set up .gitignore to exclude build files.

# .gitignore
/.import/
/export/
