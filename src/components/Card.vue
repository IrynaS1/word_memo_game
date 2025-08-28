<script setup>
import { ref } from 'vue';
import Button from './Button.vue';
import CloseIcon from '../icons/CloseIcon.vue';
import TickIcon from '../icons/TickIcon.vue';

let { firstWord, secondWord, statePosition, statusPosition } = defineProps({
	firstWord: String,
	secondWord: String,
	statePosition: String,
	statusPosition: String,
});

let word = ref(firstWord); 
let translation = ref(secondWord);
let state = ref('closed'); //state - closed | opened
let status = ref('pending'); //status - success | fail | pending

const flipCard = (newStatus) => {
	state.value = newStatus;
	word.value = translation.value;
};

const choiceFalse = (newState, newStatus) => {
	state.value = newState;
	status.value = newStatus;
};

const choiceTrue = (newState, newStatus) => {
	state.value = newState;
	status.value = newStatus;
};
</script>

<template>
	<div :id="id" class="card" >
		<div class="card__content-wrapper">
			<div class="card__content-wrapper-els card__number">01</div>
				<Button 
					v-if="state === 'closed' && status === 'pending'"
					class="card__content-wrapper-els card__actions" 
					@click="flipCard('opened')"
					>
					Перевернуть
				</Button > 
				<Button 
					v-else-if="state === 'opened' && status === 'pending'"
					class="card__content-wrapper-els card__actions card__btns" 
				>
					<CloseIcon @click="choiceFalse('closed', 'fail')"/>
					<TickIcon @click="choiceTrue('closed', 'success')"/>
				</Button>
				<Button 
					v-else-if="state === 'closed' && status === 'success' || status === 'fail'"
					class="card__content-wrapper-els card__actions card__ending" 
					@click="flipCard()"
					>
					Завершено
				</Button > 
				<div class="card__content-text">{{word}}</div>
			<!-- 	<CloseIcon class="status-icon" />
				<TickIcon class="status-icon"/>  -->
		</div>
	</div>
</template>

<style scoped>
	.card {
		width: 250px;
		height: 376px;
		padding: 19px 28px 24px;
		border-radius: 16px;
		box-shadow: 0px 0px 16px 0px rgba(0, 0, 0, 0.1);
		background-color: var(--color-secondary);
	}

	.card:hover {
		box-shadow: 10px 10px 10px 0px rgba(0, 0, 0, 0.05);
	}

	.card__content-wrapper {		
		display: flex;
		align-items: center;
		justify-content: center;
		position: relative;
		width: 100%;
		height: 100%;
		border: 1px solid var(--bg-color);
		border-radius: 12px;
	}

	.card__content-wrapper-els {
 		position: absolute; 
		background-color: var(--color-secondary);
	}

	.card__number {
		padding: 0 2px;
		left: 16px;
		top: -10px;
		color: var(--color--text-content);
		font-size: 14px;
		font-weight: 400;
	}

	.card__content-text {
		padding: 0 20px;
		text-align: center;
	}

	.card__actions {
		left: 33%;
		bottom: -10px;
		padding: 0 4px;
		color: rgba(34, 34, 34, 1);
		font-family: var(--font);
		font-size: 12px;
		font-weight: 600;
		line-height: 18px;
		border: none;
		text-transform: uppercase;
		cursor: pointer;
	}

	.card__btns {
		display: flex;
		padding: 0 9px;
		gap: 32px;
	}

	.card__ending {
		left: 35%;
	}

	.status-icon {
		width: 36px;
		height: 36px;
		position: absolute;
		top: -18px;
	}
</style>