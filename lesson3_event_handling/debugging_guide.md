# 🎨 Lesson 3: Event Handling Debugging Guide

## Learning Objectives
By the end of this lesson, students will be able to:
- Understand different types of event listeners and their proper usage
- Debug mouse and keyboard event handling issues
- Fix event object property access errors
- Handle canvas-based interactions and coordinate calculations
- Implement proper event delegation and state management

## Project Setup
1. Open `drawing_app_debug.html` in your web browser
2. Open Developer Tools (F12 or right-click → Inspect)
3. Go to the Console tab to see error messages
4. Try interacting with the drawing app (mouse clicks, keyboard shortcuts)
5. Watch the Event Logger to see what events are being captured

## 🐛 Bugs to Find and Fix

### Bug 1: Mouse Events Not Working Properly
**Problem**: Drawing doesn't work correctly on the canvas
**Location**: `initializeCanvas()` function and event listener setup
**Learning Focus**: Proper event listener attachment and event types
**Symptoms**: 
- Drawing might not start/stop correctly
- Events might fire on wrong elements
- Mouse leaving canvas doesn't stop drawing

**Debugging Steps:**
1. Check which elements have event listeners attached
2. Verify event listener names are correct
3. Ensure all necessary mouse events are handled

### Bug 2: Keyboard Shortcuts Not Responding
**Problem**: Pressing keyboard shortcuts doesn't change tools
**Location**: `initializeKeyboardEvents()` and `handleKeyboard()` functions
**Learning Focus**: Keyboard event types and key property access
**Symptoms**:
- Key presses don't trigger tool changes
- Wrong key codes being detected
- Ctrl+Z undo not working

**Debugging Steps:**
1. Check if keyboard event listener is attached
2. Verify correct event type (keydown vs keypress)
3. Check key detection method (e.key vs e.keyCode)

### Bug 3: Tool Selection Visual Updates
**Problem**: Clicking tool buttons doesn't show which tool is active
**Location**: `selectTool()` function
**Learning Focus**: CSS class manipulation and element selection
**Symptoms**:
- Active tool button doesn't highlight
- Previous tool button stays highlighted
- Wrong button gets highlighted

**Debugging Steps:**
1. Check CSS class removal from previous buttons
2. Verify element ID construction
3. Ensure correct button gets the active class

### Bug 4: Drawing Continues Outside Canvas
**Problem**: Drawing doesn't stop when mouse leaves canvas area
**Location**: Canvas event listener setup
**Learning Focus**: Mouse event handling and boundaries
**Symptoms**:
- Drawing continues when mouse moves outside canvas
- isDrawing state not properly managed

**Debugging Steps:**
1. Check if mouseout/mouseleave events are handled
2. Verify drawing state management
3. Test mouse behavior at canvas boundaries

### Bug 5: Event Logger Shows Undefined Values
**Problem**: Event log displays 'undefined' instead of actual values
**Location**: `draw()` function and `logEvent()` calls
**Learning Focus**: Variable scope and proper variable references
**Symptoms**:
- Event log shows "Position: (undefined, undefined)"
- Wrong variable names being used

**Debugging Steps:**
1. Check variable names in logEvent calls
2. Verify variable scope and availability
3. Ensure correct event object properties are accessed

## 🔧 Event Handling Concepts Covered

### Mouse Events
```javascript
// Basic mouse events
element.addEventListener('mousedown', function(e) {
    // Mouse button pressed
});

element.addEventListener('mousemove', function(e) {
    // Mouse moved
});

element.addEventListener('mouseup', function(e) {
    // Mouse button released
});

element.addEventListener('mouseout', function(e) {
    // Mouse left element
});
```
Trae

I need to create a small project for Lesson 2 on DOM Manipulation Basics, similar to the calculator debug project. This should include selectors, interactive elements, and a color picker with intentional bugs for debugging practice.

lesson1_calculator_debug/calculator_debug.html :( 1 - 50 )

Let me see the rest of the calculator file to understand the structure better, then I'll create a similar DOM manipulation project with color picker functionality.

lesson1_calculator_debug/calculator_debug.html :( 200 - 416 )

Now I'll create a DOM manipulation project for Lesson 2 with selectors, interactive elements, and a color picker. I'll include intentional bugs similar to the calculator project for debugging practice.

. :( 1 - 1 )

I need to create a new directory for lesson 2 and then create the DOM manipulation project files.

JavaScript

I'll create a DOM manipulation project for Lesson 2 that includes selectors, interactive elements, and a color picker with intentional bugs for debugging practice. Let me create the project files:

