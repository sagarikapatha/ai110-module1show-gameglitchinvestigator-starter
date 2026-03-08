# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").
  
When I first ran the game, the Streamlit page opened and showed the title “Game Glitch Investigator” with a box to enter guesses, difficulty settings, and the score, etc. The interface looked simple, so I started playing couple of rounds with different inputs and difficulty level. While playing it, I noticed some problems with the game behavior.They are:
Bug1: The hints were incorrect, because when my guess was higher than the secret number the game told me to go higher instead of telling me to go lower. 
Bug2: Changing the difficulty level did not seem to fully affect the game, since the guessing range shown on the screen still looked the same. 
Bug3: While clicking on “New Game,” the game did not restart but the secret number was changing(everytime I click new game), and some information from the previous round seemed to remain.
Bug4: The range of the difficulty levels are incorrect
Bug5: Negative scoring
---
## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
