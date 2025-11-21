# Quiz-statique

This is a small static quiz project demonstrating a simple JavaScript-driven quiz UI. It contains two versions of the app:

- `before/` — starter version (unimplemented or beginning state).
- `after/` — completed version with working quiz behavior.

How to use

- Open `after/index.html` in your browser to run the finished quiz.
- The page uses `after/styles.css` for styling and `after/script.js` for the interactive quiz logic.

Files overview

- `after/index.html` — HTML markup for the quiz. It contains:
  - A form with the id `quiz-form` that wraps the questions.
  - Question blocks with the class `question-item`.
  - Radio inputs for answers with the class `answer` and a `value` of either `"true"` or `"false"` to indicate the correct choice.
  - An element with id `alert` used to show a success message when all answers are correct.
- `after/styles.css` — styles for layout and the visual feedback classes (`correct`, `incorrect`, and the `active` state for the alert).
- `after/script.js` — quiz behavior (detailed below).
- `before/` — contains the initial or example version of the same files (useful for comparison or teaching).

What `after/script.js` does

1. It selects key DOM elements at the top:

   - `const form = document.getElementById("quiz-form")`
   - `const answers = Array.from(document.querySelectorAll(".answer"))`
   - `const questionItems = document.querySelectorAll(".question-item")`
   - `const alert = document.querySelector("#alert")`

2. The script listens for the form `submit` event and prevents the default submit behavior.

3. Before evaluating answers, it marks every question as incorrect by default (adds the `incorrect` class and removes `correct`). This ensures unanswered questions are treated as incorrect.

4. It gathers the checked answer inputs: `answers.filter(answer => answer.checked)` and iterates over them.

5. For each selected answer it checks `answer.value === "true"`:

   - If true: it marks the parent `.question-item` with class `correct` and removes `incorrect`.
   - If false: it marks the parent `.question-item` with class `incorrect` and removes `correct`.

6. After checking selected answers it computes two helper booleans:

   - `allTrue` — whether every selected answer has `value === "true"`.
   - `allAnswered` — whether the number of selected answers equals the number of questions.

7. If both `allTrue` and `allAnswered` are true, it shows the `#alert` element by adding the `active` class and hides it again after 1 second (`setTimeout`).

Notes and customization ideas

- To change which answer is correct, set the `value` attribute on the appropriate input to `"true"` in `after/index.html`.
- The UI depends on CSS classes `correct` and `incorrect` to visually indicate feedback — modify `after/styles.css` to change colors or transitions.
- The alert uses an `active` class to show/hide; you can extend it to show a score or more detailed feedback.
- The current logic treats unanswered questions as incorrect; if you prefer to force users to answer every question, add validation before evaluating.

If you want, I can:

- Add comments inside `after/index.html` showing which inputs should be `true`.
- Add a small score display in the page and update it on submit.
- Create a short automated test or demo script to verify behaviors.

Enjoy exploring the quiz!
