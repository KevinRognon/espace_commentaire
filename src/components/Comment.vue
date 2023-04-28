<script setup>
import {ref} from 'vue'

const post = ref([
	{ id: 1, username: "Kevin", title: "Titre du commentaire", content: "Commentaire"}
])

defineProps(['post.username'])
</script>

<template>
	<div id="commentaire">
		<h2>{{ post.username }} a dit:</h2>
		<h3>{{ post.title }}</h3>
		<p>
			{{ post.content }}
		</p>
	</div>
</template>


<style>

</style>
