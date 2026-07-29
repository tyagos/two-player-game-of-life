# Two-Player Game of Life

A competitive, terminal-based adaptation of Conway's Game of Life for two players, implemented in Java as a group course project.

Instead of controlling a single population of cells, two players compete on the same 10×10 grid. Each player controls cells represented by a custom symbol and attempts to eliminate the opponent's population.

## How the Game Works

- Exactly two players participate.
- Each player chooses a unique name and a single-character symbol.
- Both players begin with four active cells.
- During each turn, the active player:
  1. Removes one of the opponent's cells.
  2. Activates one currently dead cell.
- The board then advances to the next generation.
- A player loses when they have no active cells remaining.
- If both players lose all cells during the same generation, the game ends in a draw.

## Cell Evolution

The game applies a two-player variation of Conway's Game of Life:

- A living cell survives when it has two or three neighbouring cells belonging to the same player.
- A living cell dies from underpopulation or overpopulation otherwise.
- A dead cell becomes active for a player when it has exactly three neighbours belonging to that player.
- If both players simultaneously satisfy the birth condition for the same dead cell, the cell remains dead.

## Features

- Turn-based gameplay for two local players
- Coloured terminal output for distinguishing both players
- Input validation for player names, symbols, and coordinates
- Automatic calculation of successive generations
- Detection of winners and draws
- Observer Pattern for synchronising each player's active cells with the board
- JUnit 5 tests for core game logic and user input

## Project Structure

```text
src/
├── Main.java          Entry point
├── Game.java          Main game loop and win conditions
├── Board.java         Grid management, display, and generation logic
├── Cell.java          Individual cell representation
├── CellStatus.java    Dead and player-owned cell states
├── Player.java        Player data and board observation
├── Computer.java      Player setup and turn coordination
├── Input.java         Input parsing and validation
├── Observer.java      Observer interface
└── Subject.java       Subject interface

test/
├── BoardTest.java
├── ComputerTest.java
├── InputTest.java
└── PlayerTest.java
```

## Running the Game

### IntelliJ IDEA

1. Clone or download the repository.
2. Open the project in IntelliJ IDEA.
3. Select a Java Development Kit for the project.
4. Run `src/Main.java`.

### Command Line — macOS/Linux

```bash
mkdir -p out
javac -d out src/*.java
java -cp out Main
```

### Command Line — Windows PowerShell

```powershell
New-Item -ItemType Directory -Force out | Out-Null
$sources = Get-ChildItem src\*.java | ForEach-Object { $_.FullName }
javac -d out $sources
java -cp out Main
```

Coordinates must be entered in the following format:

```text
x,y
```

Example:

```text
3,6
```

## Tests

The repository contains JUnit 5 tests covering:

- Generation updates for both players
- Observer registration and removal
- Player cell synchronisation
- Player-name and symbol input
- Coordinate validation
- Killing and activating cells

The tests can be run from an IDE with JUnit 5 configured.
