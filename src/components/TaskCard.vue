<template>
	<div class="task_card my_style">
		<div>
			<h4>{{model.title}}</h4>
			<p>{{model.description}}</p>
		</div>
		<div>
			<button @click="emitOnDone" v-if="!model.status">Выполнить</button>
			<button @click="emitOnRemove" v-else>Удалить</button>
		</div>		

	</div>
</template>

<script>
export default {
  emits: ['emitOnDone', 'emitOnRemove'],
  props: {
    model: {
      required: true,
      default: {
        id: 0,
        title: 'Create video',
        description: 'And upload on YouTube',
        status: false
      }
    }
  },
	setup (props, {emit} ) {
    const emitOnDone = () => {
      emit('onDone')

    }

    const emitOnRemove = () => {
      emit('onRemove')

    }

		

		return {
      emitOnDone,
      emitOnRemove
    }
	}
}
</script>

<style  scoped>
.task_card{
  display: flex;
  justify-content: space-between;
  align-items: center;
}

</style>