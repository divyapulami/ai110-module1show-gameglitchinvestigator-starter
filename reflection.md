# 💭 Reflection: Game Glitch Investigator



## 1. What was broken when you started?

- What did the game look like the first time you ran it?
> When I first ran the game, it looked like a simple number guessing game built with Streamlit. The interface worked, and I could enter guesses and press the submit button. However, the game behavior was inconsistent and confusing. Even when I knew the secret number from the developer debug panel, the hints did not always make sense.

- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").
  > The first bug I noticed was that the hint messages were backwards. When I entered a number higher than the secret number, the game sometimes told me to go higher instead of lower. The second bug was that the game accepted numbers outside the allowed range, including negative numbers, even though the instructions said the guess should be between 1 and 100. I also noticed that after pressing the New Game button, the previous guess remained in the textbox.
  

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
> I used ChatGPT and GitHub Copilot in VS Code while working on this project. ChatGPT helped explain why certain bugs were happening and suggested possible fixes. Copilot helped me examine sections of the code and understand how some functions worked.

- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
Ans:  One correct suggestion from AI was to fix the hint logic inside the check_guess() function. The original code returned messages that did not match the comparison results. The AI suggested correcting the logic so that guesses greater than the secret return "Too High – Go Lower" and guesses smaller than the secret return "Too Low – Go Higher." I verified this by testing the game with numbers above and below the secret number and confirming the hints were correct.

- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).
Ans: At one point, the AI suggested clearing the textbox by directly modifying st.session_state.guess_input after the widget had already been created. When I tried this, Streamlit produced an error saying the session state could not be modified after the widget was instantiated. This showed that the suggestion did not follow Streamlit's rules for widget state management. I fixed the problem by using a different input key approach instead.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
Ans: I tested each change by running the Streamlit app and manually entering different guesses. I used the developer debug panel to see the secret number and verify that the hints matched the expected behavior. If the hints and results were consistent across multiple guesses, I considered the bug fixed.

- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
  Ans: One test I ran was entering guesses above and below the secret number to confirm the hint logic worked correctly. For example, if the secret number was 50 and I guessed 60, the game correctly displayed "Too High – Go Lower." When I guessed 40, it displayed "Too Low – Go Higher." This confirmed that the comparison logic was working as intended.

- Did AI help you design or understand any tests? How?
Ans: Yes, AI helped suggest testing different edge cases such as negative numbers and numbers larger than the allowed range.
---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
Ans: The secret number kept changing because Streamlit reruns the entire script whenever the user interacts with the app. If the secret number is generated directly during those reruns, it gets replaced each time the script executes again. This made the game behave unpredictably.

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
Ans: Streamlit reruns the entire Python script whenever something changes in the interface, such as clicking a button or entering text. Session state acts like memory that allows certain values to persist between those reruns. Without session state, variables would reset every time the app refreshed.

- What change did you make that finally gave the game a stable secret number?

Ans: The secret number was stored in st.session_state so that it would only be generated once per game instead of every time the script reran. This allowed the secret number to remain consistent while the player continued making guesses.

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
Ans: Ans: One habit I want to continue using is testing small fixes step by step instead of changing many parts of the code at once. By focusing on one bug at a time, it was easier to identify what actually fixed the problem.

  
- What is one thing you would do differently next time you work with AI on a coding task?
Ans: Next time I would provide more context to the AI earlier in the process. Including specific code sections or describing the bug more clearly would likely lead to more accurate suggestions. 

- In one or two sentences, describe how this project changed the way you think about AI generated code.
Ans: This project showed me that AI-generated code is helpful but not always correct. Developers still need to carefully review, test, and sometimes reject AI suggestions. AI can speed up debugging, but it does not replace understanding the code.
