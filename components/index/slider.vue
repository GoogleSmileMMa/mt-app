<template>
  <div class="slider">
    <el-carousel height="240px">
      <el-carousel-item 
        v-for="item in list" 
        :key="item.img">
        <img :src="item.img">
      </el-carousel-item>
    </el-carousel>
  </div>
</template>
<script>
	export default {
		data(){
			return{
				list:[{
					url:'#abc',
					img:''
				},{
					url:'#bsbsb',
					img:''
				},{
					url:'#kdff',
					img:''
				},{
					url:'',
					img:''
				}]
			}
		}
	}
</script>