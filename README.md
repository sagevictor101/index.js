<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <link rel="stylesheet" href="style2002.css">

</head>
<body>


    <div class="calculator-grid">
        <div class="output">
            <div data-previous-operand class="previous-operand">123 +</div>
            <div data-current-operand class="current-operand">456</div>
        </div>
        <button data-all-clear class="span-two">AC</button>
        <button data-delete>DEL</button>
        <button data-operation>*</button>
        <button data-number>1</button>
        <button data-number>2</button>
        <button data-number>3</button>
        <button data-operation>*</button>
        <button data-number>4</button>
        <button data-number>5</button>
        <button data-number>6</button>
        <button data-operation>+</button>
        <button data-number>7</button>
        <button data-number>8</button>
        <button data-number>9</button>
        <button data-operation>-</button>
        <button data-number>.</button>
        <button data-number>0</button>
        <button data-equals class="span-two">=</button>
    </div>

    <script src="script2002.js"></script>
</body>
</html>
64
script2002.js
@@ -0,0 +1,64 @@
class Calculator {
    constructor(previousOperandTextElement, currentOperandTextElement) {
        this.previousOperandTextElement = previousOperandTextElement
        this.currentOperandTextElement = currentOperandTextElement
        this.clear()
    }

    clear() {
        this.currentOperand = ""
        this.previousOperand = ""
        this.operation = undefined
    }

    delete() {

    }

    appendNumber(number) {
        if (number === '.' && this.currentOperand.includes('.')) return
      this.currentOperand = this.currentOperand.toString() + number.toString()
    }

    chooseOperation(operation) {
       this.operation = operation
       this.previousOperand = this.currentOperand
       this.currentOperand = ''
    }

    compute() {

    }

    updateDisplay() {
      this.currentOperandTextElement.innerText = this.currentOperand
      this.previousOperandTextElement.innerText = this.previousOperand
    }
}

calculator.appendNumber(button.innerText)

const numberButtons = document.querySelectorAll('[data-number]')
const operationButtons = document.querySelectorAll('[data-operation]')
const equalsButton = document.querySelectorAll('[data-equals]')
const deleteButton = document.querySelectorAll('[data-delete]')
const allClearButton = document.querySelectorAll('[data-all-clear]')
const previousOperandTextElement = document.querySelectorAll('[data-previous-operand]')
const currentOperandTextElement = document.querySelectorAll('[data-current-operand]')

const calculator = new Calculator(previousOperandTextElement, 
currentOperandTextElement)

numberButtons.forEach(button => {
    button.addEventListener('click', () -> {
        calculator.appendNumber(button.innerText)
        calculator.updateDisplay()
    })

    operationButtons.forEach(button => {
        button.addEventListener('click', () -> {
            calculator.chooseOperation(button.innerText)
            calculator.updateDisplay()

        })
})
59
style2002.css
@@ -0,0 +1,59 @@
*, *::before, *::after {
    box-sizing: border-box;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: normal;
}

body {
    padding: 0;
    margin: 0;
    background: linear-gradient(to right, black, yellow);
}

.calculator-grid {
    display: grid;
    justify-content: center;
    align-content: center;
    min-height: 100vh;
    grid-template-columns: repeat(4, 100px);
    grid-template-rows: minmax(120px, auto) repeat(5, 100px);
}

.calculator-grid > button {
    cursor: pointer;
    font-size: 2em;
    border: 1px solid white;
    outline: none;
    background-color: greenyellow;
}

.calculator-grid > button:hover {
    background-color: yellow;
}

.span-two {
    grid-column: span 2;
}

.output {
    grid-column: 1 /-1;
    background-color: black;
    display: flex;
    align-items: flex-end;
    justify-content: space-around;
    flex-direction: column;
    padding: 10px;
    word-wrap: break-word;
    word-break: break-all;
}

.output .previous-operand {
    color: rgba(255, 255, 255, .75);
    font-size: 1.5rem;
}


.output .current-operand {
    color: white;
    font-size: 2.5rem;
} 
