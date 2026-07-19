You are an expert HTML, CSS, and JavaScript developer.

Create a simple browser-based otome game that runs on GitHub Pages.

Use only:
- HTML
- CSS
- Vanilla JavaScript

Files:
- index.html
- style.css
- script.js
- assets/

Requirements:

1. Title Screen
- Display the game title.
- A "Start" button.
- Clicking Start opens the name input screen.

2. Name Input Screen
- Display the text:
  "Please enter your name."
- The input field should be empty by default.
- A Confirm button.
- Save the player's name.
- Replace every "[Player]" in dialogue with the entered name.

3. Prologue
- Display a background image.
- Display a dialogue box at the bottom.
- Display a character name box above the dialogue box.
- Show dialogue with a typewriter animation.
- Clicking anywhere advances the dialogue.
- Fade transition between scenes.

4. UI
- Resolution designed for 1920×1080.
- Modern otome game style.
- Elegant fantasy-themed interface.
- Large readable text.
- Smooth button hover animations.

5. Story Data

Use a JavaScript array like this:

const story = [
{
    background: "assets/backgrounds/무제413_20260718172638.png",
    character: "",
    name: "",
    text: "..."
},
{
    background: "assets/backgrounds/무제413_20260718172638.png",
    character: "",
    name: "",
    text: "..."
}
];

6. Code
- Keep the code clean.
- Add comments.
- Use reusable functions.
- Do not use any external libraries.
