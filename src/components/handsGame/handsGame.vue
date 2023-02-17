<script setup lang="ts">
import { Ref } from "vue";

type GameRound = {
	player: string;
	ai: string;
	winner: string;
};

type GameResult = {
	rounds: number;
	wins: number;
	losses: number;
	draws: number;
};

type Options = {
	name: string;
	src: string;
	isActive: boolean;
};

// const gameRound: Ref<GameRound> = ref({
// 	player: "",
// 	ai: "",
// 	winner: "",
// });

// const gameResult: Ref<GameResult> = ref({
// 	rounds: 0,
// 	wins: 0,
// 	losses: 0,
// 	draws: 0,
// });

const options: Ref<Options[]> = ref([
	{
		name: "lion",
		src: ".../assets/images/lion.svg",
		isActive: false,
	},
	{
		name: "shark",
		src: ".../assets/images/shark.svg",
		isActive: false,
	},
	{
		name: "owl",
		src: "/_nuxt/assets/images/owl.svg",
		isActive: false,
	},
]);
</script>
<template>
	<div class="max-w-2xl text-base flex flex-col justify-center items-center">
		<h1 class="font-extrabold text-2xl text-center p-4">
			Stone, paper, scissors - which one will you choose?
		</h1>
		<p class="text-center p-8 max-w-lg">
			Rules: Win after five wins. Select your card and push start button:
		</p>
		<div class="flex">
			<HandsGameCard v-for="option in options" :option="option" />
		</div>
		<button class="w-2/5 mt-6 bg-gray-400 rounded-md shadow-md">Play</button>
		<div class="flex flex-col w-full p-8">
			<!-- <div>
				<p>
					Your choise: <span>{{ gameRound.player }}</span>
				</p>
				<p>
					Computer choise: <span>{{ gameRound.ai }}</span>
				</p>
				<p>
					Winner: <span>{{ gameRound.winner }}</span>
				</p>
			</div>
			<div class="flex flex-wrap">
				<p class="w-1/2">
					Rounds: <span>{{ gameResult.rounds }}</span>
				</p>
				<p class="w-1/2">
					Wins: <span>{{ gameResult.wins }}</span>
				</p>
				<p class="w-1/2">
					Losses: <span>{{ gameResult.losses }}</span>
				</p>
				<p class="w-1/2">
					Draws: <span>{{ gameResult.draws }}</span>
				</p>
			</div> -->
		</div>
	</div>
</template>
<style scoped></style>
