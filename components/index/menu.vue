<template>
  <div class="m-menu">
    <dl 
      class="nav" 
      @mouseleave="mouseleave">
      <dt>全部分类</dt>
      <dd 
        v-for="(item,index) in menu" 
        :key="index" 
        @mouseenter="enter">
        <i :class="item.type"/>{{ item.name }}<span class="arrow"/>
      </dd>
    </dl>
    <div 
      v-if="kind" 
      class="detail" 
      @mouseenter="sover" 
      @mouseleave="sout">
      // 模块的循环
      <template v-for="(item,index) in curDetail.child">
        <h4 :key="index">{{ item.title }}</h4>
        <span 
          v-for="(v,index) in item.child" 
          :key="index">{{ v }}</span>
      </template>
    </div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        kind: "",
        meun: [{
          type: "food",
          name: "美食",
          child: [{
            title: "美食",
            child: ["代金券", "甜点饮品", "火锅", "自助餐", "小吃快餐"]
          }]
        }, {
          type: "takeout",
          name: "外卖",
          child: [{
            title: "外卖",
            child: ["美团外卖"]
          }]
        }, {
          type: "hotel",
          name: "酒店",
          child: [{
            title: "酒店星级",
            child: ["经济型", "舒适/三星", "高档/四星", "豪华/五星"]
          }]
        }]

      }
    },
    computed: {
      curDetail() {
        return this.menu.filter((item) => item.type === this.kind)
      }
    },
    methods: {
      mouseleave() {
        let self = this
        self._timer = setTimeout(() => {
          this.kind = ''
        }, 150)
      },
      enter(e) {
        this.kind = e.target.querySelector('i').className
      },
      sover() {
        clearTimeout(this._timer)
      },
      sout() {
        this.kind = ""
      }
    }
  }

</script>
