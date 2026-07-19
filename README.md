Create a clean and expandable Otome Game player name input screen using HTML, CSS, and JavaScript.

This project will eventually become a complete visual novel/otome game, so please keep the code modular, organized, and easy to expand.

## General Requirements

- Use HTML, CSS, and vanilla JavaScript only.
- Separate all files properly.
- Write clean, well-commented code.
- Design the layout for a 1920×1080 resolution.
- Make it responsive so it still looks good on smaller screens.

------------------------------------------------

## Name Input Screen

When the game launches, the first screen should ask the player to enter their name.

The layout should be centered both horizontally and vertically.

Display the following title above the input box:

"Please enter your name."

------------------------------------------------

## Custom PNG Input Box

IMPORTANT:

Do NOT use the browser's default input appearance.

I will create my own PNG input box.

Use the following image:

images/ui/name_box.png

The PNG is only the decorative frame.

Place a completely transparent HTML input element perfectly on top of the PNG image.

The player should feel like they are typing directly inside the PNG artwork.

Input settings:

- Background: transparent
- Border: none
- Outline: none
- Box shadow: none
- Text color: white
- Text alignment: center
- Font size: about 30px
- Placeholder: none
- Default value: empty
- Max length: 10 characters
- autocomplete="off"
- spellcheck="false"

The cursor should appear immediately when the player clicks anywhere inside the PNG frame.

------------------------------------------------

## Start Button

I will also create a custom PNG button.

Use:

images/ui/start_button.png

Display this button below the name box.

When clicked:

If the input is empty:

Display a small warning message below the input box:

"Please enter your name."

Do not switch pages.

If a name has been entered:

Save it into LocalStorage using:

playerName

Then redirect the player to:

story.html

------------------------------------------------

## JavaScript

Whenever story.html loads, create:

const playerName = localStorage.getItem("playerName");

This variable should be easy to use throughout the game.

Example:

Hello, ${playerName}

------------------------------------------------

## File Structure

index.html

story.html

css/
    style.css

js/
    script.js

images/
    background/
        무제413_20260718172638.png

    ui/
        name_box.png
        start_button.png

------------------------------------------------

## Future Expansion

Please organize the project so the following features can easily be added later:

- Dialogue system
- Character sprites
- Background switching
- Choice system
- Affection system
- Save / Load
- Auto mode
- Skip mode
- Settings menu
- Gallery
- CG Viewer
- Live2D characters
- Multiple routes
- Multiple endings

------------------------------------------------

## Important

The HTML input should be completely invisible.

Only the PNG frame should be visible.

The player should never notice that a standard HTML input element is being used.

The final result should feel like a professional Japanese Otome Game UI rather than a standard web form.
