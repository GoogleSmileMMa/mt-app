<template>
  <div class="search-panel">
    <el-row>
      <el-col 
        :span="3" 
        class="left">
        <img 
          src="" 
          alt="美团">
        <el-col>
          <el-col 
            :span="15" 
            class="center">
            <div class="wrapper">
              <el-input 
                v-model="serach" 
                placeholder="搜索商家或地点" 
                @focus="focus" 
                @blur="blur" 
                @input="input">
                <button class="el-button el-button-primary">
                  <i class="el-icon-serach"/>
                </button>
                <dl 
                  v-if="isHotPlace" 
                  class="hotPlace">
                  <dt 
                    v-for="(item,index) in hotPlace" 
                    :key="index">{{ item }}</dt>
                </dl>
                <dl 
                  v-if="isSearchList" 
                  class="searchList">
                  <dt 
                    v-for="(item,index) in serachList" 
                    :key="index">火锅</dt>
                </dl>
            </el-input></div>
            <p class="suggest">
              <a href="#">故宫博物院</a>
              <a href="#">故宫博物院</a>
              <a href="#">故宫博物院</a>
              <a href="#">故宫博物院</a>
            </p>
            <ul class="nav">
              <li><nuxt-link 
                to="/" 
                class="takeout">美团外卖</nuxt-link></li>
              <li><nuxt-link 
                to="/" 
                class="moive">猫眼电影</nuxt-link></li>
              <li><nuxt-link 
                to="/" 
                class="hotel">美团酒店</nuxt-link></li>
              <li><nuxt-link 
                to="/" 
                class="apartment">名宿/公寓</nuxt-link></li>
              <li><nuxt-link 
                to="/" 
                class="business">商家入驻</nuxt-link></li>
            </ul>
            <el-col>
              <e-col 
                :span="6" 
                class="right">
                <ul class="security">
                  <li><i class="refound"><p class="txt">随时退</p></i></li>
                  <li><i class="single"><p class="txt">不满意免单</p></i></li>
                  <li><i class="overdue"><p class="txt">过期退</p></i></li>
                </ul>
              </e-col>
    </el-col></el-col></el-col></el-col></el-row>
  </div>
</template>
<script>
	export default{
		data(){
			return {
				serach:"",
				isFocus:false,
				hotPlace:[],
				searchList:[]
			}
		},
		computed:{
			isHotPlace(){
				return this.isFocus&&!this.serach
			},
			isSearchList(){
				return this.isFocus&&this.serach
			}
		},
		methods:{
			focus(){
				this.isFocus = true;
			},
			blur(){
				setTimeout(()=>{
					this.isFocus = false;
				},200)
			},
			input(){
				
			}
		}
	}
</script>