<template lang="html">
  <div class="ydc-release-content">
    <TabPanelRelease :tabs="tabs">
      <template slot="amount">
        <div class="ydc-release-amount">
          <span>
            今日发布数量：<em>0</em>
            /6 <a href="standard.html" target="_blank">发文规范</a>
          </span>
        </div>
      </template>
    <template slot="tab1">
      <div class="ydc-form-city">
        <form :action="SERVER+'api/publish'" enctype="multipart/form-data" method="post" ref="form">
          <input type="hidden" name="token" :value="token">
          <div class="ydc-release-form-group">
            <div class="ydc-warning-default">
              <p>标题字数需在11字到30字之间。</p>
            </div>
            <div class="ydc-release-form-group-input">
              <input
                type="text"
                class="ydc-form-control"
                name="title"
                placeholder="请输入标题，为了更好的展示效果，建议标题字数在30个汉字以内"
                />
              <div class="ydc-form-group-jl">
                <span id="messageCount">0</span>
                /30
              </div>
            </div>
          </div>
          <div class="ydc-release-form-text">
            <textarea name="content" style="width: 100%;">请输入内容
                        </textarea>
          </div>
          <div class="aui-card-form-item">
            <label class="aui-card-form-label">分类:</label>
            <div class="aui-card-form-input">
             <!-- <select name="catalogs" v-for="catalog,index in catalogs" :value="catalogs_selected[index]">
                <option v-for="item in catalog" :value="item.ID">{{item.title}}</option>
              </select>-->
              <!-- <select name="calalogs" v-for="catalog in catalogs">{{catalog}} -->
              <!-- <option value="" v-for="item in catalog" >{{item.title}}</option> -->
              <!-- </select> -->
              <select name="catalogs" v-for="catalog,index in catalogs" @change="catalog_change(index)">
                <option value="" v-for="item in catalog" :value="item.ID">{{item.title}}</option>
              </select>
              <select class="city">
                <option>请选择二级分类</option>
              </select>
              <select class="city" style="display:none">
                <option>互联网金融</option>
                <option>干货</option>
                <option>电子商务</option>
                <option>互联网+</option>
                <option>物联网</option>
              </select>
              <select class="city" style="display:none">
                <option>人机交互</option>
                <option>AR</option>
                <option>虚拟现实</option>
              </select>
              <select class="city" style="display:none">
                <option>收藏</option>
                <option>国学</option>
                <option>哲学</option>
                <option>民俗</option>
                <option>风水</option>
                <option>文学</option>
              </select>
              <select class="city" style="display:none">
                <option>新车</option>
                <option>用车</option>
                <option>汽车保养</option>
                <option>二手车</option>
                <option>新车评测</option>
                <option>试驾</option>
              </select>
              <select class="city" style="display:none">
                <option>电子竞技</option>
                <option>手游</option>
                <option>页游</option>
                <option>电视游戏</option>
              </select>
            </div>
          </div>
          <div class="aui-card-form-item preview aui-news">
            <label class="aui-card-form-label">封面:</label>
            <div class="aui-file-up-img" id="preview_0">
              <img class id="imghead_0" border="0" src="../assets/images/icon/noimg.gif" />
            </div>
            <div class="aui-file-up-btn clearfix">
              <div class="idPicFile aui-btn aui-file-new">
                <input
                  type="file"
                  name="cover"
                  class="file_photo aui-file-new-up"
                  style="margin:0;"
                />
                <a>上传图片</a>
              </div>
              <div class="aui-remarks">
                <p>图片尺寸建议：800*400 图片大小不超过1MB</p>
              </div>
            </div>
          </div>
          <div class="ydc-btn">
            <button class="btn"  type="button" @click="publish()">发布</button>
            <button  type="button" class="btn btn-default">保存草稿</button>
          </div>
        </form>
      </div>
    </template>
                <template slot="tab2">
  <div class="ydc-release-form-group">
    <div class="ydc-warning-default">
      <p>标题字数需在11字到30字之间。</p>
    </div>
    <div class="ydc-release-form-group-input clearfix">
      <label class="ydc-form-group-label">标题</label>
      <input
        style="width:89.999%"
        type="text"
        class="ydc-form-control"
        title
        placeholder="请输入标题，为了更好的展示效果，建议标题字数在30个汉字以内"
        onkeyUp="textLimitCheck(this, 30);"
      />
      <div class="ydc-form-group-jl">
        <span id="messageCount1">0</span>/30
      </div>
    </div>
    <div class="ydc-release-form-group-input ydc-release-form-group-ms clearfix">
      <label class="ydc-form-group-label">描述</label>
      <input
        style="width:89.999%"
        type="text"
        class="ydc-form-control"
        title
        placeholder="请输入描述，统一描述"
        onkeyUp
      />
      <div class="ydc-form-group-jl">
        <span id>0</span>/30
      </div>
    </div>
    <div class="aui-card-form-item preview aui-news" style="margin-top:20px;">
      <label class="aui-card-form-label">封面:</label>
      <div class="aui-file-up-img" id="preview_0">
        <img class id="imghead_0" border="0" src="../assets/images/icon/noimg.gif" />
      </div>
      <div class="aui-file-up-btn clearfix">
        <div class="idPicFile aui-btn aui-file-new">
          <input
            type="file"
            name="file"
            id="1"
            class="file_photo aui-file-new-up"
            style="margin:0;"
          />
          <a>上传图片</a>
        </div>
        <div class="aui-remarks">
          <p>图片尺寸建议：800*400 图片大小不超过1MB</p>
        </div>
      </div>
    </div>
    <div class="ydc-btn" style="margin-top:20px;">
      <button class="btn">发布</button>
      <button class="btn btn-default">保存草稿</button>
    </div>
  </div>
</template>
         </TabPanelRelease>   
    </div>
</template>
<script>
import TabPanelRelease from "@/components/tabPanelRelease";
import { SERVER } from "@/config";
import {fetch_form} from "@/lib/fetch"
export default {
  name: "release",
  methods:{
    async publish(){
      let form =this.$refs['form']
    let json = await fetch_form(form)
    console.log(json)
    },
    catalog_change(){
      // thsi.$refs
    }
  },
  data() {
    return {
      tabs: [
        { title: "发布文章", slotname: "tab1" },
        { title: "发布图集", slotname: "tab2" }
      ],
      catalogs: [
        [{"ID":1,"title":"互联网"},{"ID":2,"title":"汽车"},{"ID":3,"title":"生活"}],
        [{"ID":4,"title":"技术"},{"ID":5,"title":"产品"},{"ID":12,"title":"运营"}],
        [{"ID":6,"title":"前端技术"},{"ID":7,"title":"后端技术"}],
        [{"ID":8,"title":"Web"},{"ID":9,"title":"JS"}],
        [{"ID":10,"title":"java"},{"ID":11,"title":"php"}],
      ],
      catalogs_selected:[
        0,0,0,0,0
      ],
      SERVER,
      token:localStorage.token,
    };
  },
  components: {
    TabPanelRelease
  },
  async created() {
    //catalog
    {
      // let res = await fetch(SERVER + "api/publish_catalog");
      // let arr = await res.json();
      // this.catalogs = arr;
    }
  }
};
</script>
<style lang="css" scoped>
</style>