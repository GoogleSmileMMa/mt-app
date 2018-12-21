<template>
  <section>
    <dl @mouseover="over">
      <dt>有格调</dt><dd 
        :class="{active:kind==='all'}" 
        kind="all" 
        keyword="全部">
        全部
      </dd>
      <dd 
        :class="{active:kind==='part'}" 
        kind="part" 
        keyword="美食">
        约会聚餐
      </dd>
      <dd 
        :class="{active:kind==='spa'}" 
        kind="spa" 
        keyword="丽人">
        丽人spa
      </dd>
      <dd 
        :class="{active:kind==='movie'}" 
        kind="moive" 
        keyword="电影">
        电影演出
      </dd>
      <dd 
        :class="{active:kind==='travel'}" 
        kind="travel" 
        keyword="旅游">
        品质出游
      </dd>
    </dl>
    <ul>
      <li 
        v-for="item in cur" 
        :key="item.title">
        <el-card 
          :body-style="{padding:'0px'}" 
          shadow="never">
          <img 
            :src="item.img" 
            class="image">
          <ul>
            <li class="title">{{ item.title }}</li>
            <li class="pos"><span>{{ item.pos }}</span></li>
            <li class="price">￥<em>{{ item.price }}</em><span>/起</span></li>
          </ul>
        </el-card>
      </li>
    </ul>
  </section>
</template>
<script>
  export default {
    data() {
      return {
        kind: 'all',
      }
    }
  }

</script>
