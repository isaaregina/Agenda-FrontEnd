<template>
	<div>
		<header class="register">
			<Button
				label="Registre seus contatos"
				severity="warning"
				icon="pi pi-plus"
				class="btn-register"
				@click="enviar"
			/>

			<InputGroup :style="{ display: 'flex', width: '400px' }">
				<InputText placeholder="Procure o usuário desejado pelo e-mail" />
				<Button icon="pi pi-search" severity="warning" />
			</InputGroup>
		</header>

		<Dialog
			v-model:visible="visibleCardRegister"
			header="Registro de contatos"
			:style="{ width: '320px', height: '460px' }"
		>
			<div>
				<InputGroup class="inputgroup-card">
					<InputGroupAddon>
						<i class="pi pi-user"></i>
					</InputGroupAddon>
					<span class="p-float-label">
						<InputText id="inputgroup" type="text" v-model="name" />
						<label for="inputgroup">Nome</label>
					</span>
				</InputGroup>
			</div>
			<div>
				<InputGroup class="inputgroup-card">
					<InputGroupAddon>
						<i class="pi pi-book"></i>
					</InputGroupAddon>
					<span class="p-float-label">
						<InputText id="inputgroup" type="text" v-model="email" />
						<label for="inputgroup">Email</label>
					</span>
				</InputGroup>
			</div>
			<div>
				<InputGroup class="inputgroup-card">
					<InputGroupAddon>
						<i class="pi pi-phone"></i>
					</InputGroupAddon>
					<span class="p-float-label">
						<InputMask
							id="inputgroup"
							v-model="value"
							mask="(99) 9999-9999"
							placeholder="Telefone"
						/>
						<label for="inputgroup">Telefone</label>
					</span>
				</InputGroup>
			</div>

			<div class="btn-submit-register">
				<Button
					type="submit"
					@click="enviar"
					label="Registrar"
					severity="info"
					rounded
				/>
			</div>
		</Dialog>
	</div>

	<div>
		<DataTable :value="contacts" :style="{ margin: '0px 20px 0px 20px' }">
			<Column field="Name" header="Name"></Column>
			<Column field="Phone" header="Phone"></Column>
			<Column field="Email" header="E-mail"></Column>
			<Column header="Escolhas">
				<template #body="props">
					<Button
						icon="pi pi-trash"
						class="icons-escolhas"
						severity="danger"
						@click="deleteContact(props.data)"
					></Button>

					<Button
						icon="pi pi-pencil"
						class="icons-escolhas"
						severity="warning"
						@click="UpdateContact(props.data)"
					></Button>
				</template>
			</Column>
		</DataTable>
	</div>
</template>

<script setup>
	import { ref } from 'vue';
	import Button from 'primevue/button';
	import DataTable from 'primevue/datatable';
	import Column from 'primevue/column';
	import Dialog from 'primevue/dialog';
	import InputGroup from 'primevue/inputgroup';
	import InputGroupAddon from 'primevue/inputgroupaddon';
	import InputText from 'primevue/inputtext';
	import InputMask from 'primevue/inputmask';

	const visibleCardRegister = ref(false);
	const value2 = ref('');

	const contacts = ref([
		{ Name: 'John', Phone: '123-456-7890', Email: 'john@example.com' },
		{ Name: 'John', Phone: '123-456-7890', Email: 'john@example.com' },
		{ Name: 'John', Phone: '123-456-7890', Email: 'john@example.com' },
		{ Name: 'John', Phone: '123-456-7890', Email: 'john@example.com' },
	]);

	const enviar = () => {
		visibleCardRegister.value = true;
		console.log('Função enviar chamada!');
	};
</script>

<style scoped>
	.register {
		background-color: #17a2b8;
		height: 60px;
		display: flex;
		align-items: center;
	}

	.register .btn-register {
		margin: 0 30px 0 30px;
		/* #ffc107 */
	}

	.btn-submit-register {
		display: flex;
		justify-content: center;
	}

	.inputgroup {
		margin: 20px 0 40px 0;
	}

	.icons-escolhas {
		margin: 0 20px 0 0;
	}
</style>
