<script setup lang="ts">
import { Ref } from "vue";

const colorOptions: Ref<string[]> = ref([
	"bg-red-500",
	"bg-orange-400",
	"bg-amber-300",
	"bg-lime-500",
	"bg-cyan-500",
	"bg-purple-400",
]);

//set level and amount of color options

type Level = {
	id: number;
	value: number;
	name: string;
};

const levelProp: Ref<Level[]> = ref([
	{
		id: 0,
		value: 0,
		name: "level",
	},
	{
		id: 1,
		value: 4,
		name: "easy",
	},
	{
		id: 2,
		value: 5,
		name: "middle",
	},
	{
		id: 3,
		value: 6,
		name: "hard",
	},
]);

const levelName: Ref<string> = ref("level");
const newColorOptions: Ref<string[]> = ref([]);

function setDifficult(number: number) {
	const workNumber: number = number % levelProp.value.length;
	const level = levelProp.value.filter((level) => level.id === workNumber);
	levelName.value = level[0].name;
	newColorOptions.value = colorOptions.value.slice(
		colorOptions.value.length - level[0].value
	);
	drawnColors.value = [];
	drawnColorsFunction();
	console.log(drawnColors.value);
}

// set random colors

const drawnColors: Ref<string[]> = ref([]);

function drawnColorsFunction() {
	for (let i = 0; i < newColorOptions.value.length; i++) {
		const number = Math.floor(Math.random() * newColorOptions.value.length);
		const drawnObjectWithColor: string[] = newColorOptions.value.filter(
			(element, index) => index === number
		);
		drawnColors.value.push(drawnObjectWithColor[0]);
	}
}
</script>
<script lang="ts"></script>
<template>
	<div class="flex flex-col gap-2">
		<p class="text-6xl">Pick color game</p>
		<div class="flex h-20 items-center justify-evenly">
			<GameColorIncreaseNumber
				:levelName="levelName"
				@increaseNumber="setDifficult"
			/>
			<!-- <p>statistic</p>
			<p>easy: {{ statisticEasy }}</p>
			<p>middle: {{ statisticMiddle }}</p>
			<p>hard: {{ statisticHard }}</p> -->
		</div>
		<GameColorLine
			:newColorOptions="newColorOptions"
			:drawnColors="drawnColors"
		/>
	</div>
</template>
<style scoped></style>
