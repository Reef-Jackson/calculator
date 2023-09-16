<script>
    let result = "";

    function appendToResult(value) {
        result += value;
        updateDisplay();
    }

    function clearResult() {
        result = "";
        updateDisplay();
    }

    function calculateResult() {
        try {
            result = eval(result);
            updateDisplay();
        } catch (error) {
            result = "Error";
            updateDisplay();
        }
    }

    function updateDisplay() {
        document.querySelector('.result-input').value = result;
    }

    // Add event listener for keydown events on the document
    document.addEventListener('keydown', (event) => {
        const key = event.key;
        const isNumeric = /^[0-9]$/.test(key);

        if (isNumeric || key.match(/[+\-*/.=]|Enter|Backspace|Escape/)) {
            event.preventDefault(); // Prevent default behavior for these keys

            if (key === 'Enter' || key === '=') {
                calculateResult();
            } else if (key === 'Backspace') {
                result = result.slice(0, -1); // Remove the last character
                updateDisplay();
            } else if (key === 'Escape') {
                clearResult();
            } else {
                appendToResult(key);
            }
        }
    });
</script>


<div class="calculator">
    <input type="text" class="result-input" bind:value={result} readonly>
    <div class="buttons">
        <button on:click={() => appendToResult('7')}>7</button>
        <button on:click={() => appendToResult('8')}>8</button>
        <button on:click={() => appendToResult('9')}>9</button>
        <button on:click={() => appendToResult('+')}>+</button>
        <button on:click={() => appendToResult('4')}>4</button>
        <button on:click={() => appendToResult('5')}>5</button>
        <button on:click={() => appendToResult('6')}>6</button>
        <button on:click={() => appendToResult('-')}>&minus;</button>
        <button on:click={() => appendToResult('1')}>1</button>
        <button on:click={() => appendToResult('2')}>2</button>
        <button on:click={() => appendToResult('3')}>3</button>
        <button on:click={() => appendToResult('*')}>&times;</button>
        <button on:click={() => appendToResult('0')}>0</button>
        <button on:click={() => clearResult()}>C</button>
        <button on:click={() => calculateResult()}>=</button>
        <button on:click={() => appendToResult('/')}>&divide;</button>
    </div>
</div>

<style>
    .calculator {
        width: 300px;
        margin: 0 auto;
        border: 1px solid #ccc;
        padding: 10px;
        margin-top: 4rem;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    }

    .result-input {
        width: 100%;
        height: 40px;
        font-size: 18px;
        margin-bottom: 10px;
        box-sizing: border-box; 
    }

    .buttons {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 5px;
    }

    .buttons button {
        width: 100%;
        height: 50px;
        font-size: 18px;
        background-color: #f2f2f2;
        border: 1px solid #ccc;
        cursor: pointer;
    }

    .buttons button:hover {
        background-color: #e0e0e0;
    }
</style>
