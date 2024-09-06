<script>
// @ts-nocheck

	import { fade } from "svelte/transition";
	import {Howl} from "howler";
	import { onMount } from "svelte";

	let visible = true;
	let verdict = "";
	let retry = false;
	
	const vineBoom = new Howl({
		src: "https://www.myinstants.com/media/sounds/vine-boom.mp3",
	});
	const keyboard = new Howl({
		src: "https://www.myinstants.com/media/sounds/keyboard-typing.mp3",
	});
	const amimir = new Howl({
		src: "https://www.myinstants.com/media/sounds/amimir.mp3",
	});
	const sus = new Howl({
		src: "https://www.myinstants.com/media/sounds/53b1bab6-a8c3-4a1a-82db-7110ce1c29ef_6KNDGWD.mp3",
	});
	const kidsYay = new Howl({src: "https://www.myinstants.com/media/sounds/kids-saying-yay-sound-effect_3.mp3",
	});
	const drumRoll = new Howl({
		src: "https://www.myinstants.com/media/sounds/drum-roll-gaming-sound-effect-hd.mp3",
	});

	let sleepGifUrl ="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExZm8zd2F2aHJqdWUzdzB3Ynh6Z2hnN3dqdTg1NnFrazVxdjIxNmZmMSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/12cYyFxlbIgXeg/giphy.webp";
	let codeGifUrl = "https://media.tenor.com/bxe8Qsx3UusAAAAM/cat.gif";

	onMount(() => {
		const sleepGif = new Image();
		sleepGif.src = sleepGifUrl;
		const codeGif = new Image();
		codeGif.src = codeGifUrl;
	});

	function triggerVerdict() {
		visible = false;
		drumRoll.play();
		setTimeout(() => {
			generateVerdict();
		}, 4500);
	}
	
	function generateVerdict() {
	    const randomNumber = Math.floor(Math.random() * 2);
		verdict = randomNumber === 0 ? "Sleep 😴" : "Code 👨‍💻";
		if (verdict === "Code 👨‍💻") {
			vineBoom.play();
			keyboard.play();
			setTimeout(() => {
				sus.play();
				retry = true;
			}, 5000);
	} else {
			amimir.play();
			kidsYay.play();
		}
	}

	function reset() {
		visible = true;
		verdict = "";
		retry = false;
	}
</script>
	
<svelte:head>
	<title>Sleep or Code?</title>
</svelte:head>


<div class="flex flex-row items-center justify-center h-screen">
	<div class="relative flex flex-col items-center justify-center gap-8 w-screen">
		{#if visible === true}
			<h1 class="text-5xl font-mono font-semibold p-4 text-center" out:fade={{ duration: 2500 }}>Sleep or Code?</h1>
			<button class="text-base font-mono font bg-slate-300 hover:bg-slate-500 hover:text-white active:bg-slate-600 rounded-lg p-4 text-center" on:click={triggerVerdict} out:fade={{ duration: 2500 }}>
			The answer is...</button
			>
		{/if}
	
		<div class="flex flex-col items-center justify-center">
			{#if verdict === "Sleep 😴"}
				<img class="w-60" src={sleepGifUrl} alt="Sleeping cat" />
			{/if}
			{#if verdict === "Code 👨‍💻"}
				<img class="w-60" src={codeGifUrl} alt="Coding cat" />
			{/if}
		</div>
		
	
		<h1 class="text-2xl font-mono font-semibold">{verdict}</h1>
	
		{#if retry && verdict === "Code 👨‍💻"}
			<button on:click={reset} in:fade={{ duration: 3000 }} class="text-base font-mono retry-button bg-slate-300 hover:bg-slate-500 active:bg-slate-600 hover:text-white rounded-lg p-4"
			>Try again?</button
			>
		{/if}
	</div>
</div>


<style>
	.retry-button {
    position: absolute;
	bottom: -4rem;
    left: 50%;
    transform: translateX(-50%);
    z-index: 10;
	}
</style>
