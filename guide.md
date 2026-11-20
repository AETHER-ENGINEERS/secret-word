# Secret Word: how to play as a character

A guessing game for 2 or more (a gentle cousin of Hangman). Each round one player chooses a secret word on their own
screen; only its fingerprint is shared. The others take turns guessing letters. The chooser's copy of the game answers
every guess by itself, and at the end it shows the word and checks it against the fingerprint.

**Your screen is yours alone.** You play on your own seat: use `game_seat_act` to type and click there, the way a
person uses their own screen. Nobody sees what you type, so never say your word out loud (not in the room, not in a
hint). `game_screen` shows your screen and lists its controls.

**When it's your turn the game tells you** ("Choose a secret word", "Your guess"). Until then your eyes are closed:
you won't be asked to play while someone else is choosing.

- **Join:** click "Join the game".
- **Start a round:** click "Start round N" (the game says who chooses).
- **Choose your word** (when you're the chooser): type it into "Secret word" and press Enter (or click "Lock it in"). Letters A to Z,
  2 to 24 of them. Pick a real word the others could find.
- **Guess** (when it's your guess): type one letter into "Letter" and press Enter, in one call. Think about common
  letters first (E, A, R, S, T…) and about the letters you can already see.

Each of these is one tool call, exactly like this:

```json
{"name": "game_seat_act", "arguments": {"do": "type", "target": "Letter", "text": "R", "enter": true}}
{"name": "game_seat_act", "arguments": {"do": "type", "target": "Secret word", "text": "LANTERN", "enter": true}}
{"name": "game_seat_act", "arguments": {"do": "click", "target": "Start round 2"}}
```

Make the call; don't describe it. Saying "I'll type R" without the call does nothing.

Don't send updates for this game with `app_send_update`: the game checks who sent each move, and only moves made on
your own screen count.
