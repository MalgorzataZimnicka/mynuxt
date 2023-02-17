<template>
	<div class="bg-yellow-500 flex flex-col justify-center align-middle">
		<div
			class="flex flex-col items-center w-96 h-96 drop-shadow-lg bg-white rounded-2xl"
		>
			<div class="flex w-96 place-content-evenly mt-2 z-10">
				<FaceColorList
					:list="FaceColorsList"
					:title="'colors'"
					@count-changes="HowManyChanges"
					@property="changeFaceColor"
				/>
				<FaceButtonList
					:list="EyebrowsList"
					:title="'eyebrow'"
					@count-changes="HowManyChanges"
					@property="changeEyebrow"
				/>
				<FaceButtonList
					:list="EyesList"
					:title="'eye'"
					@count-changes="HowManyChanges"
					@property="changeEye"
				/>
				<FaceButtonList
					:list="LipsList"
					:title="'lips'"
					@count-changes="HowManyChanges"
					@property="changeLips"
				/>
			</div>
			<FaceShow
				:PickedFaceColor="PickedFaceColor"
				:PickedEyebrow="PickedEyebrow"
				:PickedEye="PickedEye"
				:PickedLips="PickedLips"
			/>
			<div class="flex h-96">
				<p class="m-auto mb-3 ml-4">
					How many changes you've done: {{ count }}
				</p>
				<FaceRandomBtn
					:title="'random'"
					@click="random"
					@count-changes="HowManyChanges"
					class="ml-8 m-auto mb-1 drop-shadow-md"
				/>
			</div>
		</div>
	</div>
</template>
<script setup>
const FaceColorsList = [
	"bg-yellow-400",
	"bg-lime-500",
	"bg-cyan-500",
	"bg-indigo-500",
	"bg-pink-500",
	"bg-red-500",
];

const EyebrowsList = ["eyebrow1", "eyebrow2", "eyebrow3"];

const EyesList = ["eye1", "eye2", "eye3", "eye4", "eye5"];

const LipsList = ["lips1", "lips2", "lips3"];

const PickedFaceColor = ref(FaceColorsList[0]);
const PickedEyebrow = ref(EyebrowsList[0]);
const PickedEye = ref(EyesList[0]);
const PickedLips = ref(LipsList[0]);

function changeFaceColor(item) {
	PickedFaceColor.value = item;
}
function changeEyebrow(item) {
	PickedEyebrow.value = item;
}
function changeEye(item) {
	PickedEye.value = item;
}
function changeLips(item) {
	PickedLips.value = item;
}

function random() {
	PickedFaceColor.value =
		FaceColorsList[Math.floor(Math.random() * FaceColorsList.length)];
	PickedEyebrow.value =
		EyebrowsList[Math.floor(Math.random() * EyebrowsList.length)];
	PickedEye.value = EyesList[Math.floor(Math.random() * EyesList.length)];
	PickedLips.value = LipsList[Math.floor(Math.random() * LipsList.length)];
}

const count = ref(0);

function HowManyChanges() {
	count.value++;
}
</script>
<style></style>
