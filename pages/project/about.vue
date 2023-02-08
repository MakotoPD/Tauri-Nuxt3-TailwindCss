<template>
	<div class="container mx-auto text-gray-300 flex flex-col items-center">
		<div class="my-12">
			<p>About project:</p>
			<table class="border-collapse border-spacing-0 mt-3">
				<tbody>
					<tr>
						<td class="border px-2 py-1">app name</td>
						<td class="border px-2 py-1">{{ appName }}</td>
					</tr>
					<tr>
						<td class="border px-2 py-1">tauri version</td>
						<td class="border px-2 py-1">{{ tauriVersion }}</td>
					</tr>
					<tr>
						<td class="border px-2 py-1">app version</td>
						<td class="border px-2 py-1">{{ appVersion }}</td>
					</tr>
					<tr>
						<td class="border px-2 py-1">Nuxt version</td>
						<td class="border px-2 py-1">3.1.2</td>
					</tr>
				</tbody>
			</table>
		</div>
	</div>
</template>
  
<script setup lang="ts">
import { getName, getTauriVersion, getVersion } from '@tauri-apps/api/app';
import { isPermissionGranted, requestPermission, sendNotification } from '@tauri-apps/api/notification';


definePageMeta({
  layout: "custom",
});

const appName = await getName();
const tauriVersion = await getTauriVersion();
const appVersion = await getVersion();


let notify = async ()  => {
	let permissionGranted = await isPermissionGranted();

	if (!permissionGranted) {
		const permission = requestPermission();
		isPermissionGranted = await permission === 'granted';
	}
	if (permissionGranted) {
		sendNotification({ title: 'TAURI & Nuxt3', body: 'Tauri with Nuxt3 are 🔥🔥' });
	}
}

</script>