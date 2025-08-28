<script setup>
import {  onMounted, ref } from 'vue';
import axios from 'axios';
import Card from './Card.vue';

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
}

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
		:second-word="card.translation"
		statePosition="closed"
		statusPosition="pending"/>
	</div>
</template>

<style scoped>
	.cards-wrapper {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		gap: 66px 100px;
	}
</style>