<!--
SPDX-FileCopyrightText: syuilo and other misskey contributors
SPDX-License-Identifier: AGPL-3.0-only
-->

<template>
	<div :class="$style.model">	
		<model-viewer 
			:src="modelUrl"
			poster="/client-assets/view-3dmodel.png"
			camera-controls
			loading="lazy"
			reveal="manual"
			@click="loadModel"
			@contextmenu.stop
			>
		</model-viewer>
  	</div>

</template>

<script lang="ts" setup>
import * as misskey from 'misskey-js';
import '@google/model-viewer';

const props = defineProps<{
	model: misskey.entities.DriveFile;
}>();

const modelUrl = $ref(props.model.url);

function loadModel(event) {
  const modelViewer = event.currentTarget;
  modelViewer.dismissPoster();
}

</script>

<style lang="scss" module>
.model {
	display: flex;
	justify-content: center;
	align-items: center;
	font-size: 3.5em;
	overflow: hidden;
	background-position: center;
	background-size: cover;
	width: 100%;
	height: 100%;
}

model-viewer {
      width: 100%;
      height: 340px;
}	

.menu {
	display: block;
	position: absolute;
	border-radius: 999px;
	background-color: rgba(0, 0, 0, 0.3);
	-webkit-backdrop-filter: var(--blur, blur(15px));
	backdrop-filter: var(--blur, blur(15px));
	color: #fff;
	font-size: 0.8em;
	width: 28px;
	height: 28px;
	text-align: center;
	bottom: 10px;
	right: 10px;
}


</style>
