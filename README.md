# Rust Chess Game

A simple chess game implemented in Rust using the ggez game engine.

## Features

- Graphical chess board with piece images
- Complete chess piece movement according to rules:
  - Castling (kingside and queenside)
  - En passant captures
  - Pawn promotion to queen, rook, bishop, or knight
- Rules enforcement:
  - Check detection
  - Checkmate detection
  - Stalemate detection
  - Can't move into check
  - Can't castle through check or while in check
- Complete draw conditions:
  - Draw by threefold repetition
  - Draw by fifty-move rule
  - Draw by insufficient material
- Turn-based gameplay
- Visual highlighting of selected pieces and possible moves
- Game management:
  - New game button
  - Algebraic notation coordinate display
- Network play:
  - Host or join multiplayer games
  - Real-time move synchronization
  - Game listing and selection
  - Player name customization

## Requirements

- Rust (latest stable version recommended)
- ggez game engine dependencies (automatically installed via Cargo)

## Running the Game

1. Clone this repository
2. Navigate to the project directory
3. Run the game using Cargo:

```
cargo run --release
```

## Network Play

To play against other players over the network:

### Starting a Server

```
cargo run --release -- --server
```

### Playing a Network Game

```
cargo run --release -- --network [--address SERVER_ADDRESS] [--name PLAYER_NAME] [--join GAME_ID]
```

- `--address`: Optional server address (default: localhost:8080)
- `--name`: Optional player name
- `--join`: Optional game ID to join directly

If no specific game ID is provided, you'll be prompted to create a new game or join an existing one.

## How to Play

- Click on a piece to select it
- Click on a highlighted square to move the selected piece
- Click on the selected piece again to deselect it
- The game automatically alternates turns between white and black
- When a pawn reaches the opposite end of the board, a promotion dialog appears
- When a king is in check, checkmate, or stalemate, the status is shown at the bottom
- Use the "New Game" button to reset the board and start again
- Algebraic chess notation coordinates are displayed on the board squares

## Draw Conditions

The game will automatically detect the following draw conditions:

- **Stalemate**: When the current player has no legal moves but is not in check
- **Threefold Repetition**: When the same position occurs three times
- **Fifty-Move Rule**: When 50 moves have been made by each player without a pawn move or capture
- **Insufficient Material**: When neither player has enough pieces to checkmate (e.g., king vs king)

## Technical Details

The game structure is organized into several modules:

- `piece.rs`: Defines the chess pieces and their movement rules
- `board.rs`: Manages the game state, board representation, and rule enforcement
- `gui.rs`: Handles rendering, user interaction, and integrated networking
- `assets.rs`: Manages loading and displaying piece images
- `network.rs`: Contains client networking functionality
- `server.rs`: Implements the multiplayer game server
- `main.rs`: Entry point that sets up the game window and event loop

## Future Improvements

- Game history and move notation
- Load and save functionality
- AI opponent
- Enhanced network play features 