<script setup>
import {  onMounted, ref } from 'vue';
import axios from 'axios';
import Card from './Card.vue';
import Button from './Button.vue';

let data = ref([]);

async function getData() {
	try {
   	const response = await axios.get('http://localhost:8080/api/random-words');
		return data.value = response.data;
	} catch (error) {
   	console.error(error);
	}
};

const loadData = async () => {
	data.value = await getData();
	data.value = data.value.map(el => ({ ...el, statePosition: 'closed', statusPosition: 'pending' }));
};

const restartGame = () => {
	loadData();
};

onMounted(() => {
	loadData();
});
</script>

<template>
	<div class="cards-wrapper">
		<Card 
		v-for="card in data" 
		:key="card.word" 
		:first-word="card.word" 
		:second-word="card.translation"/>
	</div>
		<Button 
			class="restart-game__btn" 
			@click="restartGame">
			Начать заново
		</Button>
</template>

<style scoped>
	.cards-wrapper {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		gap: 66px 100px;
		margin-bottom: 100px;
	}

	.restart-game__btn {
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