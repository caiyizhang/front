<template>
  <div class="common-layout">
    <el-container >
      <el-header>Header</el-header>
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
    <el-form-item label="地区" style="width: 1000px">
        <el-select
          v-model="pname"
          @change="choseProvince"
          placeholder="省级地区"
          style="width: 152px; margin-right: 5px"
        >
          <el-option
            v-for="(item, $index) in province"
            :key="$index"
            :label="item.value"
            :value="item.id"
          >
          </el-option>
        </el-select>
        <el-select
          style="width: 190px; margin-right: 5px"
          v-model="cname"
          @change="choseCity"
          placeholder="市级地区"
        >
          <el-option
            v-for="(item, $index) in city"
            :key="$index"
            :label="item.value"
            :value="item.id"
          >
          </el-option>
        </el-select>
        <el-select
          style="width: 170px"
          v-model="bname"
          @change="choseBlock"
          placeholder="区级地区"
        >
          <el-option
            v-for="(item, $index) in block"
            :key="$index"
            :label="item.value"
            :value="item.value"
          >
          </el-option>
        </el-select>
        <el-select  style="width: 152px; margin-right: 5px" placeholder="Select" size="large">
        </el-select>
            <el-button type="success" size="large">
              Success
            </el-button>
      </el-form-item>

    </el-form>

            
          </el-space>
          
            <div id="container"></div>
          </el-space>
          
          
        </el-main>
      </el-container>
    </el-container>
  </div>

</template>

<script>
import { ChineseDistricts } from '../api/xuanzhi'
export default {
  data() {
    return {
      ChineseDistricts: ChineseDistricts,
      province: [],
      shi1: [],
      qu1: [],
      city: [],
      block: [],
      pname: "", //省的名字
      cname: "", //市的名字
      bname: "", //区的名字
      mapInfo: {
        address: "上海市浦东新区周家渡街道毛家巷",//初始值默认
        lng: 121.517533,
        lat: 31.170182,
        lnglat: [121.517533, 31.170182],
      }, 
    };
  },
  methods: {
    // 加载china地点数据，三级
    getCityData: function () {
      let that = this;
      that.ChineseDistricts.forEach(function (item, index) {
        //省级数据
        that.province.push({
          id: item.code,
          value: item.name,
          children: item.children,
        });
      });
    },
    // 选省
    choseProvince: function (e) {
      let that = this;
      that.city = [];
      that.block = [];
      that.cname = "";
      that.bname = "";
      for (var index2 in that.province) {
        if (e === that.province[index2].id) {
          that.shi1 = that.province[index2].children;
          that.pname = that.province[index2].value;
          that.shi1.forEach(function (citem, cindex) {
            that.city.push({
              id: citem.code,
              value: citem.name,
              children: citem.children,
            });
          });
        }
      }
      console.log(that.pname);
    },
    // 选市
    choseCity: function (e) {
      let that = this;
      that.block = [];
      that.bname = "";
      for (var index3 in that.city) {
        if (e === that.city[index3].id) {
          that.qu1 = that.city[index3].children;
          that.cname = that.city[index3].value;
          that.E = that.qu1[0].id;
          that.qu1.forEach(function (bitem, bindex) {
            that.block.push({
              id: bitem.code,
              value: bitem.name,
              children: [],
            });
          });
        }
      }
      console.log(that.cname);
    },
    // 选区
    choseBlock: function (e) {
      this.bname = e;
      console.log(this.bname);
    },
  },
  mounted() {
    this.getCityData();
  },
};
</script>