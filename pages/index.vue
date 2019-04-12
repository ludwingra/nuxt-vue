<template lang="html">
	<div class="container">
		<header>
				<h1 class="title">Albums de la página</h1>
		</header>

		<div class="columns is-multiline">
			<AlbumCard :album="album" v-for="album in albums" :key="album.id"></AlbumCard>
		</div>
	</div>
</template>

<script>

	import axios from 'axios';
	import env from '../config/env.js';
	import AlbumCard from '../components/AlbumCard';

export default {
	name: 'IndexPage',
	components: {
		AlbumCard: AlbumCard
	},
	data(){
		return {
			albums: []
		}
	},
	created: async function(){
		let res =  await axios.get(`${env.endpoint}/albums`);
		this.albums = res.data;
	}
}
</script>

<style scoped>

</style>
