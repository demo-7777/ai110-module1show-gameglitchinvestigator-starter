# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| Guess: 9999 | Program should reject guess because it is out of range of 1 to 100 | Program accepts the guess and outputs the instruction to go lower or higher | none |
| Guess: 50 | Program should output "Go LOWER!" because the secret number was 26 | Program falsely outputs "Go HIGHER!" | none |
| Guess: 50, Attempts left: 1 | Program should only output instruction "Go LOWER!" or "Go HIGHER!" when there exists 1 attempt left | Program falsely outputs "Out of attempts! ..." and reveals the secret number and player's score | none |

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)? 
  ChatGPT

- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result). 
  AI suggested that high/low hint logic was reversed, which was correct. The fix was verified by running the app and seeing in the debug menu that after the change, the guesses led to the app correctly outputting either "Go HIGHER!" or "Go LOWER!"
  
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result). 
  AI suggested passing low and high into parse_guess to evaluate if guess was out of range. This suggestion was rejected because other instances in app.py, calls to parse_guess would have to be modified. It was simpler to move range checking to "if submit:" body. This decision was verified by running the game again and seeing that the game correctly recognized a guess to be out of the selected range.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
     By running the app again after adding a change and checking if the output or behavior was as intended.
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
     Pytest originally failed because check_guess normally returns a tuple containing both the result and the message. The tests were fixed by unpacking the tuple into variables 'result' and 'message', then comparing only the result value. After that, the three check_guess tests passed.
- Did AI help you design or understand any tests? How?
     Yes. AI highlighted the type error when comparing result and each literal string.
---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
   Streamlit reruns the app after user interactions, including submitting a guess, pressing New Game, or changing difficulty. Session state keeps values like guess history saved across those reruns, but the reset logic clears them when New Game is pressed or a new difficulty is selected.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
     Manually test each bug fix first before moving on to ensure the change actually fixed the bug.

- What is one thing you would do differently next time you work with AI on a coding task?
     Don't ask AI to do everything at once in one prompt. AI generally gives better suggestions when
     the prompt or task focuses on one component at a time.


- In one or two sentences, describe how this project changed the way you think about AI generated code.
     It is good at understanding code and identifying simple bugs but struggles to understand overall
     design principles and choices.