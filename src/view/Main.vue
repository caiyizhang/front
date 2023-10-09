<template>
  <div id="main" class="common-layout" ref="main">
    <el-container>
      <el-header class="header">
        <img :src="logo" class="image">
        <span >选址大师</span> 
      </el-header>
      <el-divider />
      <el-container>
        <el-aside width="200px" >
          
        <el-menu >
          <el-menu-item index="1">
            <template #title>
              1
            </template>
            
            
          </el-menu-item>
          <el-menu-item index="2">
            <template #title>
              2
            </template>
            
          </el-menu-item>
          <el-menu-item index="3">
            <template #title>
              3
            </template>
          </el-menu-item>
        </el-menu>
      
        </el-aside>
        <!--el-divider direction="vertical" /-->
        <el-main>
          <el-space direction="vertical" alignment="start" :size="30">
            <el-space spacer="  ">

              <el-form ref="form" label-width="85px">     
    
      <Select></Select>

      

    </el-form>

            
          </el-space>
          
          <Map></Map>
          
          </el-space>
          
          
        </el-main>
      </el-container>
    </el-container>
  </div>

  

  
</template>
  
  <script>
  import Select from '../components/Select.vue'
  import Map from '../components/Map.vue'
  import logo from '../assets/logo.png'
  export default {
    name: "Main",
    components: {
        Select,
        Map,
        
    },
    data () {
          return {
          logo
    }
  },
    mounted() {
      // this.$axios({
      //   method:'get',
      //   URL:'/xuanzhi/api/province',
      // })
      // .then((res)=>{
      //   console.log(JSON.stringify(res.data));
      // })
      // .catch(error => console.log(error))
      // this.$axios.get('/xuanzhi/api/province')
      // .then(res=>{
			// 	console.log(JSON.stringify(res.data.results));
			// })
      // .catch(error => console.log(error))

      // this.$axios.get('/xuanzhi/api/citys',{
      //   params:{
      //     province:'北京市'
      //   }
      // })
      // .then(res=>{
			// 	console.log(JSON.stringify(res.data));
			// })
      // .catch(error => console.log(error))
  },
  };
  </script>

<style>
  .image {
    margin-top: 1%;
    left: -30%;
    width: 40px;
    height: 40px;
  }
  
.amap-logo {
  display: none!important;
  visibility: hidden!important;
}
 
.amap-copyright {
  display: none!important;
  visibility: hidden!important;
}
.header {
  position: relative;

}
</style>