<script>
import { reactive } from 'vue'

export default {
	setup(){
		let user = reactive({
			nom: '',
			prenom: '',
			content: ''
		})
		let liste_commentaires = reactive([])

		function storeComment(){
			if(user.nom === '' || user.prenom === '' || user.content === ''){
				alert('Veuillez remplir tous les champs')
				return
			}
			liste_commentaires.push({
				user: {
					nom: user.nom,
					prenom: user.prenom,
					content: user.content
				}
			})
			user.nom = ''
			user.prenom = ''
			user.content = ''
		}
		return {
			user,
			liste_commentaires,
			storeComment
		}
	}
}



</script>

<template>
	<section>
		<div id="coms" v-for="item in liste_commentaires">
			<div>
				<h3>{{ item.user.prenom + " " + item.user.nom }}</h3>
				<p>{{ item.user.content }}</p>
			</div>
			<span class="sep"></span>
		</div>
	</section>
	<h2>Ecrire un commentaire</h2>

	<form @submit.prevent="storeComment()">
		<div>
			<label>Prénom: </label><br>
			<input id="input_pseudo" v-model="user.prenom" type="text">
		</div>
		<div>
			<label>Nom: </label><br>
			<input id="input_pseudo" v-model="user.nom" type="text"><br>
		</div>

		<div>
			<label>Votre commentaire: </label><br>
			<textarea id="text_area" v-model="user.content" cols="50" rows="5" maxlength="300"></textarea><br>
		</div>
		<button>Envoyer</button>
	</form>
</template>


<style scoped>
	h2{
		text-align: center;
		font-size: 2rem;
		margin: 50px 0;
	}
	section{
		display: flex;
		flex-direction: column;
		align-items: left;
		scrollbar-width: thin;
		margin-bottom: 50px;
	}
	#coms{
		font-family: 'Roboto';
		color: black;
		min-width: 20rem;
		max-width: 100%;
		min-height: 100px;
		margin: 20px;

		overflow: hidden;
	}
	.sep{
		display: block;
		width: 100%;
		height: 1px;
		background-color: grey;
		opacity: 0.3;
	}
	#coms div {
		margin: 30px;
	}
	#coms h3, p{
		text-align: left;
		font-weight: 300;
	}
	#coms h3{
		font-size: 1.2rem;
		margin-bottom: 20px;
	}
	#coms p{
		color: grey;
	}
	form{
		margin: 0 auto;
		display: flex;
		align-items: center;
		gap: 20px;
		flex-direction: column;
	}
	form label{
		text-align: left;
		font-weight: bold;
	}
	form input{
		font-size: 1.4rem;
		width: 60vw;
		height: 3rem;
		border-radius: 8px;
		border-style: solid;
		border-color: grey;

		padding: 10px;
	}
	form input::placeholder{
		font-size: 1.4rem;
	}
	form textarea{
		width: 60vw;
		font-size: 1.4rem;
		padding: 10px;
		border-radius: 10px;
		border-style: solid;
		border-color: grey;
	}
	form button{
		width: 10rem;
		height: 3rem;
		border-radius: 10px;
		border-style: solid;
		border-color: grey;
		margin: 10px auto;
		font-size: 1.5rem;
	}
</style>
