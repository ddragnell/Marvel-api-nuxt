<template>
	<v-layout class="rounded rounded-md">

		<v-app-bar style="background-color:black;">
			<a href="https://developer.marvel.com" target="_blank">
					<v-img src="/marvel.png" alt="Página Marvel" width="200" style="margin-left: 300%;"/>
			</a>
		</v-app-bar>

	</v-layout>

	<main>
		<slot />

	</main>

</template>


<script setup>
</script>