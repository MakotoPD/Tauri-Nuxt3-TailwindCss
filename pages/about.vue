<template>
	<div class="container mx-auto text-gray-300">
		<p>This page will be displayed at the /about route.</p>

		<button class="mt-4 px-4 py-2 rounded-lg bg-blue-500" @click="notify()">Check notification</button>
	</div>
</template>
  
<script setup lang="ts">
import { sendNotification } from '@tauri-apps/api/notification';

let notify = async ()  => {

	sendNotification({ title: 'TAURI & Nuxt3', body: 'Tauri with Nuxt3 are 🔥🔥' });

}

</script>