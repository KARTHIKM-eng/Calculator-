let displayValue = '0';
let firstOperand = null;
let operator = null;
let waitingForSecondOperand = false;

const display = document.getElementById('display');

function updateDisplay() {
    display.textContent = displayValue;
}

function clearDisplay() {
    displayValue = '0';
    firstOperand = null;
    operator = null;
    waitingForSecondOperand = false;
    updateDisplay();
}

function inputNumber(number) {
    if (waitingForSecondOperand) {
        displayValue = number;
        waitingForSecondOperand = false;
    } else {
        displayValue = displayValue === '0' ? number : displayValue + number;
    }
    updateDisplay();
}

function setOperator(nextOperator) {
    const inputValue = parseFloat(displayValue);
    
    if (firstOperand === null) {
        firstOperand = inputValue;
    } else if (operator) {
        const result = calculate(firstOperand, inputValue, operator);
        displayValue = `${result}`;
        firstOperand = result;
        updateDisplay();
    }
    operator = nextOperator;
    waitingForSecondOperand = true;
}

function calculate() {
    const inputValue = parseFloat(displayValue);
    
    if (operator && !waitingForSecondOperand) {
        const result = firstOperand !== null 
            ? operate(firstOperand, inputValue, operator) 
            : inputValue;
        displayValue = `${result}`;
        firstOperand = null;
        operator = null;
        updateDisplay();
    }
}

function operate(a, b, op) {
    switch(op) {
        case '+': return a + b;
        case '-': return a - b;
        case '*': return a * b;
        case '/': return a / b;
        default: return b;
    }
}

// Event listeners for buttons
document.querySelectorAll('[data-number]').forEach(button => {
    button.addEventListener('click', () => inputNumber(button.textContent));
});

document.querySelectorAll('[data-operator]').forEach(button => {
    button.addEventListener('click', () => setOperator(button.textContent));
});
