# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [x] Describe the game's purpose.
      The game is a number guessing game where the player chooses a difficulty, guesses the secret number, and receives hints after each guess. The goal is to guess the correct number before running out of attempts while the app tracks score, attempts, and guess history.

- [x] Detail which bugs you found.
      There were three main bugs while testing the game. First, the game accepted guesses outside the allowed range instead of rejecting them. Second, the high and low hint messages were reversed, so the game sometimes told the player to go higher when the guess was already too high. Third, the game sometimes displayed “Out of attempts” and revealed the answer even though the screen still showed that one attempt was left.



- [x] Explain what fixes you applied.
      The game logic was refactored into logic_utils.py so functions like difficulty range handling, guess parsing, guess checking, and score updating could be tested more easily. Range validation was added so out-of-range guesses are rejected, the high/low hint logic was corrected, and the attempts counter was changed to start at 0 so the player gets the correct number of attempts. The reset logic was also updated so pressing New Game or changing difficulty starts a fresh game with a new secret number, cleared history, reset score, and reset attempts.

## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. User enters a guess of 25
2. Game returns "Go HIGHER!"
3. User enters a guess of 30 -> "Go LOWER!"
4. Game ends after correct guess
5. Score is updated with the final score
6. Selecting new difficulty starts a new game

**Screenshot** *(optional)*: <!-- Insert a screenshot of your fixed, winning game here -->

## 🧪 Test Results

============================= test session starts ==============================
platform linux -- Python 3.13.0, pytest-9.0.3, pluggy-1.6.0
rootdir: /mnt/c/vs/ai110/week2/ai110-module1show-gameglitchinvestigator-starter
plugins: anyio-4.13.0
collected 3 items

tests/test_game_logic.py ...                                             [100%]

============================== 3 passed in 0.09s ===============================

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, describe the Enhanced UI changes here — a screenshot is optional]
