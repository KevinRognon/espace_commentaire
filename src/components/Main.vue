<script>
import { reactive } from 'vue'

export default {
	setup(){
		let user = reactive({
			username: '',
			content: ''
		})
		let liste_commentaires = reactive([])

		function storeComment(){
			if(user.username == '' || user.content == ''){
				alert('Veuillez remplir tous les champs')
				return
			}
			liste_commentaires.push({
				user: {
					username: user.username,
					content: user.content
				}
			})
			user.username = ''
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
				<h3>{{ item.user.username }}</h3>
				<p>{{ item.user.content }}</p>
			</div>
		</div>
	</section>
	<h2>Ecrire un commentaire</h2>
	<form @submit.prevent="storeComment()">
		<label>Pseudonyme: </label><br>
		<input id="input_pseudo" v-model="user.username" type="text"><br>

		<label>Votre commentaire: </label><br>
		<textarea id="text_area" v-model="user.content" cols="50" rows="5" maxlength="300"></textarea><br>
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
		height: 400px;
		overflow-y: scroll;
		scrollbar-width: thin;
		margin-bottom: 50px;
	}
	#coms{
		font-family: 'Roboto';
		color: black;
		min-width: 20rem;
		max-width: 40rem;
		min-height: 100px;
		margin: 20px;

		overflow: hidden;
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
		display: flex;
		flex-direction: column;
		margin: 0 auto;
	}
	form label{
		text-align: left;
	}
	form input{
		font-size: 1.4rem;
		width: 40rem;
		height: 3rem;
		border-radius: 10px;
		border-style: solid;
		border-color: grey;

		padding: 10px;
	}
	form input::placeholder{
		font-size: 1.4rem;
	}
	form textarea{
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
