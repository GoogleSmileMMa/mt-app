<template>
  <div class="exit"/>
</template>
<script>
	export default {
		layout:blank,
		middleware:async (ctx)=>{
			const {status,data} = await this.axios.get('/users/exit')
			if(status.code===200&&data&&data.code===0){
				window.location.href = '/'
			}
		}
	}
</script>