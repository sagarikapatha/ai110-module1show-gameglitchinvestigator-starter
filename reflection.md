# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").\
When I first ran the game, the Streamlit page opened and showed the title “Game Glitch Investigator” with a box to enter guesses, difficulty settings, and the score, etc. The interface looked simple, so I started playing couple of rounds with different inputs and difficulty level. While playing it, I noticed some problems with the game behavior.They are:\
Bug1: The hints were incorrect, because when my guess was higher than the secret number the game told me to go higher instead of telling me to go lower.\
Bug2: Changing the difficulty level did not seem to fully affect the game, since the guessing range shown on the screen still looked the same.\
Bug3: While clicking on “New Game,” the game did not restart but the secret number was changing(everytime I click new game), and some information from the previous round seemed to remain.\
Bug4: The range of the difficulty levels are incorrect.\
Bug5: Negative scoring.
---
## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?\
GitHub Copilot
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).\
Copilot suggested moving the core game logic functions like check_guess, parse_guess, and update_score from app.py into logic_utils.py. This was correct because it separated the UI code from the game logic, making the program easier to maintain and test. I verified this by updating the imports in app.py, running pytest, and launching the Streamlit app to confirm the game still worked correctly.
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).\
Copilot initially suggested clearing the text input by setting st.session_state[f"guess_input_{difficulty}"] = "" after the guess was submitted. When I ran the app, Streamlit raised a StreamlitAPIException because widget state cannot be modified after the widget is created during the same run. I verified this by reading the error traceback. I fixed the problem by using a Streamlit form with clear_on_submit=True, which correctly resets the textbox after submitting a guess.
---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?\
I tested each fix in two ways: running automated tests with pytest and manually running the game using streamlit run app.py. If both the tests passed and the behavior worked correctly in the game, I considered the bug fixed.

- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.\
I created a pytest test to verify the check_guess function. For example, I tested that if the guess is 60 and the secret number is 50, the function returns "Too High" with the correct hint. When I ran pytest, the test passed, confirming that the high/low hint logic was fixed.

- Did AI help you design or understand any tests? How?\
Yes. Copilot helped generate a pytest test for the check_guess function. The AI suggested testing specific scenarios such as a correct guess, a guess that is too high, and a guess that is too low. I reviewed the test, adjusted the assertion slightly to avoid emoji encoding issues, and then ran the tests to verify the logic.
---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.\
The secret number changed because Streamlit reruns the entire script every time the user interacts with the app. If the secret number is generated normally with random.randint() each run, it will create a new number each time.

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?\
In Streamlit, the whole script runs again every time the user clicks a button or enters input. To keep information between runs, Streamlit provides session state, which stores values like variables that persist while the app is running.

- What change did you make that finally gave the game a stable secret number?\
I stored the secret number inside st.session_state.secret. This allowed the value to persist across reruns instead of being regenerated every time the app updated.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
 - This could be a testing habit, a prompting strategy, or a way you used Git.\
I want to continue writing small automated tests with pytest whenever I fix a bug. This helps confirm that the logic works correctly and prevents the same bug from appearing again later.

- What is one thing you would do differently next time you work with AI on a coding task?\
Next time, I would ask more focused prompts and review the AI suggestions carefully before applying them. Some suggestions looked correct but caused errors when running the code.

- In one or two sentences, describe how this project changed the way you think about AI generated code.\
This project showed me that AI-generated code is helpful but not always correct. Developers still need to review the logic, test the code, and verify that the solution actually works.
