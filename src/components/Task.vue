<template>
  <div id="li-task">
		<span>
			{{ taskIndex }} props taskData: {{ taskData }}
		</span>
  </div>
</template>

<script>
export default {
	props: ['taskData', 'taskIndex']
}
</script>

<style>

</style>
