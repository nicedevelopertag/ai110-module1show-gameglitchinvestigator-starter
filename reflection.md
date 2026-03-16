# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
    1. The game was in a fresh, state--no drop downs expanded, on top of that difficult was set to Normal (range 1 to 100). With 7 attempts left. Show hint was also checked.
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").
    1. Easy had a number range between 1-20, Normal and hard were swapped (100 and 50 respectively). This would be confusing to the users from a UX design perspective, as such fixes will be needed to ensure proper compliance.

    2. New game was not working as intended. When game is in fresh state, there is an "off-by-one" error present:
      a. "Guess a number between 1 and 100. Attempts left: 7"
      b. "Attempts allowed: 8"
    this would be present before any attempts at guessing were actually made.

    3. The hints provided after a guess were misleading. For instance, when the guess was too high, the hint said "Go HIGHER!" instead of "Go LOWER!", which confused the player and made winning impossible.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
  1. Copilot and Claude Code were utilized in the execution of this project.

- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
  1. Copilot suggested fixing the check_guess function by correcting the hint messages, where "Too High" should display "Go LOWER!" instead of "Go HIGHER!". I verified this by running the game, making guesses, and observing that the hints now correctly guided me towards the secret number, allowing me to win the game.

- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).
  1. Claude Code initially suggested initializing attempts to 0 instead of 1, but this caused the attempts left to show 8 instead of 7 at the start, which didn't match the intended behavior. I verified by testing the game and seeing the discrepancy, then adjusted it back to 1 to maintain the correct display.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
  1. I decided a bug was fixed by manually playing the game to ensure the behavior matched expectations, such as being able to win, hints being accurate, and the secret number remaining consistent. Additionally, I checked the developer debug info to verify internal state like attempts and score were updating correctly.
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
  1. I ran pytest on the test_game_logic.py file, which executed tests for the check_guess function. The tests passed, confirming that the function correctly identified winning guesses, too high, and too low outcomes, demonstrating that the logic was sound and the hints were now accurate.
- Did AI help you design or understand any tests? How?
  1. AI assisted by suggesting the structure for the test cases in test_game_logic.py, providing examples of how to assert outcomes for different guess scenarios. This helped me understand how to write focused unit tests for the game logic functions.

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
  1. Streamlit reruns are like refreshing the entire app script every time a user interacts with it, such as clicking a button or changing a slider, which allows the app to update dynamically based on new inputs. Session state acts as a persistent storage mechanism that keeps variables like the secret number or score across these reruns, ensuring that data doesn't reset unintentionally and maintaining the app's continuity during the user's session.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
  1. The habit of running automated tests with pytest after each fix to validate changes, as it provided quick feedback on whether the logic was correct and helped catch regressions early.
- What is one thing you would do differently next time you work with AI on a coding task?
  1. I would provide more detailed prompts to AI tools, specifying exact requirements and edge cases upfront, to reduce the need for iterative corrections and ensure the generated code aligns more closely with expectations from the start.
- In one or two sentences, describe how this project changed the way you think about AI generated code.
  1. This project demonstrated that AI-generated code, while a useful starting point, often contains subtle bugs and requires thorough manual review and testing. It shifted my perspective to view AI as a collaborative tool rather than a definitive solution, emphasizing the importance of human oversight in debugging and refining automated outputs.
