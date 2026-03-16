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

- [ ] Describe the game's purpose.
- [ ] Detail which bugs you found.
- [ ] Explain what fixes you applied.


This project is a Streamlit number guessing game where the player must guess a secret number within a limited number of attempts.

During debugging I discovered several issues:
- The hint logic was reversed (higher/lower messages were incorrect).
- The game accepted numbers outside the allowed range.
- The secret number type changed between string and integer on different attempts.
- The New Game button did not reset the input field properly.

I fixed these issues by correcting the comparison logic in `check_guess()`, adding input validation in `parse_guess()`, keeping the secret number consistently as an integer, and resetting the game state when starting a new game.

## 📸 Demo

- [ ] [Insert a screenshot of your fixed, winning game here]

![Game Demo](Screenshots.png)

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, insert a screenshot of your Enhanced Game UI here]
