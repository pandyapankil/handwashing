<script>
	import Timer from './Timer.svelte';
	import HowTo from './HowTo.svelte';

	let audio;
	function timerEnds() {
		audio.play();
	}
</script>

<style>
	h1, h3 {
		text-align: center;
	}
</style>

<h1>Handwashing App</h1>

<Timer on:end={timerEnds} />

<HowTo />

<h3>
	<a href="https://www.who.int/gpsc/media/how_to_handwash_lge.gif">Picture Source</a>
	<a href="https://www.soundboard.com/sb/sound/159369/">Sound Source</a>
</h3>

<audio bind:this={audio} src="sound.mp3"></audio>
