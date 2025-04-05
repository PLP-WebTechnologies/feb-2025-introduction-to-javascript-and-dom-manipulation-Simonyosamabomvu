<!-- index.html  -->

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DOM Manipulation Demo</title>
    <link rel="stylesheet" href="styles.css">
    <script src="script.js" defer></script>
</head>
<body>
    <header>
        <h1 id="main-heading">DOM Manipulation Demo</h1>
    </header>

    <main>
        <section class="content-section">
            <p id="dynamic-text">This text will change when you click the button below.</p>
            <button id="text-change-btn">Change Text</button>
        </section>

        <section class="content-section">
            <div id="style-demo" class="box">This box will change color.</div>
            <button id="style-change-btn">Change Style</button>
        </section>

        <section class="content-section">
            <div id="element-container">
                <p>Existing element</p>
            </div>
            <button id="toggle-element-btn">Toggle Element</button>
        </section>
    </main>

    <footer>
        <p>&copy; 2023 DOM Demo</p>
    </footer>
</body>
</html>

//script.js

// Wait for DOM to fully load
document.addEventListener('DOMContentLoaded', () => {
    // Task 1: Change text content dynamically
    const textChangeBtn = document.getElementById('text-change-btn');
    const dynamicText = document.getElementById('dynamic-text');
    
    textChangeBtn.addEventListener('click', () => {
        dynamicText.textContent = 'Text successfully changed using JavaScript!';
    });

    // Task 2: Modify CSS styles via JavaScript
    const styleChangeBtn = document.getElementById('style-change-btn');
    const styleDemo = document.getElementById('style-demo');
    
    styleChangeBtn.addEventListener('click', () => {
        styleDemo.style.backgroundColor = '#4CAF50';
        styleDemo.style.color = 'white';
        styleDemo.style.padding = '20px';
        styleDemo.textContent = 'Styles have been modified!';
    });

    // Task 3: Add/remove element on button click
    const toggleElementBtn = document.getElementById('toggle-element-btn');
    const elementContainer = document.getElementById('element-container');
    let newElementExists = false;
    let newElement = null;
    
    toggleElementBtn.addEventListener('click', () => {
        if (!newElementExists) {
            // Create new element
            newElement = document.createElement('p');
            newElement.textContent = 'New element added dynamically!';
            newElement.classList.add('highlight');
            elementContainer.appendChild(newElement);
            toggleElementBtn.textContent = 'Remove Element';
        } else {
            // Remove the element
            elementContainer.removeChild(newElement);
            toggleElementBtn.textContent = 'Add Element';
        }
        newElementExists = !newElementExists;
    });
});

/* styles.css */

body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
}

header {
    background-color: #f4f4f4;
    padding: 20px;
    text-align: center;
}

.content-section {
    margin: 30px 0;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 5px;
}

button {
    background-color: #333;
    color: white;
    border: none;
    padding: 10px 15px;
    margin-top: 10px;
    cursor: pointer;
    border-radius: 3px;
}

button:hover {
    background-color: #555;
}

.box {
    padding: 15px;
    background-color: #f8f8f8;
    border: 1px solid #ccc;
    margin-bottom: 10px;
}

.highlight {
    color: #d35400;
    font-weight: bold;
}