```
mkdir lesson2_dom_manipulation
```
Now I'll create the main project file:

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" 
  content="width=device-width, 
  initial-scale=1.0">
  <title>Interactive Color Picker 
  - DOM Debug Challenge</title>
  <style>
    /* Modern, clean styling */
    body {
      font-family: 'Arial', 
      sans-serif;
      margin: 0;
      padding: 20px;
      background: linear-gradient
      (135deg, #74b9ff 0%, #0984e3 
      100%);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    
    .container {
      background: white;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 10px 30px rgba
      (0, 0, 0, 0.2);
      max-width: 600px;
      width: 100%;
    }
    
    h1 {
      text-align: center;
      color: #333;
      margin-bottom: 20px;
      font-size: 28px;
    }
    
    .debug-info {
      background: #fff3cd;
      border: 1px solid #ffeaa7;
      padding: 15px;
      border-radius: 8px;
      margin-bottom: 20px;
      font-size: 14px;
      color: #856404;
    }
    
    .color-picker-section {
      background: #f8f9fa;
      padding: 20px;
      border-radius: 10px;
      margin-bottom: 20px;
    }
    
    .controls {
      display: grid;
      grid-template-columns: 1fr 
      1fr;
      gap: 20px;
      margin-bottom: 20px;
    }
    
    .control-group {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    
    label {
      font-weight: bold;
      color: #333;
    }
    
    input[type="range"] {
      width: 100%;
      height: 8px;
      border-radius: 4px;
      outline: none;
      cursor: pointer;
    }
    
    input[type="color"] {
      width: 100%;
      height: 50px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }
    
    .color-display {
      width: 100%;
      height: 100px;
      border: 3px solid #333;
      border-radius: 10px;
      margin: 20px 0;
      transition: all 0.3s ease;
    }
    
    .color-info {
      display: grid;
      grid-template-columns: repeat
      (3, 1fr);
      gap: 15px;
      margin: 20px 0;
    }
    
    .info-box {
      background: #e9ecef;
      padding: 15px;
      border-radius: 8px;
      text-align: center;
    }
    
    .info-box h4 {
      margin: 0 0 10px 0;
      color: #495057;
    }
    
    .info-box span {
      font-size: 18px;
      font-weight: bold;
      color: #007bff;
    }
    
    .element-selector {
      margin: 20px 0;
    }
    
    .target-elements {
      display: flex;
      gap: 15px;
      margin: 15px 0;
    }
    
    .target-element {
      width: 80px;
      height: 80px;
      border: 2px solid #333;
      border-radius: 8px;
      cursor: pointer;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: bold;
      color: white;
      text-shadow: 1px 1px 2px rgba
      (0,0,0,0.5);
    }
    
    .target-element:hover {
      transform: scale(1.1);
      box-shadow: 0 5px 15px rgba
      (0,0,0,0.3);
    }
    
    .buttons {
      display: flex;
      gap: 10px;
      margin: 20px 0;
      flex-wrap: wrap;
    }
    
    button {
      padding: 12px 20px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-weight: bold;
      transition: all 0.2s;
      font-size: 14px;
    }
    
    .btn-primary {
      background: #007bff;
      color: white;
    }
    
    .btn-primary:hover {
      background: #0056b3;
    }
    
    .btn-secondary {
      background: #6c757d;
      color: white;
    }
    
    .btn-secondary:hover {
      background: #545b62;
    }
    
    .btn-success {
      background: #28a745;
      color: white;
    }
    
    .btn-success:hover {
      background: #1e7e34;
    }
    
    .debug-section {
      margin-top: 20px;
      padding: 15px;
      background: #f8f9fa;
      border-radius: 8px;
      border-left: 4px solid 
      #007bff;
    }
    
    .debug-section h3 {
      margin-top: 0;
      color: #007bff;
    }
    
    .bug-list {
      list-style-type: none;
      padding: 0;
    }
    
    .bug-list li {
      padding: 8px 0;
      border-bottom: 1px solid 
      #dee2e6;
    }
    
    .bug-list li:last-child {
      border-bottom: none;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>🎨 Interactive Color 
    Picker - DOM Debug Challenge</
    h1>
    
    <div class="debug-info">
      <strong>🐛 Debugging 
      Mission:</strong> This color 
      picker has several DOM 
      manipulation bugs! Use 
      browser developer tools to 
      find and fix them.
    </div>
    
    <div 
    class="color-picker-section">
      <div class="controls">
        <div class="control-group">
          <label 
          for="redSlider">Red 
          (0-255):</label>
          <input type="range" 
          id="redSlider" min="0" 
          max="255" value="128" 
          oninput="updateColorFromS
          liders()">
          <span id="redValue">128</
          span>
        </div>
        
        <div class="control-group">
          <label 
          for="greenSlider">Green 
          (0-255):</label>
          <input type="range" 
          id="greenSlider" min="0" 
          max="255" value="128" 
          oninput="updateColorFromS
          liders()">
          <span 
          id="greenValue">128</
          span>
        </div>
        
        <div class="control-group">
          <label 
          for="blueSlider">Blue 
          (0-255):</label>
          <input type="range" 
          id="blueSlider" min="0" 
          max="255" value="128" 
          oninput="updateColorFromS
          liders()">
          <span 
          id="blueValue">128</span>
        </div>
        
        <div class="control-group">
          <label 
          for="colorInput">Direct 
          Color Picker:</label>
          <input type="color" 
          id="colorInput" 
          value="#808080" 
          onchange="updateColorFrom
          Picker()">
        </div>
      </div>
      
      <div class="color-display" 
      id="colorDisplay"></div>
      
      <div class="color-info">
        <div class="info-box">
          <h4>RGB</h4>
          <span id="rgbDisplay">rgb
          (128, 128, 128)</span>
        </div>
        <div class="info-box">
          <h4>HEX</h4>
          <span 
          id="hexDisplay">#808080</
          span>
        </div>
        <div class="info-box">
          <h4>HSL</h4>
          <span id="hslDisplay">hsl
          (0, 0%, 50%)</span>
        </div>
      </div>
    </div>
    
    <div class="element-selector">
      <h3>🎯 Select Elements to 
      Color:</h3>
      <div class="target-elements">
        <div 
        class="target-element" 
        id="box1" 
        onclick="selectElement
        ('box1')">Box 1</div>
        <div 
        class="target-element" 
        id="box2" 
        onclick="selectElement
        ('box2')">Box 2</div>
        <div 
        class="target-element" 
        id="box3" 
        onclick="selectElement
        ('box3')">Box 3</div>
        <div 
        class="target-element" 
        id="box4" 
        onclick="selectElement
        ('box4')">Box 4</div>
      </div>
      
      <div class="buttons">
        <button 
        class="btn-primary" 
        onclick="applyColorToSelect
        ed()">Apply Color to 
        Selected</button>
        <button 
        class="btn-secondary" 
        onclick="resetAllColors()
        ">Reset All Colors</button>
        <button 
        class="btn-success" 
        onclick="randomizeColors()
        ">Randomize All</button>
        <button 
        class="btn-primary" 
        onclick="copyColorCode()
        ">Copy HEX Code</button>
      </div>
    </div>
    
    <div class="debug-section">
      <h3>🔍 Bugs to Find & Fix:</
      h3>
      <ul class="bug-list">
        <li>🐛 <strong>Bug 1:</
        strong> Color sliders 
        don't update the display</
        li>
        <li>🐛 <strong>Bug 2:</
        strong> Element selection 
        doesn't work</li>
        <li>🐛 <strong>Bug 3:</
        strong> Color values show 
        'undefined'</li>
        <li>🐛 <strong>Bug 4:</
        strong> Reset button 
        doesn't clear selections</
        li>
        <li>🐛 <strong>Bug 5:</
        strong> Copy function 
        throws an error</li>
      </ul>
    </div>
  </div>

  <script>
    // INTENTIONAL BUGS FOR DOM 
    MANIPULATION DEBUGGING
    
    // Global variables
    let currentColor = { r: 128, 
    g: 128, b: 128 };
    let selectedElement = null;
    
    // BUG 1: Function name 
    mismatch - called 
    'updateColorFromSliders' but 
    defined as 'updateColor'
    function updateColor() {
      const red = document.
      getElementById('redSlider').
      value;
      const green = document.
      getElementById
      ('greenSlider').value;
      const blue = document.
      getElementById('blueSlider').
      value;
      
      currentColor = { r: red, g: 
      green, b: blue };
      
      // Update slider value 
      displays
      document.getElementById
      ('redValue').textContent = 
      red;
      document.getElementById
      ('greenValue').textContent = 
      green;
      document.getElementById
      ('blueValue').textContent = 
      blue;
      
      updateColorDisplay();
      console.log('Color 
      updated:', currentColor);
    }
    
    function updateColorFromPicker
    () {
      const colorInput = document.
      getElementById('colorInput');
      const hex = colorInput.value;
      
      // Convert hex to RGB
      const r = parseInt(hex.substr
      (1, 2), 16);
      const g = parseInt(hex.substr
      (3, 2), 16);
      const b = parseInt(hex.substr
      (5, 2), 16);
      
      currentColor = { r, g, b };
      
      // Update sliders
      document.getElementById
      ('redSlider').value = r;
      document.getElementById
      ('greenSlider').value = g;
      document.getElementById
      ('blueSlider').value = b;
      
      updateColor();
    }
    
    // BUG 3: Function uses wrong 
    variable names for color values
    function updateColorDisplay() {
      const colorDisplay = 
      document.getElementById
      ('colorDisplay');
      
      // BUG 3: Using undefined 
      variables instead of 
      currentColor properties
      const rgb = `rgb(${red}, $
      {green}, ${blue})`; // 
      Should be currentColor.r, 
      currentColor.g, currentColor.
      b
      const hex = rgbToHex
      (currentColor.r, 
      currentColor.g, currentColor.
      b);
      const hsl = rgbToHsl
      (currentColor.r, 
      currentColor.g, currentColor.
      b);
      
      colorDisplay.style.
      backgroundColor = rgb;
      
      // Update info displays
      document.getElementById
      ('rgbDisplay').textContent = 
      rgb;
      document.getElementById
      ('hexDisplay').textContent = 
      hex;
      document.getElementById
      ('hslDisplay').textContent = 
      hsl;
      
      console.log('Display 
      updated:', { rgb, hex, 
      hsl });
    }
    
    // BUG 2: Function uses wrong 
    selector method
    function selectElement
    (elementId) {
      // Remove previous selection
      if (selectedElement) {
        selectedElement.style.
        border = '2px solid #333';
      }
      
      // BUG 2: Using 
      getElementsByClassName 
      instead of getElementById
      selectedElement = document.
      getElementsByClassName
      (elementId)[0]; // Should be 
      getElementById
      
      if (selectedElement) {
        selectedElement.style.
        border = '3px solid 
        #ff6b6b';
        console.log('Selected 
        element:', elementId);
      } else {
        console.log('Element not 
        found:', elementId);
      }
    }
    
    function applyColorToSelected
    () {
      if (!selectedElement) {
        alert('Please select an 
        element first!');
        return;
      }
      
      const rgb = `rgb($
      {currentColor.r}, $
      {currentColor.g}, $
      {currentColor.b})`;
      selectedElement.style.
      backgroundColor = rgb;
      
      console.log('Applied color 
      to selected element:', rgb);
    }
    
    // BUG 4: Reset function 
    doesn't clear selected element 
    properly
    function resetAllColors() {
      // Reset all target elements
      const elements = document.
      querySelectorAll('.
      target-element');
      elements.forEach(element => {
        element.style.
        backgroundColor = 
        '#6c757d';
        element.style.border = 
        '2px solid #333';
      });
      
      // BUG 4: Not clearing the 
      selectedElement variable
      // selectedElement = 
      null; // This line is missing
      
      console.log('All colors 
      reset');
    }
    
    function randomizeColors() {
      const elements = document.
      querySelectorAll('.
      target-element');
      elements.forEach(element => {
        const r = Math.floor(Math.
        random() * 256);
        const g = Math.floor(Math.
        random() * 256);
        const b = Math.floor(Math.
        random() * 256);
        element.style.
        backgroundColor = `rgb($
        {r}, ${g}, ${b})`;
      });
      
      console.log('Colors 
      randomized');
    }
    
    // BUG 5: Copy function has 
    wrong method name
    function copyColorCode() {
      const hex = document.
      getElementById('hexDisplay').
      textContent;
      
      // BUG 5: Using writeText 
      instead of writeText method
      navigator.clipboard.
      writeToClipboard(hex).then
      (() => { // Should be 
      writeText
        alert('Color code copied 
        to clipboard!');
      }).catch(err => {
        console.error('Failed to 
        copy:', err);
        // Fallback for older 
        browsers
        const textArea = document.
        createElement('textarea');
        textArea.value = hex;
        document.body.appendChild
        (textArea);
        textArea.select();
        document.execCommand
        ('copy');
        document.body.removeChild
        (textArea);
        alert('Color code copied 
        to clipboard!');
      });
    }
    
    // Helper functions
    function rgbToHex(r, g, b) {
      return "#" + ((1 << 24) + 
      (parseInt(r) << 16) + 
      (parseInt(g) << 8) + parseInt
      (b)).toString(16).slice(1);
    }
    
    function rgbToHsl(r, g, b) {
      r /= 255;
      g /= 255;
      b /= 255;
      
      const max = Math.max(r, g, 
      b);
      const min = Math.min(r, g, 
      b);
      let h, s, l = (max + min) / 
      2;
      
      if (max === min) {
        h = s = 0;
      } else {
        const d = max - min;
        s = l > 0.5 ? d / (2 - max 
        - min) : d / (max + min);
        
        switch (max) {
          case r: h = (g - b) / d 
          + (g < b ? 6 : 0); break;
          case g: h = (b - r) / d 
          + 2; break;
          case b: h = (r - g) / d 
          + 4; break;
        }
        h /= 6;
      }
      
      return `hsl(${Math.round(h * 
      360)}, ${Math.round(s * 100)}
      %, ${Math.round(l * 100)}%)`;
    }
    
    // Initialize the color picker
    window.onload = function() {
      updateColorDisplay();
      console.log('Color picker 
      loaded - Ready for 
      debugging!');
      console.log('Open Developer 
      Tools (F12) to see debug 
      messages');
      console.log('Try interacting 
      with the color picker and 
      watch for errors');
    };
    
    /*
    🎯 DEBUGGING EXERCISES FOR 
    STUDENTS:
    
    1. **DOM Selection**: Practice 
    using getElementById, 
    querySelector, etc.
    2. **Event Handling**: Fix 
    function name mismatches in 
    event handlers
    3. **Variable Scope**: 
    Understand global vs local 
    variable access
    4. **Element Styling**: Learn 
    to manipulate CSS properties 
    via JavaScript
    5. **Error Handling**: Fix 
    undefined variable references
    6. **API Usage**: Correct 
    clipboard API method names
    
    🔧 DOM MANIPULATION TECHNIQUES 
    TO PRACTICE:
    - document.getElementById() vs 
    document.querySelector()
    - element.style.property 
    manipulation
    - element.textContent vs 
    element.innerHTML
    - Event handling with onclick 
    and addEventListener
    - CSS class manipulation with 
    classList
    - Form input value handling
    - Error debugging with console.
    log()
    */
  </script>
</body>
</html>
```
Now I'll create a debugging guide for this lesson:

```
# 🎨 Lesson 2: DOM Manipulation 
Debugging Guide

## Learning Objectives
By the end of this lesson, 
students will be able to:
- Use browser developer tools to 
debug DOM manipulation issues
- Understand different DOM 
selection methods
- Fix common JavaScript errors 
related to element selection and 
styling
- Practice event handling and form 
input manipulation
- Debug variable scope and 
reference errors

## Project Setup
1. Open `color_picker_debug.html` 
in your web browser
2. Open Developer Tools (F12 or 
right-click → Inspect)
3. Go to the Console tab to see 
error messages
4. Try interacting with the color 
picker elements

## 🐛 Bugs to Find and Fix

### Bug 1: Function Name Mismatch
**Problem**: Color sliders don't 
update the display when moved
**Location**: HTML onclick 
handlers vs JavaScript function 
names
**Learning Focus**: Event handler 
function naming
**Hint**: Check if the function 
called in HTML matches the 
function defined in JavaScript

### Bug 2: Wrong DOM Selection 
Method
**Problem**: Clicking on colored 
boxes doesn't select them
**Location**: `selectElement()` 
function
**Learning Focus**: `getElementById
()` vs `getElementsByClassName()`
**Hint**: Look at how elements are 
being selected and what method 
should be used

### Bug 3: Undefined Variable 
References
**Problem**: Color values show 
'undefined' in the display
**Location**: `updateColorDisplay()
` function
**Learning Focus**: Variable scope 
and object property access
**Hint**: Check if variables are 
properly defined and accessible

### Bug 4: Incomplete Reset 
Function
**Problem**: Reset button doesn't 
clear element selections properly
**Location**: `resetAllColors()` 
function
**Learning Focus**: State 
management and variable cleanup
**Hint**: What variables need to 
be reset when clearing selections?

### Bug 5: Wrong API Method Name
**Problem**: Copy color code 
button throws an error
**Location**: `copyColorCode()` 
function
**Learning Focus**: Web API method 
names
**Hint**: Check the correct method 
name for the Clipboard API

## 🔧 Debugging Techniques to 
Practice

### 1. Console Debugging
```javascript
// Add console.log statements to 
track values
console.log('Current color:', 
currentColor);
console.log('Selected element:', 
selectedElement);
```
### 2. DOM Inspection
- Right-click on elements and select "Inspect"
- Check if elements have the expected IDs and classes
- Verify CSS styles are being applied
### 3. Event Debugging
- Check if event handlers are properly attached
- Verify function names match between HTML and JavaScript
- Test events by adding console.log in event handlers
### 4. Variable Tracking
- Use the Console tab to check variable values
- Type variable names in console to see their current values
- Use typeof to check variable types
### 5. Breakpoint Debugging
- Set breakpoints in the Sources tab
- Step through code execution line by line
- Watch variable values change during execution
## 🎯 DOM Manipulation Concepts Covered
### Element Selection
- document.getElementById(id) - Select by ID
- document.querySelector(selector) - Select first matching element
- document.querySelectorAll(selector) - Select all matching elements
- document.getElementsByClassName(className) - Select by class name
### Element Styling
- element.style.property = value - Direct style manipulation
- element.style.backgroundColor - Background color
- element.style.border - Border styling
### Form Input Handling
- input.value - Get/set input values
- input.onchange - Handle input changes
- input.oninput - Handle real-time input
### Event Handling
- onclick attribute in HTML
- addEventListener() method
- Event handler function parameters
## 🚀 Extension Challenges
Once you've fixed all the bugs, try these additional challenges:

1. Add Color History : Store the last 5 colors used
2. Keyboard Shortcuts : Add keyboard controls for color adjustment
3. Color Palette : Create preset color buttons
4. Gradient Generator : Create gradients between two colors
5. Color Accessibility : Add contrast ratio calculations
## 💡 Tips for Success
1. Read Error Messages : The console will tell you exactly what's wrong
2. Check Spelling : Many bugs are simple typos in function or variable names
3. Use Console.log : Add logging to understand what's happening
4. Test Incrementally : Fix one bug at a time and test
5. Inspect Elements : Use the Elements tab to verify DOM structure
## 🎓 Learning Outcomes
After completing this debugging exercise, you should understand:

- How to select and manipulate DOM elements
- Common JavaScript errors and how to fix them
- Browser developer tools for debugging
- Event handling in JavaScript
- CSS styling through JavaScript
- Variable scope and object property access
Remember: Debugging is a crucial skill for any developer. Take your time, read error messages carefully, and use the browser's developer tools to your advantage!

```

This DOM manipulation project 
includes:

1. **Interactive Color Picker** 
with RGB sliders and direct color 
input
2. **Element Selection** - 
clickable boxes that can be colored
3. **Multiple DOM Selectors** - 
demonstrating different selection 
methods
4. **Event Handling** - various 
button interactions
5. **CSS Manipulation** - changing 
styles through JavaScript
6. **Form Input Handling** - 
sliders and color inputs

**Intentional Bugs for Debugging 
Practice:**
- Function name mismatches 
(similar to calculator project)
- Wrong DOM selection methods
- Undefined variable references
- Incomplete state management
- Incorrect API method names

The project teaches essential DOM 
manipulation concepts while 
providing hands-on debugging 
experience, perfect for Lesson 2 
of your JavaScript course!
```

May-Xiaoting-Zhou

Copy

Delete

similar prepare | 3 | Event Handling | Event listeners, drawing app, user interactions |

Trae

Used 1 context

README.md 30-31

I'll create an Event Handling project for Lesson 3 that includes event listeners, a drawing app, and user interactions with intentional bugs for debugging practice.

```
mkdir lesson3_event_handling
```
Now I'll create the main project file:

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" 
  content="width=device-width, 
  initial-scale=1.0">
  <title>Interactive Drawing App - 
  Event Handling Debug Challenge</
  title>
  <style>
    /* Modern, clean styling */
    body {
      font-family: 'Arial', 
      sans-serif;
      margin: 0;
      padding: 20px;
      background: linear-gradient
      (135deg, #a8edea 0%, #fed6e3 
      100%);
      min-height: 100vh;
    }
    
    .container {
      max-width: 1000px;
      margin: 0 auto;
      background: white;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 10px 30px rgba
      (0, 0, 0, 0.2);
    }
    
    h1 {
      text-align: center;
      color: #333;
      margin-bottom: 20px;
      font-size: 28px;
    }
    
    .debug-info {
      background: #fff3cd;
      border: 1px solid #ffeaa7;
      padding: 15px;
      border-radius: 8px;
      margin-bottom: 20px;
      font-size: 14px;
      color: #856404;
    }
    
    .toolbar {
      display: flex;
      gap: 15px;
      margin-bottom: 20px;
      padding: 15px;
      background: #f8f9fa;
      border-radius: 10px;
      flex-wrap: wrap;
      align-items: center;
    }
    
    .tool-group {
      display: flex;
      align-items: center;
      gap: 10px;
    }
    
    .tool-group label {
      font-weight: bold;
      color: #333;
    }
    
    button {
      padding: 10px 15px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-weight: bold;
      transition: all 0.2s;
      font-size: 14px;
    }
    
    .btn-primary {
      background: #007bff;
      color: white;
    }
    
    .btn-primary:hover {
      background: #0056b3;
    }
    
    .btn-secondary {
      background: #6c757d;
      color: white;
    }
    
    .btn-secondary:hover {
      background: #545b62;
    }
    
    .btn-danger {
      background: #dc3545;
      color: white;
    }
    
    .btn-danger:hover {
      background: #c82333;
    }
    
    .btn-success {
      background: #28a745;
      color: white;
    }
    
    .btn-success:hover {
      background: #1e7e34;
    }
    
    input[type="range"] {
      width: 100px;
    }
    
    input[type="color"] {
      width: 50px;
      height: 35px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    
    .canvas-container {
      border: 3px solid #333;
      border-radius: 10px;
      margin: 20px 0;
      display: flex;
      justify-content: center;
      background: white;
    }
    
    #drawingCanvas {
      border-radius: 7px;
      cursor: crosshair;
    }
    
    .interaction-panel {
      display: grid;
      grid-template-columns: 1fr 
      1fr;
      gap: 20px;
      margin: 20px 0;
    }
    
    .event-logger {
      background: #f8f9fa;
      padding: 15px;
      border-radius: 8px;
      border: 1px solid #dee2e6;
    }
    
    .event-logger h3 {
      margin-top: 0;
      color: #495057;
    }
    
    #eventLog {
      height: 200px;
      overflow-y: auto;
      background: white;
      padding: 10px;
      border: 1px solid #ced4da;
      border-radius: 5px;
      font-family: monospace;
      font-size: 12px;
    }
    
    .keyboard-controls {
      background: #f8f9fa;
      padding: 15px;
      border-radius: 8px;
      border: 1px solid #dee2e6;
    }
    
    .keyboard-controls h3 {
      margin-top: 0;
      color: #495057;
    }
    
    .key-info {
      display: grid;
      grid-template-columns: 1fr 
      2fr;
      gap: 10px;
      font-size: 14px;
    }
    
    .key-info div {
      padding: 5px;
      background: white;
      border-radius: 3px;
      border: 1px solid #dee2e6;
    }
    
    .debug-section {
      margin-top: 20px;
      padding: 15px;
      background: #f8f9fa;
      border-radius: 8px;
      border-left: 4px solid 
      #007bff;
    }
    
    .debug-section h3 {
      margin-top: 0;
      color: #007bff;
    }
    
    .bug-list {
      list-style-type: none;
      padding: 0;
    }
    
    .bug-list li {
      padding: 8px 0;
      border-bottom: 1px solid 
      #dee2e6;
    }
    
    .bug-list li:last-child {
      border-bottom: none;
    }
    
    .active-tool {
      background: #28a745 
      !important;
      color: white !important;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>🎨 Interactive Drawing App 
    - Event Handling Debug 
    Challenge</h1>
    
    <div class="debug-info">
      <strong>🐛 Debugging 
      Mission:</strong> This 
      drawing app has several 
      event handling bugs! Use 
      browser developer tools to 
      find and fix them.
    </div>
    
    <div class="toolbar">
      <div class="tool-group">
        <label>Tools:</label>
        <button id="penTool" 
        class="btn-primary 
        active-tool" 
        onclick="selectTool('pen')
        ">✏️ Pen</button>
        <button id="eraserTool" 
        class="btn-secondary" 
        onclick="selectTool
        ('eraser')">🧽 Eraser</
        button>
        <button id="lineTool" 
        class="btn-secondary" 
        onclick="selectTool('line')
        ">📏 Line</button>
        <button id="circleTool" 
        class="btn-secondary" 
        onclick="selectTool
        ('circle')">⭕ Circle</
        button>
      </div>
      
      <div class="tool-group">
        <label 
        for="brushSize">Size:</
        label>
        <input type="range" 
        id="brushSize" min="1" 
        max="50" value="5" 
        oninput="updateBrushSize()
        ">
        <span 
        id="sizeDisplay">5px</span>
      </div>
      
      <div class="tool-group">
        <label 
        for="colorPicker">Color:</
        label>
        <input type="color" 
        id="colorPicker" 
        value="#000000" 
        onchange="updateColor()">
      </div>
      
      <div class="tool-group">
        <button class="btn-danger" 
        onclick="clearCanvas()
        ">🗑️ Clear</button>
        <button 
        class="btn-success" 
        onclick="saveDrawing()">💾 
        Save</button>
        <button 
        class="btn-secondary" 
        onclick="undoLastAction()
        ">↶ Undo</button>
      </div>
    </div>
    
    <div class="canvas-container">
      <canvas id="drawingCanvas" 
      width="800" height="400"></
      canvas>
    </div>
    
    <div class="interaction-panel">
      <div class="event-logger">
        <h3>📋 Event Logger</h3>
        <div id="eventLog"></div>
        <button 
        class="btn-secondary" 
        onclick="clearEventLog()
        ">Clear Log</button>
      </div>
      
      <div 
      class="keyboard-controls">
        <h3>⌨️ Keyboard Shortcuts</
        h3>
        <div class="key-info">
          <div><strong>P</strong></
          div><div>Pen Tool</div>
          <div><strong>E</strong></
          div><div>Eraser Tool</
          div>
          <div><strong>L</strong></
          div><div>Line Tool</div>
          <div><strong>C</strong></
          div><div>Circle Tool</
          div>
          <div><strong>Space</
          strong></div><div>Clear 
          Canvas</div>
          <div><strong>Ctrl+Z</
          strong></div><div>Undo</
          div>
        </div>
        <p><strong>Current Key:</
        strong> <span 
        id="currentKey">None</
        span></p>
      </div>
    </div>
    
    <div class="debug-section">
      <h3>🔍 Bugs to Find & Fix:</
      h3>
      <ul class="bug-list">
        <li>🐛 <strong>Bug 1:</
        strong> Mouse events don't 
        work on canvas</li>
        <li>🐛 <strong>Bug 2:</
        strong> Keyboard shortcuts 
        not responding</li>
        <li>🐛 <strong>Bug 3:</
        strong> Tool selection 
        doesn't update visually</
        li>
        <li>🐛 <strong>Bug 4:</
        strong> Drawing continues 
        when mouse leaves canvas</
        li>
        <li>🐛 <strong>Bug 5:</
        strong> Event logger shows 
        'undefined' events</li>
      </ul>
    </div>
  </div>

  <script>
    // INTENTIONAL BUGS FOR EVENT 
    HANDLING DEBUGGING
    
    // Global variables
    let canvas, ctx;
    let isDrawing = false;
    let currentTool = 'pen';
    let currentColor = '#000000';
    let currentSize = 5;
    let lastX = 0;
    let lastY = 0;
    let drawingHistory = [];
    
    // BUG 1: Canvas event 
    listeners not properly attached
    function initializeCanvas() {
      canvas = document.
      getElementById
      ('drawingCanvas');
      ctx = canvas.getContext
      ('2d');
      
      // BUG 1: Using wrong event 
      names
      canvas.addEventListener
      ('mousedown', startDrawing);
      canvas.addEventListener
      ('mousemove', draw);
      canvas.addEventListener
      ('mouseup', stopDrawing);
      // Missing: canvas.
      addEventListener('mouseout', 
      stopDrawing);
      
      // BUG 1: Event listeners 
      attached to wrong element
      document.addEventListener
      ('mousedown', 
      startDrawing); // Should be 
      canvas only
      
      console.log('Canvas 
      initialized');
    }
    
    // BUG 2: Keyboard event 
    listener not attached properly
    function 
    initializeKeyboardEvents() {
      // BUG 2: Using wrong event 
      type
      document.addEventListener
      ('keypress', 
      handleKeyboard); // Should 
      be 'keydown'
      
      console.log('Keyboard events 
      initialized');
    }
    
    function startDrawing(e) {
      isDrawing = true;
      [lastX, lastY] = getMousePos
      (e);
      
      // Save state for undo
      saveCanvasState();
      
      logEvent('Mouse Down', 
      `Tool: ${currentTool}, 
      Position: (${lastX}, $
      {lastY})`);
    }
    
    function draw(e) {
      if (!isDrawing) return;
      
      const [currentX, currentY] = 
      getMousePos(e);
      
      ctx.lineWidth = currentSize;
      ctx.lineCap = 'round';
      ctx.strokeStyle = 
      currentColor;
      
      switch (currentTool) {
        case 'pen':
          drawLine(lastX, lastY, 
          currentX, currentY);
          break;
        case 'eraser':
          erase(currentX, 
          currentY);
          break;
        case 'line':
          // For line tool, we'd 
          need to handle 
          differently
          drawLine(lastX, lastY, 
          currentX, currentY);
          break;
        case 'circle':
          // For circle tool, we'd 
          need to handle 
          differently
          drawCircle(lastX, lastY, 
          currentX, currentY);
          break;
      }
      
      [lastX, lastY] = [currentX, 
      currentY];
      
      // BUG 5: Logging undefined 
      values
      logEvent('Mouse Move', 
      `Position: (${x}, ${y})
      `); // Should be currentX, 
      currentY
    }
    
    function stopDrawing() {
      if (!isDrawing) return;
      isDrawing = false;
      
      logEvent('Mouse Up', 
      'Drawing stopped');
    }
    
    function getMousePos(e) {
      const rect = canvas.
      getBoundingClientRect();
      return [
        e.clientX - rect.left,
        e.clientY - rect.top
      ];
    }
    
    function drawLine(x1, y1, x2, 
    y2) {
      ctx.beginPath();
      ctx.moveTo(x1, y1);
      ctx.lineTo(x2, y2);
      ctx.stroke();
    }
    
    function drawCircle(x1, y1, 
    x2, y2) {
      const radius = Math.sqrt
      (Math.pow(x2 - x1, 2) + Math.
      pow(y2 - y1, 2));
      ctx.beginPath();
      ctx.arc(x1, y1, radius, 0, 2 
      * Math.PI);
      ctx.stroke();
    }
    
    function erase(x, y) {
      ctx.save();
      ctx.globalCompositeOperation 
      = 'destination-out';
      ctx.beginPath();
      ctx.arc(x, y, currentSize, 
      0, 2 * Math.PI);
      ctx.fill();
      ctx.restore();
    }
    
    // BUG 3: Tool selection 
    doesn't update button styles
    function selectTool(tool) {
      currentTool = tool;
      
      // BUG 3: Not removing 
      active class from previous 
      tool
      const buttons = document.
      querySelectorAll('.toolbar 
      button');
      buttons.forEach(btn => btn.
      classList.remove
      ('active-tool'));
      
      // BUG 3: Wrong element ID 
      used
      const activeButton = 
      document.getElementById(tool 
      + 'Tool'); // Should be 
      toolName + 'Tool'
      if (activeButton) {
        activeButton.classList.add
        ('active-tool');
      }
      
      logEvent('Tool Selected', 
      tool);
      console.log('Tool 
      selected:', tool);
    }
    
    function updateBrushSize() {
      const sizeSlider = document.
      getElementById('brushSize');
      currentSize = sizeSlider.
      value;
      document.getElementById
      ('sizeDisplay').textContent 
      = currentSize + 'px';
      
      logEvent('Brush Size 
      Changed', currentSize + 
      'px');
    }
    
    function updateColor() {
      const colorPicker = document.
      getElementById
      ('colorPicker');
      currentColor = colorPicker.
      value;
      
      logEvent('Color Changed', 
      currentColor);
    }
    
    function clearCanvas() {
      ctx.clearRect(0, 0, canvas.
      width, canvas.height);
      drawingHistory = [];
      
      logEvent('Canvas Cleared', 
      'All drawings removed');
    }
    
    function saveCanvasState() {
      drawingHistory.push(ctx.
      getImageData(0, 0, canvas.
      width, canvas.height));
      
      // Limit history to prevent 
      memory issues
      if (drawingHistory.length > 
      10) {
        drawingHistory.shift();
      }
    }
    
    function undoLastAction() {
      if (drawingHistory.length > 
      0) {
        const previousState = 
        drawingHistory.pop();
        ctx.putImageData
        (previousState, 0, 0);
        
        logEvent('Undo', 'Last 
        action undone');
      } else {
        logEvent('Undo Failed', 
        'No actions to undo');
      }
    }
    
    function saveDrawing() {
      const link = document.
      createElement('a');
      link.download = 'my-drawing.
      png';
      link.href = canvas.toDataURL
      ();
      link.click();
      
      logEvent('Drawing Saved', 
      'Downloaded as PNG');
    }
    
    // BUG 2: Keyboard event 
    handler with wrong key 
    detection
    function handleKeyboard(e) {
      // BUG 2: Using wrong 
      property for key detection
      const key = e.keyCode; // 
      Should be e.key or e.code
      
      document.getElementById
      ('currentKey').textContent = 
      key;
      
      // BUG 2: Wrong key 
      comparisons
      switch (key) {
        case 80: // Should be 'p' 
        or 'P'
          selectTool('pen');
          break;
        case 69: // Should be 'e' 
        or 'E'
          selectTool('eraser');
          break;
        case 76: // Should be 'l' 
        or 'L'
          selectTool('line');
          break;
        case 67: // Should be 'c' 
        or 'C'
          selectTool('circle');
          break;
        case 32: // Should be ' ' 
        (space)
          e.preventDefault();
          clearCanvas();
          break;
      }
      
      // Handle Ctrl+Z for undo
      if (e.ctrlKey && key === 90) 
      { // Should be e.key === 'z'
        e.preventDefault();
        undoLastAction();
      }
      
      logEvent('Key Pressed', key);
    }
    
    function logEvent(eventType, 
    details) {
      const eventLog = document.
      getElementById('eventLog');
      const timestamp = new Date().
      toLocaleTimeString();
      const logEntry = `[$
      {timestamp}] ${eventType}: $
      {details}\n`;
      
      eventLog.textContent += 
      logEntry;
      eventLog.scrollTop = 
      eventLog.scrollHeight;
    }
    
    function clearEventLog() {
      document.getElementById
      ('eventLog').textContent = 
      '';
    }
    
    // Initialize the application
    window.onload = function() {
      initializeCanvas();
      initializeKeyboardEvents();
      
      console.log('Drawing app 
      loaded - Ready for 
      debugging!');
      console.log('Open Developer 
      Tools (F12) to see debug 
      messages');
      console.log('Try drawing, 
      using keyboard shortcuts, 
      and watch for errors');
      
      logEvent('App Initialized', 
      'Drawing app ready');
    };
    
    /*
    🎯 DEBUGGING EXERCISES FOR 
    STUDENTS:
    
    1. **Event Listeners**: Fix 
    mouse and keyboard event 
    attachment
    2. **Event Properties**: Use 
    correct event object properties
    3. **Element Selection**: Fix 
    ID-based element selection
    4. **Event Propagation**: 
    Handle mouse events properly
    5. **Variable References**: 
    Fix undefined variable usage
    
    🔧 EVENT HANDLING TECHNIQUES 
    TO PRACTICE:
    - addEventListener() vs 
    onclick attributes
    - Mouse events: mousedown, 
    mousemove, mouseup, mouseout
    - Keyboard events: keydown, 
    keypress, keyup
    - Event object properties: e.
    key, e.keyCode, e.clientX, e.
    clientY
    - Event prevention: e.
    preventDefault()
    - Event delegation and bubbling
    - Canvas coordinate calculation
    - State management in 
    interactive applications
    */
  </script>
</body>
</html>
```
Now I'll create the debugging guide for this lesson:

```
# 🎨 Lesson 3: Event Handling 
Debugging Guide

## Learning Objectives
By the end of this lesson, 
students will be able to:
- Understand different types of 
event listeners and their proper 
usage
- Debug mouse and keyboard event 
handling issues
- Fix event object property access 
errors
- Handle canvas-based interactions 
and coordinate calculations
- Implement proper event 
delegation and state management

## Project Setup
1. Open `drawing_app_debug.html` 
in your web browser
2. Open Developer Tools (F12 or 
right-click → Inspect)
3. Go to the Console tab to see 
error messages
4. Try interacting with the 
drawing app (mouse clicks, 
keyboard shortcuts)
5. Watch the Event Logger to see 
what events are being captured

## 🐛 Bugs to Find and Fix

### Bug 1: Mouse Events Not 
Working Properly
**Problem**: Drawing doesn't work 
correctly on the canvas
**Location**: `initializeCanvas()` 
function and event listener setup
**Learning Focus**: Proper event 
listener attachment and event types
**Symptoms**: 
- Drawing might not start/stop 
correctly
- Events might fire on wrong 
elements
- Mouse leaving canvas doesn't 
stop drawing

**Debugging Steps:**
1. Check which elements have event 
listeners attached
2. Verify event listener names are 
correct
3. Ensure all necessary mouse 
events are handled

### Bug 2: Keyboard Shortcuts Not 
Responding
**Problem**: Pressing keyboard 
shortcuts doesn't change tools
**Location**: 
`initializeKeyboardEvents()` and 
`handleKeyboard()` functions
**Learning Focus**: Keyboard event 
types and key property access
**Symptoms**:
- Key presses don't trigger tool 
changes
- Wrong key codes being detected
- Ctrl+Z undo not working

**Debugging Steps:**
1. Check if keyboard event 
listener is attached
2. Verify correct event type 
(keydown vs keypress)
3. Check key detection method (e.
key vs e.keyCode)

### Bug 3: Tool Selection Visual 
Updates
**Problem**: Clicking tool buttons 
doesn't show which tool is active
**Location**: `selectTool()` 
function
**Learning Focus**: CSS class 
manipulation and element selection
**Symptoms**:
- Active tool button doesn't 
highlight
- Previous tool button stays 
highlighted
- Wrong button gets highlighted

**Debugging Steps:**
1. Check CSS class removal from 
previous buttons
2. Verify element ID construction
3. Ensure correct button gets the 
active class

### Bug 4: Drawing Continues 
Outside Canvas
**Problem**: Drawing doesn't stop 
when mouse leaves canvas area
**Location**: Canvas event 
listener setup
**Learning Focus**: Mouse event 
handling and boundaries
**Symptoms**:
- Drawing continues when mouse 
moves outside canvas
- isDrawing state not properly 
managed

**Debugging Steps:**
1. Check if mouseout/mouseleave 
events are handled
2. Verify drawing state management
3. Test mouse behavior at canvas 
boundaries

### Bug 5: Event Logger Shows 
Undefined Values
**Problem**: Event log displays 
'undefined' instead of actual 
values
**Location**: `draw()` function 
and `logEvent()` calls
**Learning Focus**: Variable scope 
and proper variable references
**Symptoms**:
- Event log shows "Position: 
(undefined, undefined)"
- Wrong variable names being used

**Debugging Steps:**
1. Check variable names in 
logEvent calls
2. Verify variable scope and 
availability
3. Ensure correct event object 
properties are accessed

## 🔧 Event Handling Concepts 
Covered

### Mouse Events
```javascript
// Basic mouse events
element.addEventListener
('mousedown', function(e) {
    // Mouse button pressed
});

element.addEventListener
('mousemove', function(e) {
    // Mouse moved
});

element.addEventListener
('mouseup', function(e) {
    // Mouse button released
});

element.addEventListener
('mouseout', function(e) {
    // Mouse left element
});
```
### Keyboard 
```javascript
// Keyboard event handling
document.addEventListener('keydown', function(e) {
    console.log('Key pressed:', e.key);
    console.log('Key code:', e.keyCode);
    
    // Check for specific keys
    if (e.key === 'p' || e.key === 'P') {
        // P key pressed
    }
    
    // Check for modifier keys
    if (e.ctrlKey && e.key === 'z') {
        e.preventDefault(); // Prevent default browser action
        // Ctrl+Z pressed
    }
});
```
### Keyboard Events
```javascript
// Keyboard event handling
document.addEventListener('keydown', function(e) {
    console.log('Key pressed:', e.key);
    console.log('Key code:', e.keyCode);
    
    // Check for specific keys
    if (e.key === 'p' || e.key === 'P') {
        // P key pressed
    }
    
    // Check for modifier keys
    if (e.ctrlKey && e.key === 'z') {
        e.preventDefault(); // Prevent default browser action
        // Ctrl+Z pressed
    }
});
```
### Canvas Coordinate Calculation
```javascript
function getMousePos(e) {
    const rect = canvas.getBoundingClientRect();
    return [
        e.clientX - rect.left,
        e.clientY - rect.top
    ];
}
```
### Event Object Properties
- e.clientX, e.clientY - Mouse position relative to viewport
- e.key - String representation of key pressed
- e.keyCode - Numeric code of key (deprecated but still used)
- e.ctrlKey, e.shiftKey, e.altKey - Modifier key states
- e.preventDefault() - Prevent default browser behavior

## 🎯 Debugging Techniques for Events
### 1. Console Logging Events
```javascript
function debugEventHandler(e) {
    console.log('Event type:', e.type);
    console.log('Target element:', e.target);
    console.log('Mouse position:', e.clientX, e.clientY);
    console.log('Key pressed:', e.key);
}
```

### 2. Event Listener Verification
```javascript
// Check if event listeners are attached
console.log('Event listeners:', getEventListeners(element));
```

### 3. State Tracking
```javascript
// Track application state
console.log('Current tool:', currentTool);
console.log('Is drawing:', isDrawing);
console.log('Mouse position:', lastX, lastY);
```

### 4. Event Flow Testing
- Test event firing order
- Check event bubbling/capturing
- Verify event target elements
## 🚀 Extension Challenges
Once you've fixed all the bugs, try these additional features:

1. Touch Events : Add support for mobile touch drawing
2. Drag and Drop : Implement image drag-and-drop onto canvas
3. Right-Click Menu : Add custom context menu
4. Multi-Touch : Support pinch-to-zoom gestures
5. Event Delegation : Use event delegation for tool buttons
## 💡 Common Event Handling Mistakes
1. Wrong Event Type : Using 'click' instead of 'mousedown'
2. Missing Event Listeners : Forgetting to attach listeners
3. Incorrect Element : Attaching listeners to wrong elements
4. Event Object Properties : Using wrong property names
5. State Management : Not properly tracking interaction state
6. Memory Leaks : Not removing event listeners when needed
## 🎓 Learning Outcomes
After completing this debugging exercise, you should understand:

- How to properly attach and manage event listeners
- Different types of mouse and keyboard events
- Event object properties and their usage
- Canvas interaction and coordinate systems
- State management in interactive applications
- Debugging techniques for event-driven code
## 🔍 Testing Your Fixes
1. Mouse Drawing : Click and drag to draw on canvas
2. Tool Switching : Click tool buttons and verify visual feedback
3. Keyboard Shortcuts : Press P, E, L, C keys to switch tools
4. Canvas Boundaries : Test drawing at canvas edges
5. Event Logging : Check that all events are properly logged
6. Undo Functionality : Use Ctrl+Z to undo actions
7. Clear Canvas : Press spacebar to clear canvas
Remember: Event handling is fundamental to interactive web applications. Understanding how events work and how to debug them will make you a much more effective JavaScript developer!


This Event Handling project includes:

1. **Interactive Drawing Canvas** with multiple tools (pen, eraser, line, circle)
2. **Mouse Event Handling** - mousedown, mousemove, mouseup, mouseout
3. **Keyboard Event Handling** - tool shortcuts and key combinations
4. **Real-time Event Logging** - shows all events as they happen
5. **Visual State Management** - active tool highlighting
6. **Canvas Interactions** - coordinate calculation and drawing

**Intentional Bugs for Debugging Practice:**
- Incorrect event listener attachment
- Wrong keyboard event types and key detection
- CSS class manipulation errors
- Missing event handlers for canvas boundaries
- Undefined variable references in event logging

The project teaches essential event handling concepts while providing comprehensive debugging practice, perfect for Lesson 3 of your JavaScript course!