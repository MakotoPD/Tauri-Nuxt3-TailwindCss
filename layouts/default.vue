<template>
	<div>
		<div class="h-14 bg-gray-700 flex px-4 justify-between items-center mb-4">
			<div class="flex space-x-3 items-center">
				<NuxtLink to="/" class="text-white border border-gray-500 px-2 py-2 rounded-md font-semibold hover:text-gray-300"> home page </NuxtLink>
				<NuxtLink to="/about" class="text-white border border-gray-500 px-2 py-2 rounded-md font-semibold hover:text-gray-300"> about page </NuxtLink>
			</div>
			<div>
				<button @click="newWindow()" class="text-gray-300 border border-gray-500 px-2 py-2 rounded-md">About project</button>
			</div>
		</div>
		<slot />
	</div>
</template>

<script setup>
import { WebviewWindow } from '@tauri-apps/api/window';


let newWindow = () => {
	const webview = new WebviewWindow('About-tauri-project', {
		url: '/project/about',
		width:300,
		height:300,
		resizable: false,
		title: 'About tauri project'
	});
	webview.once('tauri://created', function () {
	// webview window successfully created
	});
	webview.once('tauri://error', function (e) {
	// an error happened creating the webview window
	});

}


</script>