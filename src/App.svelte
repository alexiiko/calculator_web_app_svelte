<script lang="ts">
  let equation: string = "";

  function clearEquation()
  {
    equation = ""
  }

  function appendNumber(number: string)
  {
    equation += number
  }

  function appendOperator(operator: string)
  {
    if (!isNaN(Number(equation[equation.length - 1])))
    {
      equation += operator
    }
  }

  function appendColon()
  {
    if (!isNaN(Number(equation[equation.length - 1])))
    {
      if (!equation.includes("."))
      {
        equation += "."
      }
    }
  }

  function calcEquation()
  {
    if (equation)
    {
      equation = eval(equation).toString()
    }
  }

  function deleteLastChar()
  {
    equation = equation.slice(0, -1)
  }

  function calcPercent()
  {
    if (!isNaN(Number(equation[equation.length - 1])))
    {
      equation = (eval(equation) / 100).toString()
    }
  }
</script>



<div class="labelContainer">
   <label >{equation}</label>
</div>

<div>
  <div class="rows">
     <button class="specialSigns button container" on:click={clearEquation}>C</button>
     <button class="specialSigns button container" on:click={deleteLastChar}>⌫</button>
     <button class="specialSigns button container" on:click={calcPercent}>%</button>
     <button class="operators button container" on:click={() => appendOperator("/")}>÷</button>
  </div>

  <div class="rows">
    <button class="numbers button container" on:click={() => appendNumber("7")}>7</button>
    <button class="numbers button container" on:click={() => appendNumber("8")}>8</button>
    <button class="numbers button container" on:click={() => appendNumber("9")}>9</button>
    <button class="operators button container" on:click={() => appendOperator("*")}>×</button>
  </div>

  <div class="rows">
     <button class="numbers button container" on:click={() => appendNumber("4")}>4</button>
     <button class="numbers button container" on:click={() => appendNumber("5")}>5</button>
     <button class="numbers button container" on:click={() => appendNumber("6")}>6</button>
     <button class="operators button container" on:click={() => appendOperator("-")}>-</button>
  </div>

  <div class="rows">
     <button class="numbers button container"on:click={() => appendNumber("1")}>1</button>
     <button class="numbers button container" on:click={() => appendNumber("2")}>2</button>
     <button class="numbers button container" on:click={() => appendNumber("3")}>3</button>
     <button class="operators button container" on:click={() => appendOperator("+")}>+</button>
  </div>

  <div class="rows">
     <button class="numbers button container halfSpan" on:click={() => appendNumber("0")}>0</button>
     <button class="specialSigns button container" on:click={appendColon}>.</button>
     <button class="specialSigns button container" on:click={calcEquation}>=</button>
  </div>
</div>


<style>
  @import "style.css";
</style>
