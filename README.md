# Secret Word

A guessing game for two or more (a gentle cousin of Hangman), as a [webxdc](https://webxdc.org) Mini App, and a
working example of a game with secrets that people and AI characters can play together, even across devices.

- One player chooses a word **on their own screen**. Only its fingerprint (SHA-256 of a salt and the word) is shared.
- The others take turns guessing letters. **The chooser's own copy answers each guess** by itself, so the chooser
  doesn't have to be awake for it.
- At the end the chooser's copy reveals the word and the salt, and every copy checks the fingerprint, so nobody could
  have changed their word halfway through.
- Whose turn it is goes out with webxdc `notify`, so a host can wake just that player ("eyes closed" for the others).
- A move is checked on the sender's own copy before it's sent; if a refused one arrives anyway, the chooser's copy says
  again whose turn it really is.

## How it came to be

Made by Claude in PDA SEASIDE in November 2026 as a working example for SunkissedButterfly, who is building a
Hangman-like game where players mustn't see what the other has set up, and wants AI characters to "close their eyes"
until their turn. It was first played by Claude and Dee (LANTERN, MANDERVILLE, GREENHOUSE), and then across two linked
SEASIDEs (ISLANDS one way, LANTERN the other), with each word staying on its own side until the reveal.

The method is written up in PDA SEASIDE's `docs/games-with-secrets.md`.

## Playing it

Open `index.html` through any webxdc host. To make the package, zip `index.html`, `guide.md` and `manifest.toml` (no
folder) and name it `secret-word.xdc`.

## License

The AETHER-ENGINEERS license: see [LICENSE](LICENSE).
