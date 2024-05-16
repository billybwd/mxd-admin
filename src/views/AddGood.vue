<template>
  <div class="add">
    <el-card class="add-container">
      <el-form :model="state.goodForm" :rules="state.rules" ref="goodRef" label-width="100px" label-position="left" class="goodForm">
        <el-form-item required label="商品分类">
          <el-cascader :placeholder="state.defaultCate" style="width: 300px" :props="state.category" @change="handleChangeCate"></el-cascader>
        </el-form-item>
        <el-form-item label="商品名称" prop="goodsName">
          <el-input style="width: 300px" v-model="state.goodForm.goodsName" placeholder="请输入商品名称"></el-input>
        </el-form-item>
        <el-form-item label="商品简介" prop="goodsIntro">
          <el-input style="width: 300px" type="textarea" v-model="state.goodForm.goodsIntro" placeholder="请输入商品简介(100字)"></el-input>
        </el-form-item>
        <el-form-item label="商品价格" prop="originalPrice">
          <el-input type="number" min="0" style="width: 300px" v-model="state.goodForm.originalPrice" placeholder="请输入商品价格"></el-input>
        </el-form-item>
        <el-form-item label="商品售卖价" prop="sellingPrice">
          <el-input type="number" min="0" style="width: 300px" v-model="state.goodForm.sellingPrice" placeholder="请输入商品售价"></el-input>
        </el-form-item>
        <el-form-item label="商品库存" prop="stockNum">
          <el-input type="number" min="0" style="width: 300px" v-model="state.goodForm.stockNum" placeholder="请输入商品库存"></el-input>
        </el-form-item>
        <el-form-item label="商品标签" prop="tag">
          <el-input style="width: 300px" v-model="state.goodForm.tag" placeholder="请输入商品小标签"></el-input>
        </el-form-item>
        <el-form-item label="上架状态" prop="goodsSellStatus">
          <el-radio-group v-model="state.goodForm.goodsSellStatus">
            <el-radio label="0">上架</el-radio>
            <el-radio label="1">下架</el-radio>
          </el-radio-group>
        </el-form-item>
        <el-form-item label="区服" prop="serverArea" class="required">
      <el-select style="width: 300px" v-model="state.goodForm.serverArea" class="full-width-input" clearable>
        <el-option v-for="(item, index) in state.serverAreaOptions" :key="index" :label="item.label"
          :value="item.value" :disabled="item.disabled"></el-option>
      </el-select>
    </el-form-item>
       <el-form-item label="职业" prop="career">
      <el-checkbox-group v-model="state.goodForm.career">
        <el-checkbox v-for="(item, index) in state.careerOptions" :key="index" :label="item.value"
          :disabled="item.disabled" style="{display: inline}">{{item.label}}</el-checkbox>
      </el-checkbox-group>
    </el-form-item>   
        <el-form-item label="星力:" prop="starForce">
          <el-input style="width: 100px" v-model.number="state.goodForm.starForce" :clearable="true" placeholder="请输入" />
       </el-form-item>
        <el-form-item label="装备等级:" prop="reqLv">
          <el-input  style="width: 100px" v-model.number="state.goodForm.reqLv" :clearable="true" placeholder="请输入" />
       </el-form-item>	   
        <el-form-item label="力量:" prop="attStr">
          <el-input  style="width: 100px" v-model.number="state.goodForm.attStr" :clearable="true" placeholder="请输入" />
       </el-form-item>
        <el-form-item label="敏捷:" prop="attDex">
          <el-input  style="width: 100px" v-model.number="state.goodForm.attDex" :clearable="true" placeholder="请输入" />
       </el-form-item>
        <el-form-item label="智力:" prop="attInt">
          <el-input  style="width: 100px" v-model.number="state.goodForm.attInt" :clearable="true" placeholder="请输入" />
       </el-form-item>
        <el-form-item label="幸运:" prop="attLuk">
          <el-input  style="width: 100px" v-model.number="state.goodForm.attLuk" :clearable="true" placeholder="请输入" />
       </el-form-item>
       <el-form-item label="锤子:" prop="hammer">
          <el-input  style="width: 100px" v-model.number="state.goodForm.hammer" :clearable="true" placeholder="请输入" />
       </el-form-item>  
       <el-form-item label="潜能颜色" prop="potentialColor">
        <el-select  style="width: 200px" v-model="state.goodForm.potentialColor" class="full-width-input" clearable>
        <el-option v-for="(item, index) in state.potentialColorOptions" :key="index" :label="item.label"
          :value="item.value" :disabled="item.disabled"></el-option>
        </el-select>
       </el-form-item>
        <el-form-item label="潜能属性" prop="potentialQuality">
          <el-select  style="width: 200px" v-model="state.goodForm.potentialQuality" class="full-width-input" clearable>
            <el-option v-for="(item, index) in state.potentialQualityOptions" :key="index" :label="item.label"
              :value="item.value" :disabled="item.disabled"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="附加潜能颜色" prop="addPotentialColor">
          <el-select  style="width: 200px" v-model="state.goodForm.addPotentialColor" class="full-width-input" clearable>
            <el-option v-for="(item, index) in state.addPotentialColorOptions" :key="index" :label="item.label"
              :value="item.value" :disabled="item.disabled"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="附加潜能属性" prop="addPotentialQuality">
          <el-select  style="width: 200px" v-model="state.goodForm.addPotentialQuality" class="full-width-input" clearable>
            <el-option v-for="(item, index) in state.addPotentialQualityOptions" :key="index" :label="item.label"
              :value="item.value" :disabled="item.disabled"></el-option>
          </el-select>
        </el-form-item>	   
        <el-form-item label="联系方式:" prop="contact">
          <el-input v-model="state.goodForm.contact" :clearable="true"  placeholder="请输入联系方式" />
       </el-form-item>
        <el-form-item required label="商品主图" prop="goodsCoverImg">
          <el-upload
            class="avatar-uploader"
            :action="state.uploadImgServer"
            accept="jpg,jpeg,png"
            :headers="{
              token: state.token
            }"
            :show-file-list="false"
            :before-upload="handleBeforeUpload"
            :on-success="handleUrlSuccess"
          >
            <img style="width: 100px; height: 100px; border: 1px solid #e9e9e9;" v-if="state.goodForm.goodsCoverImg" :src="state.goodForm.goodsCoverImg" class="avatar">
            <el-icon v-else class="avatar-uploader-icon"><Plus /></el-icon>
          </el-upload>
        </el-form-item>
        <el-form-item label="详情内容">
          <div ref='editor'></div>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitAdd()">{{ state.id ? '立即修改' : '立即创建' }}</el-button>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script setup>
