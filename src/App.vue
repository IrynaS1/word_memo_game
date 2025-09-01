<script setup>
import { ref, provide } from 'vue';
import Header from './components/Header.vue';
import Button from './components/Button.vue';
import Cards from './components/Cards.vue';

let isActive = ref(true);
const score = ref(0);

const startGame = () => {
	isActive.value = !isActive.value;
};

provide('updateScore', (points) => {
	score.value = score.value + points;
})
</script>

<template>
	<div class="page-wrapper">
		<Header :score="score"/>
		<main class="main">			
			<Cards v-if="!isActive"/>
			<Button 
				v-else
				class="start-game__btn" 
				@click="startGame">
				Начать игру
			</Button>

		</main>	
	</div>
</template>

<style scoped>
	.page-wrapper {
		padding: 0 64px;
	}

	.main {
		max-width: 100%;
		height: 100vh;
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
		gap: 100px;
	}

	.start-game__btn {
		width: 335px;
		background-color: var(--color-active);
		color: var(--color-secondary);
		border-radius: 100px;
		padding: 16px 0;
		border: none;
		font-size: 24px;
		font-weight: 400;
		line-height: 36px;
		cursor: pointer;
	}
</style>
