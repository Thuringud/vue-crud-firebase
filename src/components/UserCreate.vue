<template>
	<div class="card card-body mt-4">
		<form @submit.prevent="onSubmit">
			<div class="form-group">
				<label>Имя</label>
				<input v-model="form.name" class="form-control" required>
			</div>

			<div class="form-group mt-3">
				<label>Почта</label>
				<input v-model="form.email" class="form-control" type="email" required>
			</div>

			<button type="submit" class="btn btn-success mt-3">
				Создать пользователя
			</button>
		</form>
	</div>
</template>

<script>
import {createUser} from '@/firebase'
import {reactive} from 'vue'

export default {
	setup() {
		const form = reactive({name: '', email: ''})

		const onSubmit = async () => {
			await createUser({...form})
			form.name = ''
			form.email = ''
		}

		return {form, onSubmit}
	}
}
</script>

<style scoped>

</style>