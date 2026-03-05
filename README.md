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

This exercise helps us see how AI-generated code can look like it works perfectly at first but still have bugs that make the program impossible to use as intended. At first, the game seems to run without errors. Once you start playing, it becomes misleading to win because the secret number changes every time the user presses submit, which means the player is never actually guessing the same number twice.

In Streamlit, the entire script reruns every time a button is clicked. If the secret number is defined normally at the top of the file, it gets regenerated on every rerun. This means the player’s guess is always being compared to a new number. I think this is where a lot of students could get stuck, especially if they have only written standard Python scripts before.

I think this is where a lot of students could get stuck because in a normal script, it feels logical to define a variable once and expect it to stay the same throughout execution. In Streamlit, the script reruns whenever the user interacts with the app. If the secret number is stored as a regular variable instead of being placed in st.session_state, it will reset on every rerun, which causes the game to be deceiving.

The game separates steps into parse_guess, check_guess and update_score. Understanding how the attempt number affects scoring or how the comparison result determines point changes requires slowing down and manually walking through a few test cases. I could see students changing the scoring formula before fully confirming whether the comparison logic is actually correct.

From a TF perspective, I would not immediately tell them the fix. I would ask questions like

- Where is the secret number being created?
- Can you print it and watch what happens after each submit?

Letting them observe the number change makes the concept of session states much more clear. I also think students could get stuck during setup. Running streamlit run app.py in the wrong directory or not installing requirements properly can block them before they even start debugging. In those cases, AI can be helpful if they ask specific questions and get unstuck faster.

I found that this activity reinforces that just because code runs does not mean it works correctly. The most important skill here is testing assumptions against actual behavior. As a TF, I would focus less on giving them the answer and more on guiding them to notice patterns and test those ideas to build confidence with debugging instead of relying entirely on AI explanations.

## 📸 Demo

- [ ] [Insert a screenshot of your fixed, winning game here]
![image alt](https://github.com/PrincessCodePath/ai110-module1show-gameglitchinvestigator-starter/blob/847f402151877afc7f1a4ebb49a10b84adc0649b/WinningGame.png)

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, insert a screenshot of your Enhanced Game UI here]