import { reactive, ref, onMounted, onBeforeUnmount, getCurrentInstance } from 'vue'
import WangEditor from 'wangeditor'
import axios from '@/utils/axios'
import { ElMessage } from 'element-plus'
import { useRoute, useRouter } from 'vue-router'
import { localGet, uploadImgServer, uploadImgsServer } from '@/utils'

const { proxy } = getCurrentInstance()
const editor = ref(null)
const goodRef = ref(null)
const route = useRoute()
const router = useRouter()
const { id } = route.query
const state = reactive({
  uploadImgServer,
  token: localGet('token') || '',
  id: id,
  defaultCate: '',
  goodForm: {
    goodsName: '',
    goodsIntro: '',
    originalPrice: '',
    sellingPrice: '',
    stockNum: '',
    goodsSellStatus: '0',
    goodsCoverImg: '',
    tag: '',
    serverArea: "",
    career: [],
    starForce: 0,
    reqLv: 0,
    attStr: 0,
    attDex: 0,
    attInt: 0,
    attLuk: 0,
    hammer: 0,
    potentialColor: "",
    potentialQuality: "",
    addPotentialColor: "",
    addPotentialQuality: "",
    contact: "",       
  },
  rules: {
    goodsName: [
      { required: 'true', message: '请填写商品名称', trigger: ['change'] }
    ],
    originalPrice: [
      { required: 'true', message: '请填写商品价格', trigger: ['change'] }
    ],
    sellingPrice: [
      { required: 'true', message: '请填写商品售价', trigger: ['change'] }
    ],
    stockNum: [
      { required: 'true', message: '请填写商品库存', trigger: ['change'] }
    ],
    serverArea: [
      { required: 'true', message: '请填写区服', trigger: ['change'] }
    ],    
  },
  serverAreaOptions: [{
          "value": "0",
          "label": "不限"
        }, {
          "value": "1",
          "label": "艾麗亞"
        }, {
          "value": "2",
          "label": "普利特"
        }, {
          "value": "3",
          "label": "琉德"
        }, {
          "value": "4",
          "label": "優依娜"
        }, {
          "value": "5",
          "label": "愛麗西亞"
        }, {
          "value": "6",
          "label": "杀人鲸"
        }],
        careerOptions: [{
          "label": "新手",
          "value": "1"
        }, {
          "label": "战士",
          "value": "2"
        }, {
          "label": "魔法师",
          "value": "3"
        }, {
          "value": "4",
          "label": "弓箭手"
        }, {
          "value": "5",
          "label": "飞侠"
        }, {
          "value": "6",
          "label": "海盗"
        }],
        potentialColorOptions: [{
          "value": "1",
          "label": "无"
        }, {
          "value": "2",
          "label": "无潜在能力"
        }, {
          "value": "3",
          "label": "特殊"
        }, {
          "value": "4",
          "label": "稀有"
        }, {
          "value": "5",
          "label": "罕见"
        }, {
          "value": "6",
          "label": "传说"
        }],
        potentialQualityOptions: [{
          "value": "1",
          "label": "无"
        }, {
          "value": "2",
          "label": "烂潜"
        }, {
          "value": "3",
          "label": "次次次"
        }, {
          "value": "4",
          "label": "次次顶"
        }, {
          "value": "5",
          "label": "次顶"
        }, {
          "value": "6",
          "label": "顶潜"
        }],
        addPotentialColorOptions: [{
          "value": "1",
          "label": "无"
        }, {
          "value": "2",
          "label": "无潜在能力"
        }, {
          "value": "3",
          "label": "特殊"
        }, {
          "value": "4",
          "label": "稀有"
        }, {
          "value": "5",
          "label": "罕见"
        }, {
          "value": "6",
          "label": "传说"
        }],
        addPotentialQualityOptions: [{
          "value": "1",
          "label": "无"
        }, {
          "value": "2",
          "label": "烂潜"
        }, {
          "value": "3",
          "label": "两排"
        }, {
          "value": "4",
          "label": "三排"
        }],        
  categoryId: '',
  category: {
    lazy: true,
    lazyLoad(node, resolve) {
      const { level = 0, value } = node
      axios.get('/categories', {
        params: {
          pageNumber: 1,
          pageSize: 1000,
          categoryLevel: level + 1,
          parentId: value || 0
        }
      }).then(res => {
        const list = res.list
        const nodes = list.map(item => ({
          value: item.categoryId,
          label: item.categoryName,
          leaf: level > 1
        }))
        resolve(nodes)
      })
    }
  }
})
let instance
onMounted(() => {
  instance = new WangEditor(editor.value)
  instance.config.showLinkImg = false
  instance.config.showLinkImgAlt = false
  instance.config.showLinkImgHref = false
  instance.config.uploadImgMaxSize = 4 * 1024 * 1024 // 4M
  instance.config.uploadFileName = 'file'
  instance.config.uploadImgHeaders = {
    token: state.token
  }
  // 图片返回格式不同，需要自定义返回格式
  instance.config.uploadImgHooks = {
    // 图片上传并返回了结果，想要自己把图片插入到编辑器中
    // 例如服务器端返回的不是 { errno: 0, data: [...] } 这种格式，可使用 customInsert
    customInsert: function(insertImgFn, result) {
      console.log('result', result)
      // result 即服务端返回的接口
      // insertImgFn 可把图片插入到编辑器，传入图片 src ，执行函数即可
      if (result.data && result.data.length) {
        result.data.forEach(item => insertImgFn(item))
      }
    }
  }
  instance.config.uploadImgServer = uploadImgsServer
  Object.assign(instance.config, {
    onchange() {
      console.log('change')
    },
  })
  instance.create()
  if (id) {
    axios.get(`/goods/${id}`).then(res => {
      const { goods, firstCategory, secondCategory, thirdCategory } = res
      state.goodForm = {
        goodsName: goods.goodsName,
        goodsIntro: goods.goodsIntro,
        originalPrice: goods.originalPrice,
        sellingPrice: goods.sellingPrice,
        stockNum: goods.stockNum,
        goodsSellStatus: String(goods.goodsSellStatus),
        goodsCoverImg: proxy.$filters.prefix(goods.goodsCoverImg),
        tag: goods.tag,
        serverArea: goods.serverArea,
        career: goods.career,
        starForce: goods.starForce,
        reqLv: goods.reqLv,
        attStr: goods.attStr,
        attDex: goods.attDex,
        attInt: goods.attInt,
        attLuk: goods.attLuk,
        hammer: goods.hammer,
        potentialColor: goods.potentialColor,
        potentialQuality: goods.potentialQuality,
        addPotentialColor: goods.addPotentialColor,
        addPotentialQuality: goods.addPotentialQuality,
        contact: goods.contact
      }
      state.categoryId = goods.goodsCategoryId
      state.defaultCate = `${firstCategory.categoryName}/${secondCategory.categoryName}/${thirdCategory.categoryName}`
      if (instance) {
        // 初始化商品详情 html
        instance.txt.html(goods.goodsDetailContent)
      }
    })
  }
})
onBeforeUnmount(() => {
  instance.destroy()
  instance = null
})
const submitAdd = () => {
  goodRef.value.validate((vaild) => {
    if (vaild) {
      // 默认新增用 post 方法
      let httpOption = axios.post
      let params = {
        goodsCategoryId: state.categoryId,
        goodsCoverImg: state.goodForm.goodsCoverImg,
        goodsDetailContent: instance.txt.html(),
        goodsIntro: state.goodForm.goodsIntro,
        goodsName: state.goodForm.goodsName,
        goodsSellStatus: state.goodForm.goodsSellStatus,
        originalPrice: state.goodForm.originalPrice,
        sellingPrice: state.goodForm.sellingPrice,
        stockNum: state.goodForm.stockNum,
        tag: state.goodForm.tag,
        serverArea: state.goodForm.serverArea,
        career: state.goodForm.career,
        starForce: state.goodForm.starForce,
        reqLv: state.goodForm.reqLv,
        attStr: state.goodForm.attStr,
        attDex: state.goodForm.attDex,
        attInt: state.goodForm.attInt,
        attLuk: state.goodForm.attLuk,
        hammer: state.goodForm.hammer,
        potentialColor: state.goodForm.potentialColor,
        potentialQuality: state.goodForm.potentialQuality,
        addPotentialColor: state.goodForm.addPotentialColor,
        addPotentialQuality: state.goodForm.addPotentialQuality,
        contact: state.goodForm.contact
      }
      console.log('params', params)
      if (id) {
        params.goodsId = id
        // 修改商品使用 put 方法
        httpOption = axios.put
      }
      httpOption('/goods', params).then(() => {
        ElMessage.success(id ? '修改成功' : '添加成功')
        router.push({ path: '/good' })
      })
    }
  })
}
const handleBeforeUpload = (file) => {
  const sufix = file.name.split('.')[1] || ''
  if (!['jpg', 'jpeg', 'png'].includes(sufix)) {
    ElMessage.error('请上传 jpg、jpeg、png 格式的图片')
    return false
  }
}
const handleUrlSuccess = (val) => {
  state.goodForm.goodsCoverImg = val.data || ''
}
const handleChangeCate = (val) => {
  state.categoryId = val[2] || 0
}
</script>

<style scoped>
  .add {
    display: flex;
  }
  .add-container {
    flex: 1;
    height: 100%;
  }
  .avatar-uploader {
    width: 100px;
    height: 100px;
    color: #ddd;
    font-size: 30px;
  }
  .avatar-uploader-icon {
    display: block;
    width: 100%;
    height: 100%;
    border: 1px solid #e9e9e9;
    padding: 32px 17px;
  }
</style>