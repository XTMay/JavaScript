# Homework Assignment: Word Guessing Game Debug Challenge

## 🎯 Learning Objectives
By completing this assignment, you will:
- Practice JavaScript debugging techniques
- Strengthen understanding of arrays, functions, and loops
- Learn to read and interpret console error messages
- Develop systematic problem-solving skills
- Gain experience with DOM manipulation and event handling

## 📋 Assignment Overview
You have been given a **Word Guessing Game** with **5 intentional bugs**. Your task is to find and fix all bugs to make the game work correctly.

## 🚀 Getting Started

### Setup Instructions
1. Open `word_guessing_debug.html` in your web browser
2. Open Developer Tools (F12 or right-click → Inspect)
3. Navigate to the **Console** tab to see error messages
4. Try playing the game to identify what's not working

### How the Game Should Work
- Players guess letters to reveal a hidden word
- Each word comes with a helpful hint
- Players have 6 attempts before losing
- Players can guess individual letters or the whole word
- Game tracks progress through multiple words
- Players can skip words or restart the game

## 🐛 Bugs to Find and Fix

### Bug 1: Function Name Mismatch
- **Symptom**: Game doesn't start when page loads
- **Location**: Check the `window.onload` function call
- **Debugging Tip**: Look for "function is not defined" error in console

### Bug 2: Array Index Error
- **Symptom**: Game crashes when loading new words
- **Location**: `loadNewWord()` function
- **Debugging Tip**: Check how array elements are being accessed

### Bug 3: Variable Reference Error
- **Symptom**: Letter guessing doesn't work properly
- **Location**: `guessLetter()` function
- **Debugging Tip**: Look for "variable is not defined" error

### Bug 4: Logic Error in Win Condition
- **Symptom**: Game declares victory when it shouldn't
- **Location**: `checkGameState()` function
- **Debugging Tip**: Think about what condition indicates a completed word

### Bug 5: Missing Return Statement
- **Symptom**: Unexpected console messages when restarting
- **Location**: `restartGame()` function
- **Debugging Tip**: Check what happens after calling another function

## 🛠️ Debugging Techniques to Practice

### 1. Console Error Reading
```javascript
// Check the Console tab for error messages like:
// "ReferenceError: functionName is not defined"
// "TypeError: Cannot read property 'word' of undefined"
```
### 2. Console Logging
```javascript
// Add console.log statements to track values:
console.log('Current word index:', currentWordIndex);
console.log('Word data:', wordData);
console.log('Letter found:', letterFound);
```

### 3. Breakpoint Debugging
- Set breakpoints in Developer Tools → Sources tab
- Step through code execution line by line
- Inspect variable values at each step
### 4. Systematic Testing
- Test each function individually
- Try edge cases (empty input, repeated letters)
- Verify each game feature works as expected
## ✅ Testing Your Fixes
After fixing each bug, test the following:

1. Game Initialization : Page loads without console errors
2. Letter Guessing : Can guess letters and see them revealed
3. Word Loading : Can progress through multiple words
4. Win Detection : Game correctly identifies when word is complete
5. Game Restart : Restart function works without side effects
## 📝 Submission Requirements
### What to Submit
1. Fixed HTML file : word_guessing_debug_fixed.html
2. Bug Report : Document each bug you found and how you fixed it
3. Testing Notes : Describe how you tested your fixes
### Bug Report Format
For each bug:

```
Bug #: [Bug Number]
Location: [Function name and line]
Problem: [What was wrong]
Solution: [How you fixed it]
Testing: [How you verified the fix]
```
## 🌟 Extension Challenges (Optional)
Once you've fixed all bugs, try these enhancements:

1. Add More Words : Expand the word bank with 10 new words
2. Difficulty Levels : Implement easy/medium/hard word categories
3. Score System : Add points based on remaining attempts
4. Hint System : Allow players to reveal one letter as a hint
5. Animation Effects : Add visual feedback for correct/incorrect guesses
## 🎓 Learning Outcomes
After completing this assignment, you should be able to:

- Identify and fix common JavaScript errors
- Use browser developer tools effectively
- Debug array and function-related issues
- Apply systematic problem-solving approaches
- Understand the importance of careful variable naming
- Recognize logical errors in conditional statements
## 💡 Tips for Success
1. Read Error Messages Carefully : They often tell you exactly what's wrong
2. Use Console.log Liberally : Track variable values throughout execution
3. Test One Fix at a Time : Don't try to fix everything at once
4. Check Your Spelling : Many bugs are simple typos
5. Think About Logic : Does the condition check what you think it checks?
## 📚 Related Concepts
This assignment reinforces:

- Arrays : Storing and accessing data collections
- Functions : Organizing code into reusable blocks
- Loops : Iterating through data structures
- Conditionals : Making decisions in code
- DOM Manipulation : Updating webpage content
- Event Handling : Responding to user interactions
- Debugging : Systematic problem identification and resolution
Good luck with your debugging adventure! 🚀


```markdown:%2FUsers%2Fxiaotingzhou%2FDocuments%2FLectures%2FJavascript%2FJavaScript%2Fhomework_word_guessing_debug%2FREADME.md
# Word Guessing Game - Homework Debug Challenge

## 📖 Overview
This is a homework assignment featuring a **Word Guessing Game** with intentional bugs for debugging practice. Students will apply JavaScript fundamentals while learning essential debugging skills.

## 🎯 Learning Focus
- **Arrays**: Word storage and manipulation
- **Functions**: Game logic organization
- **Loops**: Character iteration and display
- **Debugging**: Systematic error identification and resolution
- **DOM Manipulation**: Dynamic content updates
- **Event Handling**: User interaction management

## 📁 Files Included
- `word_guessing_debug.html` - Main game file with 5 intentional bugs
- `assignment.md` - Detailed assignment instructions and debugging guide
- `README.md` - This overview file

## 🐛 Intentional Bugs
1. **Function Name Mismatch**: Called function doesn't match defined name
2. **Array Index Error**: Incorrect array element access
3. **Variable Reference Error**: Using undefined variable name
4. **Logic Error**: Incorrect win condition check
5. **Missing Return Statement**: Function continues executing unexpectedly

## 🚀 Quick Start
1. Open `word_guessing_debug.html` in a web browser
2. Open Developer Tools (F12)
3. Check Console tab for errors
4. Follow the assignment instructions in `assignment.md`

## 🎮 Game Features
- Interactive word guessing with hints
- Letter-by-letter or whole word guessing
- Attempt tracking and scoring
- Multiple words to progress through
- Visual feedback and game state management

## 🛠️ Debugging Skills Practiced
- Reading console error messages
- Using console.log() for value tracking
- Setting and using breakpoints
- Systematic function testing
- Logical condition analysis

## 📚 Educational Value
This assignment bridges the gap between learning JavaScript concepts and applying them in real debugging scenarios, preparing students for practical development challenges.