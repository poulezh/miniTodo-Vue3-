<template>
	<div class="my_list task_input">
		<input v-model="title" placeholder="title" type="text">
		<input v-model="description" placeholder="desc" type="text">
		<button @click="onAddTask">Add Task</button>

	</div>
</template>

<script>
import {ref } from 'vue'
export default {
	emits: {
		//валидируем обьект
		onAddTask({title, description}){
			if(title === '' || description === ''){
				alert('Fill some info please')
				return false

			}
			return true
		}
	},
	setup (props, {emit}) {
		const title = ref('')
		const description = ref('')
		const onAddTask = () => {
			emit('onAddTask', { title: title.value, description: description.value})
			
		}
		

		return {
			title,
			description,
			onAddTask
		}
	}
}
</script>

<style scoped>
.task_input{
	margin: 10px 0;

}

</style>