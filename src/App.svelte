<script>
    let value1 = 0;
    let selectedAnswer = ""; 

    function checkGuess1() {
        const resultBox = document.getElementById('result-1');
        const extraBox = document.getElementById('extra-box');

        if (value1 >= 370 && value1 <= 380) {
            resultBox.textContent = "Gut geschätzt! Es sind 375 Millionen PKW.";
            resultBox.style.color = "#9cbb50";
            extraBox.style.display = "block";
        } else if (value1 >= 350 && value1 <= 390) {
            resultBox.textContent = "Fast";
            resultBox.style.color = "orange";
            extraBox.style.display = "none";
        } else {
            resultBox.textContent = "Probiers nochmal";
            resultBox.style.color = "#e46767";
            extraBox.style.display = "none";
        }
    }

    function checkAnswer(answer) {
        selectedAnswer = answer; 
    }
</script>

<div class="text-box">
    <p>Wie viele <b>PKW</b> stoßen in <b>24 Stunden</b> so viel <b>Schwefeldioxid</b> aus wie ein Kreuzfahrtschiff in derselben Zeit?</p>
</div>

<div class="slider">
    <input
        id="slider"
        type="range"
        min="0"
        max="400"
        step="1"
        on:mouseup={checkGuess1}
        on:keyup={checkGuess1}
        bind:value={value1}
    />
    <label for="slider">{value1} Mio.</label>

    <div class="pictograms">
        {#each Array(Math.floor(value1)) as _}
            <img src="car4.png" alt="Car" width="25" />
        {/each}
    </div>

    <p style="font-size: 13px; margin-top: 12px;">Ein Auto = 1 Millionen PKW</p>
</div>

<div id="result-1" class="result-box-1"></div>

<div id="extra-box" class="extra-box" style="display: none;">
    <p>
Ein Kreuzfahrschiff stößt in 24 Stunden etwa so viel Schwefeldioxid aus, wie <b> 375 Millionen PKW </b> in derselben Zeit. PKW-Kraftstoffe enthalten deutlich <b> weniger Schwefel </b>, weshalb ihr Schwefeldioxid-Ausstoß im Vergleich verschwindend gering ist. 
    </p>
</div>

<style>
    :global(body) {
        background-color: #efe0cd; 
        margin: 0; 
        color: #427fb7; 
        font-size: 18px;
        font-family: PT Serif;
    }

    div {
        padding: 10px;
    }

    .text-box {
        padding: 18px;
        border-radius: 15px;
        margin: 30px;
    }

    .slider {
        margin: 30px;
        color: #427fb7;
        text-align: center;
    }

    input[type="range"] {
        width: 50%; 
        display: block; 
        margin: 10px auto; 
    }

    .result-box-1 {
        font-size: 1.2em;
        font-weight: bold;
        text-align: center;
        margin-top: 20px;
    }

    .extra-box {
        font-size: 1em;
        color: #427fb7; 
        text-align: justify;
        background-color: #e9ffe9;
        border-radius: 10px;
        padding: 15px;
        margin: 20px 30px;
    }

    .pictograms {
        display: flex;
        flex-wrap: wrap;
        justify-content: center; 
    }

    .pictograms img {
        margin: 2px;
    }
</style>
