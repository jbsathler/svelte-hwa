<script>
    import ProgressBar from "./ProgressBar.svelte";

    const totalSeconds = 20;
    let secondsLeft = totalSeconds;
    let isRunning = false;

    $: progress = (totalSeconds - secondsLeft) * 100 / totalSeconds;
    
    function startTimer() {
        isRunning = true;
        const timer = setInterval(() => {
            secondsLeft -= 1;
            if (secondsLeft == 0) {
                clearInterval(timer);
                secondsLeft = totalSeconds;
                isRunning = false;
            }
        }, 1000);
    }

</script>

<style>
    h2 {
        margin: 0;
    }
    .start {
        background-color: #9A4949;
        margin: 10px 0;
        width: 100%;
    }
    .start[disabled] {
        background-color: #C2C2C2;
        cursor: not-allowed;
    }
</style>

<div bp="grid">
    <h2 bp="offset-5@md 4@md 12@sm">Seconds Left: {secondsLeft}</h2>
</div>

<ProgressBar {progress} />

<div bp="grid">
    <button
        disabled={isRunning}
        on:click={startTimer}
        bp="offset-5@md 4@md 12@sm"
        class="start"
    >Start</button>
</div>
