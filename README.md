# Pocket Chess Online — Android Studio project v2

## Run
1. Extract this ZIP.
2. Open `PocketChessOnline` in Android Studio.
3. Allow Gradle sync and install Android SDK 35 if prompted.
4. Run on an Android device or emulator (minimum Android 6.0 / API 23).

## Included in this build
- Modern dark mobile UI and chessboard
- Standard legal movement, king safety, check/checkmate/stalemate
- Castling, en passant, automatic queen promotion
- Undo, move history, SAN-like move labels, PGN export and basic PGN import
- Configurable chess clock, sound toggle, board flip
- Experimental heuristic AI with easy/medium/hard settings
- WebSocket connection UI and JSON message protocol scaffold

## Important online multiplayer note
This project does **not** include a hosted multiplayer backend. The WebSocket UI expects a server that understands:
- Client join: `{"type":"join","room":"ROOM","fen":"..."}`
- Client move: `{"type":"move","room":"ROOM","from":"e2","to":"e4","promotion":"Q","fen":"..."}`
- Server broadcasts authoritative moves as `{"type":"move","from":"e2","to":"e4","promotion":"Q"}`
The backend should authenticate users, validate moves on the server, manage room membership, handle reconnection and clocks, and reject illegal or out-of-turn moves. Do not expose secrets in the client. A production service should use TLS (`wss://`).

## Limitations / review before production
This is a starter project, not a certified chess engine or Play Store-ready release. AI is heuristic rather than minimax search. PGN import supports common SAN moves but has not been tested against every PGN variation, comments, disambiguation, or result edge case. Online mode is only a client protocol scaffold until a compatible server is supplied. Draw claims, repetition adjudication, insufficient-material detection, and selectable promotion are not fully implemented. Review and test thoroughly before release.
