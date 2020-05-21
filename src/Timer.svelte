<script>
	import ProgressBar from './ProgressBar.svelte';
	const totalSeconds = 5;
	let secondsLeft = totalSeconds;
	let isRunning = false;
	let progress = 0;

	function startTimer() {
		isRunning = true;
		let timer = setInterval(() => {
			progress += (100 / totalSeconds);
			secondsLeft -= 1;
			if (secondsLeft == 0) {
				progress = 0;
				clearInterval(timer);
				isRunning = false;
				secondsLeft = totalSeconds;
			}
		}, 1000);
	}
</script>

<style>
	h2 {
		margin: 0;
	}
	.start {
		background-color: rgb(94, 172, 175);
		width: 100%;
		margin: 10px 0;
	}
	.start[disabled] {
		background-color: gray;
		cursor: not-allowed;
	}
</style>

<div bp="grid">
	<h2 bp="offset-5@md 4@md 12@sm">
		Seconds Left: {secondsLeft}
	</h2>
</div>
<ProgressBar {progress}/>

<div bp="grid">
	<button disabled={isRunning} bp="offset-5@md 4@md 12@sm" class="start" on:click={startTimer}>Start</button>
</div>
