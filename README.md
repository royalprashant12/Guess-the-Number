# Guess-the-Number Game

This is a simple Guess-the-Number game implemented in JavaScript, HTML, and CSS. The goal of the game is to guess a random number between 1 and 100 within 10 attempts.

## How to Play
1. Enter your guess in the input field and click the "Submit" button.
2. The game will let you know if your guess is too high or too low.
3. You have a total of 10 attempts to guess the correct number.
4. If you guess correctly, the game ends with a congratulatory message.
5. If you fail to guess within 10 attempts, the game reveals the correct number, and you can start a new game.

## Features
- **Input Validation:** Ensures that the entered guess is a valid number between 1 and 100.
- **Feedback Messages:** Displays hints whether the guess is too low or too high.
- **Game Over Handling:** Ends the game when the correct number is guessed or the player runs out of attempts.
- **Restart Option:** Provides a button to start a new game after the game ends.

## Game Logic

```javascript
//Player Makes a Guess
submit.addEventListener('click', function (e) {
  e.preventDefault();
  const guess = parseInt(userInput.value);
  validateGuess(guess);
});
```
## Player Makes a Guess
Capture the player's guess when the submit button is clicked.

```javascript

submit.addEventListener('click', function (e) {
  e.preventDefault();
  const guess = parseInt(userInput.value);
  validateGuess(guess);
});
```
## Validate the Guess
Check if the input is a valid number between 1 and 100. If not, show an alert message.

```javascript

function validateGuess(guess) {
  if (isNaN(guess) || guess < 1 || guess > 100) {
    alert('Please enter a valid number between 1 and 100');
  } else {
    checkGuess(guess);
  }
}
```
## Check the Guess
Compare the player's guess to the random number.

If the guess is correct, display a winning message and end the game.
If the guess is too high or too low, display a hint message and allow another guess.
```javascript

function checkGuess(guess) {
  if (guess === randomNumber) {
    displayMessage('You guessed it right!');
    endGame();
  } else if (guess < randomNumber) {
    displayMessage('Number is TOO low');
  } else {
    displayMessage('Number is TOO high');
  }
}
```
## Display Guess and Remaining Attempts
Show the player's guess and decrease the remaining attempts.

```javascript

function displayGuess(guess) {
  userInput.value = '';
  guessSlot.innerHTML += `${guess}, `;
  numGuess++;
  remaining.innerHTML = `${11 - numGuess}`;
}
```
## End the Game
When the player guesses correctly or runs out of attempts, disable input and offer a new game option.

```javascript

function endGame() {
  userInput.value = '';
  userInput.setAttribute('disabled', '');
  const p = document.createElement('p');
  p.classList.add('button');
  p.innerHTML = `<h2 id="newGame">Start New Game</h2>`;
  startOver.appendChild(p);
  playGame = false;
  newGame();
}
```
## Start a New Game
When the player chooses to start a new game, reset all variables and UI elements.

```javascript

function newGame() {
  const newGameButton = document.querySelector('#newGame');
  newGameButton.addEventListener('click', function (e) {
    randomNumber = parseInt(Math.random() * 100 + 1);
    prevGuess = [];
    numGuess = 1;
    guessSlot.innerHTML = '';
    remaining.innerHTML = '10';
    userInput.removeAttribute('disabled');
    startOver.removeChild(document.querySelector('#newGame').parentNode);
    playGame = true;
  });
}
```
![image](https://github.com/user-attachments/assets/abfa28c3-2292-43ab-abf6-9a9dc45aa25b)

