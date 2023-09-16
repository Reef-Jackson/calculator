<script>
    import Calculator from "../components/calculator.svelte";
</script>

<div class="main-container">
    <div class="header-container">
        <h1>Calculator App</h1>
    </div>
    <div class="calculator-container">
        <Calculator />
    </div>
</div>


<style>
    .header-container {
        margin: auto;
        width: 66vw;
        height: fit-content;
    }
    .header-container h1 {
        padding-top: 1rem;
        margin: auto;
        text-align: center;
    }


</style>