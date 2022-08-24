<template>
	<div id="app">
		<h1>Formulário Desafio</h1>
		<div class="conteudo">
			<form class="painel" v-if="!isSent">
				<div class="cabecalho">Formulário</div>
				<Rotulo nome="Nome Completo">
					<NomeCompleto v-model="fullName"/>
				</Rotulo>
				<Rotulo nome="E-mail">
					<input type="text" v-model="email">
				</Rotulo>
				<Rotulo nome="Senha">
					<input type="password" v-model="password">
				</Rotulo>
				<Rotulo nome="Armazenar dados?">
					<SwitchComp v-model="sData"/>
				</Rotulo>
				<button @click.prevent="sendData">Enviar</button>
			</form>
			<div class="painel" v-else>
				<div class="cabecalho">Resultado</div>
				<Rotulo nome="Nome Completo">
					<span>{{ fullName.name }} {{ fullName.surname }}</span>
				</Rotulo>
				<Rotulo nome="E-mail">
					<span>{{ email }}</span>
				</Rotulo>
				<Rotulo nome="Dados">
					<span>{{ sData.description }}</span>
				</Rotulo>
			</div>
		</div>
	</div>
</template>

<script>
import Rotulo from './components/Rotulo.vue'
import NomeCompleto from './components/NomeCompleto.vue'
import SwitchComp from './components/SwitchComp.vue'

export default {
	name: 'app',
	components: { Rotulo, NomeCompleto, SwitchComp },
	data(){
		return {
			fullName: {
				name: '',
				surname: ''
			},
			email: '',
			password: '',
			sData: {
				save: false,
				description: 'Dados não armazenados'
			},
			isSent: false
		}
	},
	methods: {
		sendData(){
			this.isSent = true
		}
	}
}
</script>

<style>

body {
	background-color: #ECECEC;
}

#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;

	display: flex;
	flex-direction: column;
}

.conteudo {
	display: flex;
}

.painel {
	flex: 1;
	background: #FFF;
	margin: 0px 10px;
	padding: 20px;
	border: 1px solid #AAA;
	border-radius: 5px;
}

.painel .cabecalho {
	width: 100%;
	background-color: #DDD;
	padding: 10px 0px;
	border-radius: 5px;
	font-size: 1.4rem;
}

#app form button {
	float: right;
	margin: 10px 0px;
	padding: 10px 20px;
	font-size: 1.4rem;
	border-radius: 5px;
	color: #FFF;
	background-color: #2196F3;
}

#app h1 {
	font-weight: 200;
	margin: 20px;
	padding: 0;
}

.mr-4 {
	margin-right: 40px;
}
</style>
