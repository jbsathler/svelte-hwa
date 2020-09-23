<script>
    import HowTo from "./components/HowTo.svelte";
    import Timer from "./components/Timer.svelte";

    let audio;

    function playSound() {
        audio.play();
    }
</script>

<style>
    h1, h3 {
        text-align: center;
    }
</style>

<h1>Handwashing App</h1>

<Timer on:end={playSound} />

<HowTo />

<h3>
  <a href="https://www.who.int/gpsc/clean_hands_protection/en/">Picture Source</a>

  <a href="https://freesound.org/people/metrostock99/sounds/345086/">Sound Source</a>
</h3>

<audio bind:this={audio}>
    <source src="assets/sound.wav" />
    <track kind="captions" />
</audio>
