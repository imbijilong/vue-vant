<template>
  <div class="home">
    <div class="demo-block">
      <!-- <img class="demo-img" v-for="(img, index) in imageList" v-lazy="img" :key="index"> -->
      <img class="demo-img" />
    </div>
    <van-form @submit="onSubmit" validate-first @failed="onFailed">
      <div class="addressTitle">
        <div class="third-div">
          <div class="fill-in">
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address1" input-align="center" />
              </van-cell-group>
            </div>
            <div class="text-info">县(市、区)</div>
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address2" input-align="center" />
              </van-cell-group>
            </div>
            <div class="text-info">乡(镇、街道)</div>
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address3" input-align="center" />
              </van-cell-group>
            </div>
            <div class="text-info">村(居)委会</div>
          </div>
          <div class="fill-in">
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address4" input-align="center" />
              </van-cell-group>
            </div>
            <div class="text-info">普查小区</div>
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address5" input-align="center" />
              </van-cell-group>
            </div>
            <div class="text-info">户编号</div>
          </div>
        </div>
      </div>
      <div class="h1">
        <div class="first-title">一、住户项目</div>
        <div class="second-title">
          <span class="title">H1.</span> 户别
        </div>
        <div class="third-div">
          <van-radio-group v-model="radio" direction="horizontal">
            <van-radio name="1" checked-color="#323233">
              <div class="radio-text">1. 家庭户</div>
            </van-radio>
            <van-radio name="2" checked-color="#323233">
              <div class="radio-text">2. 集体户</div>
            </van-radio>
          </van-radio-group>
        </div>
      </div>
      <div class="h2">
        <div class="second-title">H2. 本户应登记人数</div>
        <div class="third-div">
          <div class="fill-in">
            <div class="text-info">2020年10月31日晚居住本户的人数</div>
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address6" input-align="center" :rules="[{ pattern, message: '请输入正确内容' }]"/>
              </van-cell-group>
            </div>
            <div class="text-info">人</div>
          </div>
          <div class="fill-in">
            <div class="text-info">户口在本户，2020年10月31日晚未住本户的人数</div>
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address7" input-align="center" />
              </van-cell-group>
            </div>
            <div class="text-info">人</div>
          </div>
        </div>
      </div>
      <div class="h3">
        <div class="second-title">H3. 本户2019年11月1日至2020年10月31日期间的出生人口</div>
        <div class="levelthird-div">
          <div class="levelfill-in">
            <div class="text-info">男</div>
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address8" input-align="center" />
              </van-cell-group>
            </div>
            <div class="text-info">人</div>
          </div>
          <div class="levelfill-in">
            <div class="text-info">女</div>
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address9" input-align="center" />
              </van-cell-group>
            </div>
            <div class="text-info">人</div>
          </div>
        </div>
      </div>
      <div class="h4">
        <div class="second-title">H4. 本户2019年11月1日至2020年10月31日期间的死亡人口</div>
        <div class="levelthird-div">
          <div class="levelfill-in">
            <div class="text-info">男</div>
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address10" input-align="center" />
              </van-cell-group>
            </div>
            <div class="text-info">人</div>
          </div>
          <div class="levelfill-in">
            <div class="text-info">女</div>
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address11" input-align="center" />
              </van-cell-group>
            </div>
            <div class="text-info">人</div>
          </div>
        </div>
      </div>
      <div class="h5">
        <div class="second-title">H5. 住房类型</div>
        <div class="third-div">
          <van-radio-group v-model="radioh5" direction="horizontal">
            <div class="h5radio">
              <div>
                <van-radio name="1" checked-color="#323233" @click="radioh5Checded(radioh5)">
                  <div class="radio-text">1. 普通住房</div>
                </van-radio>
              </div>
              <div>
                <van-radio name="2" checked-color="#323233" @click="radioh5Checded(radioh5)">
                  <div class="radio-text">2. 商住公寓</div>
                </van-radio>
              </div>
            </div>
            <div class="h5radio3">
              <van-radio name="3" checked-color="#323233" @click="radioh5Checded(radioh5)">
                <div class="radio-text">
                  3.
                  <span class="h5radio3Span">集体住所(学生宿舍、职工宿舍、工棚、养老院、福利院、旅馆、宗教机构等)</span>
                </div>
              </van-radio>
            </div>
            <div class="h5radio">
              <van-radio name="4" checked-color="#323233" @click="radioh5Checded(radioh5)">
                <div class="radio-text">4. 其他住所</div>
              </van-radio>
              <van-radio name="5" checked-color="#323233" @click="radioh5Checded(radioh5)">
                <div class="radio-text">5. 非居住房屋</div>
              </van-radio>
            </div>
            <div class="h5radio">
              <van-radio name="6" checked-color="#323233" @click="radioh5Checded(radioh5)">
                <div class="radio-text">6. 无住房</div>
              </van-radio>
            </div>
          </van-radio-group>
        </div>
      </div>
      <div v-show="h6h7model">
        <div class="h6">
          <div class="second-title">H6. 本户住房建筑面积</div>
          <div class="levelthird-div">
            <div class="levelfill-in">
              <div class="text-info">
                <van-cell-group>
                  <van-field v-model="address12" input-align="center" />
                </van-cell-group>
              </div>
              <div class="text-info">平方米</div>
            </div>
          </div>
        </div>
        <div class="h7">
          <div class="second-title">H7. 本户住房间数</div>
          <div class="levelthird-div">
            <div class="levelfill-in">
              <div class="text-info">
                <van-cell-group>
                  <van-field v-model="address13" input-align="center" />
                </van-cell-group>
              </div>
              <div class="text-info">间</div>
            </div>
          </div>
        </div>
      </div>

      <div class="d1">
        <div class="first-title">二、个人项目</div>
        <div class="second-title">D1. 姓名</div>
        <div class="levelthird-div">
          <div class="levelfill-in">
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address14" input-align="center" />
              </van-cell-group>
            </div>
          </div>
        </div>
      </div>

      <div class="d2">
        <div class="second-title">D2. 与户主关系</div>
        <div class="third-div">
          <van-radio-group v-model="radio2" direction="horizontal">
            <div class="h5radio">
              <div>
                <van-radio name="0" checked-color="#323233">
                  <div class="radio-text">0. 户主</div>
                </van-radio>
              </div>
              <div>
                <van-radio name="1" checked-color="#323233">
                  <div class="radio-text">1. 配偶</div>
                </van-radio>
              </div>
            </div>
            <div class="h5radio">
              <van-radio name="2" checked-color="#323233">
                <div class="radio-text">2. 子女</div>
              </van-radio>
              <van-radio name="3" checked-color="#323233">
                <div class="radio-text">3. 父母</div>
              </van-radio>
            </div>
            <div class="h5radio">
              <van-radio name="4" checked-color="#323233">
                <div class="radio-text">4. 岳父母或公婆</div>
              </van-radio>
              <van-radio name="5" checked-color="#323233">
                <div class="radio-text">5. 祖父母</div>
              </van-radio>
            </div>
            <div class="h5radio">
              <van-radio name="6" checked-color="#323233">
                <div class="radio-text">6. 媳婿</div>
              </van-radio>
              <van-radio name="7" checked-color="#323233">
                <div class="radio-text">7. 孙子女</div>
              </van-radio>
            </div>
            <div class="h5radio">
              <van-radio name="8" checked-color="#323233">
                <div class="radio-text">8. 兄弟姐妹</div>
              </van-radio>
              <van-radio name="9" checked-color="#323233">
                <div class="radio-text">9. 其他</div>
              </van-radio>
            </div>
          </van-radio-group>
        </div>
      </div>
      <!-- <div class="d3">
      <div class="second-title">D3. 公民身份号码</div>
      <div class="levelthird-div">
        <div class="levelfill-in">
          <div class="text-info">
            <van-cell-group>
              <van-field v-model="address15" input-align="center" />
            </van-cell-group>
          </div>
        </div>
      </div>
      </div>-->
      <div class="d3">
        <div class="second-title">D3. 公民身份号码</div>
        <div class="vanCell right-error">
          <van-field
            v-model="idCardNo"
            input-align="center"
            :error-message="errMsg.idCardNo"
            @blur="onBlurCheckCard"
          />
        </div>
      </div>
      <div class="d4">
        <div class="second-title">
          <span class="title">D4.</span> 性别
        </div>
        <div class="third-div">
          <van-radio-group v-model="radio" direction="horizontal">
            <van-radio name="1" checked-color="#323233">
              <div class="radio-text">1. 男</div>
            </van-radio>
            <van-radio name="2" checked-color="#323233">
              <div class="radio-text">2. 女</div>
            </van-radio>
          </van-radio-group>
        </div>
      </div>
      <div class="d5">
        <div class="second-title">D5. 出生年月</div>
        <div class="levelthird-div">
          <div class="levelfill-in">
            <div class="text-info">出生于</div>
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address16" input-align="center" />
              </van-cell-group>
            </div>
            <div class="text-info">年</div>
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address17" input-align="center" />
              </van-cell-group>
            </div>
            <div class="text-info">月</div>
          </div>
        </div>
      </div>
      <div class="d6">
        <div class="second-title">D6. 民族</div>
        <div class="levelthird-div">
          <div class="levelfill-in">
            <div class="text-info">
              <van-cell-group>
                <van-field v-model="address18" input-align="center" />
              </van-cell-group>
            </div>
            <div class="text-info">族</div>
          </div>
        </div>
      </div>
      <div class="d7">
        <div class="second-title">D7. 普查时点居住地</div>
        <div class="third-div">
          <van-radio-group v-model="radio2">
            <div class="d7radio">
              <van-radio name="0" checked-color="#323233">
                <div class="radio-text">1. 本普查小区</div>
              </van-radio>
            </div>
            <div class="d7radio">
              <van-radio name="1" checked-color="#323233">
                <div class="radio-text">2. 本村(居)委会其他普查小区</div>
              </van-radio>
            </div>
            <div class="d7radio">
              <van-radio name="2" checked-color="#323233">
                <div class="radio-text">3. 本乡(镇、街道)其他村(居)委会</div>
              </van-radio>
            </div>
            <div class="d7radio">
              <van-radio name="3" checked-color="#323233">
                <div class="radio-text">4. 本县(市、区)其他乡(镇、街道)</div>
              </van-radio>
            </div>

            <div class="radioFive">5. 其他县(市、区)，请填写下面地址</div>
            <div class="third-div">
              <div class="fill-in">
                <div class="text-info">
                  <van-cell-group>
                    <van-field v-model="address19" input-align="center" />
                  </van-cell-group>
                </div>
                <div class="text-info">省(区、市)</div>
              </div>
              <div class="fill-in">
                <div class="text-info">
                  <van-cell-group>
                    <van-field v-model="address20" input-align="center" />
                  </van-cell-group>
                </div>
                <div class="text-info">地(市)</div>
              </div>
              <div class="fill-in">
                <div class="text-info">
                  <van-cell-group>
                    <van-field v-model="address21" input-align="center" />
                  </van-cell-group>
                </div>
                <div class="text-info">县(市、区)</div>
              </div>
            </div>
            <div class="d7radio">
              <van-radio name="6" checked-color="#323233">
                <div class="radio-text">6. 港澳台或国外</div>
              </van-radio>
            </div>
          </van-radio-group>
        </div>
      </div>
      <div class="d8">
        <div class="second-title">D8. 户口登记地</div>
        <div class="third-div">
          <van-radio-group v-model="radiod8">
            <div class="d8radio">
              <van-radio
                name="1"
                checked-color="#323233"
                clickable
                @click="radiod8Checded(radiod8)"
              >
                <div class="radio-text">1. 本村(居)委会</div>
              </van-radio>
            </div>
            <div class="d8radio">
              <van-radio
                name="2"
                checked-color="#323233"
                clickable
                @click="radiod8Checded(radiod8)"
              >
                <div class="radio-text">2. 本乡(镇、街道)其他村(居)委会</div>
              </van-radio>
            </div>
            <div class="d8radio">
              <van-radio
                name="3"
                checked-color="#323233"
                clickable
                @click="radiod8Checded(radiod8)"
              >
                <div class="radio-text">3. 本县(市、区)其他乡(镇、街道)</div>
              </van-radio>
            </div>
            <div class="radioFive">4. 其他县(市、区)，请填写下面地址</div>
            <div class="third-div">
              <div class="fill-in">
                <div class="text-info">
                  <van-cell-group>
                    <van-field v-model="address22" input-align="center" />
                  </van-cell-group>
                </div>
                <div class="text-info">省(区、市)</div>
              </div>
              <div class="fill-in">
                <div class="text-info">
                  <van-cell-group>
                    <van-field v-model="address23" input-align="center" />
                  </van-cell-group>
                </div>
                <div class="text-info">地(市)</div>
              </div>
              <div class="fill-in">
                <div class="text-info">
                  <van-cell-group>
                    <van-field v-model="address24" input-align="center" />
                  </van-cell-group>
                </div>
                <div class="text-info">县(市、区)</div>
              </div>
            </div>
            <div class="d8radio">
              <van-radio name="5" checked-color="#323233" @click="radiod8Checded(radiod8)">
                <div class="radio-text">5. 户口待定</div>
              </van-radio>
            </div>
          </van-radio-group>
        </div>
      </div>
      <div v-show="d9d10model">
        <div class="d9">
          <div class="second-title">D9. 离开户口登记地时间</div>
          <div class="third-div">
            <van-radio-group v-model="radiod9" direction="horizontal">
              <div class="h5radio">
                <div>
                  <van-radio name="1" checked-color="#323233" @click="radiod9Checded(radiod9)">
                    <div class="radio-text">1. 没有离开户口登记地</div>
                  </van-radio>
                </div>
                <div>
                  <van-radio name="2" checked-color="#323233" @click="radiod9Checded(radiod9)">
                    <div class="radio-text">2. 不满半年</div>
                  </van-radio>
                </div>
              </div>
              <div class="h5radio">
                <van-radio name="3" checked-color="#323233" @click="radiod9Checded(radiod9)">
                  <div class="radio-text">3. 半年以上，不满一年</div>
                </van-radio>
                <van-radio name="4" checked-color="#323233" @click="radiod9Checded(radiod9)">
                  <div class="radio-text">4. 一年</div>
                </van-radio>
              </div>
              <div class="h5radio">
                <van-radio name="5" checked-color="#323233" @click="radiod9Checded(radiod9)">
                  <div class="radio-text">5. 二年</div>
                </van-radio>
                <van-radio name="6" checked-color="#323233" @click="radiod9Checded(radiod9)">
                  <div class="radio-text">6. 三年</div>
                </van-radio>
              </div>
              <div class="h5radio">
                <van-radio name="7" checked-color="#323233" @click="radiod9Checded(radiod9)">
                  <div class="radio-text">7. 四年</div>
                </van-radio>
                <van-radio name="8" checked-color="#323233" @click="radiod9Checded(radiod9)">
                  <div class="radio-text">8. 五年</div>
                </van-radio>
              </div>
              <div class="h5radio">
                <van-radio name="9" checked-color="#323233" @click="radiod9Checded(radiod9)">
                  <div class="radio-text">9. 六年及以上</div>
                </van-radio>
              </div>
            </van-radio-group>
          </div>
        </div>
        <div v-show="d10model">
          <div class="d10">
            <div class="second-title">D10. 离开户口登记地原因</div>
            <div class="third-div">
              <van-radio-group v-model="radioD10" direction="horizontal">
                <div class="h5radio">
                  <div>
                    <van-radio name="0" checked-color="#323233">
                      <div class="radio-text">0. 工作就业</div>
                    </van-radio>
                  </div>
                  <div>
                    <van-radio name="1" checked-color="#323233">
                      <div class="radio-text">1. 学习培训</div>
                    </van-radio>
                  </div>
                </div>
                <div class="h5radio">
                  <van-radio name="2" checked-color="#323233">
                    <div class="radio-text">2. 随同迁移</div>
                  </van-radio>
                  <van-radio name="3" checked-color="#323233">
                    <div class="radio-text">3. 房屋拆迁</div>
                  </van-radio>
                </div>
                <div class="h5radio">
                  <van-radio name="4" checked-color="#323233">
                    <div class="radio-text">4. 改善住房</div>
                  </van-radio>
                  <van-radio name="5" checked-color="#323233">
                    <div class="radio-text">5. 寄挂户口</div>
                  </van-radio>
                </div>
                <div class="h5radio">
                  <van-radio name="6" checked-color="#323233">
                    <div class="radio-text">6. 婚姻嫁娶</div>
                  </van-radio>
                  <van-radio name="7" checked-color="#323233">
                    <div class="radio-text">7. 照料孙子女</div>
                  </van-radio>
                </div>
                <div class="h5radio">
                  <van-radio name="8" checked-color="#323233">
                    <div class="radio-text">8. 为子女就学</div>
                  </van-radio>
                  <van-radio name="9" checked-color="#323233">
                    <div class="radio-text">9. 其他</div>
                  </van-radio>
                </div>
              </van-radio-group>
            </div>
          </div>
        </div>
      </div>

      <div v-show="d11d12Model">
        <div class="d11">
          <div class="second-title">D11. 是否识字</div>
          <div class="third-div">
            <van-radio-group v-model="radio" direction="horizontal">
              <van-radio name="1" checked-color="#323233">
                <div class="radio-text">1. 是</div>
              </van-radio>
              <van-radio name="2" checked-color="#323233">
                <div class="radio-text">2. 否</div>
              </van-radio>
            </van-radio-group>
          </div>
        </div>
        <div class="d12">
          <div class="second-title">D12. 受教育程度</div>
          <div class="third-div">
            <van-radio-group v-model="radioD12" direction="horizontal">
              <div class="h5radio">
                <div>
                  <van-radio name="0" checked-color="#323233">
                    <div class="radio-text">1. 未上过学</div>
                  </van-radio>
                </div>
                <div>
                  <van-radio name="1" checked-color="#323233">
                    <div class="radio-text">2. 小学</div>
                  </van-radio>
                </div>
              </div>
              <div class="h5radio">
                <van-radio name="2" checked-color="#323233">
                  <div class="radio-text">3. 初中</div>
                </van-radio>
                <van-radio name="3" checked-color="#323233">
                  <div class="radio-text">4. 高中</div>
                </van-radio>
              </div>
              <div class="h5radio">
                <van-radio name="4" checked-color="#323233">
                  <div class="radio-text">5. 大学专科</div>
                </van-radio>
                <van-radio name="5" checked-color="#323233">
                  <div class="radio-text">6. 大学本科</div>
                </van-radio>
              </div>
              <div class="h5radio">
                <van-radio name="6" checked-color="#323233">
                  <div class="radio-text">7. 研究生</div>
                </van-radio>
              </div>
            </van-radio-group>
          </div>
        </div>
      </div>

      <div class="sidentifyInfo">
        <div>
          <!-- <van-cell-group> -->
          <van-field v-model="value" placeholder="请输入验证码" />
          <!-- </van-cell-group> -->
        </div>
        <div class="sidentify">
          <Sidentify></Sidentify>
        </div>
        <div class="sidentifyBut">
          <van-button type="primary" size="mini">看不清,下一张</van-button>
        </div>
      </div>

      <div class="sub">
        <van-button round block type="info" native-type="submit">提交</van-button>
      </div>
    </van-form>
    <tab-bar></tab-bar>
  </div>
</template>

<script>
import TabBar from "@/components/common/TabBar.vue";
import Sidentify from "@/components/common/SIdentify.vue"; //**引入验证码组件**
import helper from "@/mixins/helper";
import { mapState, mapActions } from "vuex";
export default {
  name: "home",
  mixins: [helper],
  components: {
    TabBar,
    Sidentify
  },
  data() {
    return {
      address1: "",
      address2: "",
      address3: "",
      address4: "",
      address5: "",
      address6: "",
      address7: "",
      address8: "",
      address9: "",
      address10: "",
      address11: "",
      address12: "",
      address13: "",
      address14: "",
      address15: "",
      address16: "",
      address17: "",
      address18: "",
      address19: "",
      address20: "",
      address21: "",
      address22: "",
      address23: "",
      address24: "",
      radio: "",
      value: "",
      radio2: "",
      radio3: "",
      radioD10: "",
      radioD12: "",
      radioh5: "",
      radiod8: "",
      radiod9: "",
      h6h7model: true,
      d9d10model: true,
      d10model: true,
      idCardNo: "", //居民身份证号
      errMsg: {
        idCardNo: ""
      },
      d11d12Model: "",
      sidentify: "", //验证码
       pattern: /^\d+$|^\d+[.]?\d+$/,
    };
  },
  computed: {
    ...mapState({
      imageList: state => state.example.imageList
    })
  },
  mounted() {
    this.queryImgList(data => {
      this.$toast(data.log);
    });
  },
  methods: {
    ...mapActions({
      queryImgList: "example/queryImgList"
    }),
    radioh5Checded: function(e) {
      if (e == "1" || e == "2") {
        this.h6h7model = true;
      } else {
        this.h6h7model = false; //H5.住房类型选择3-6的，跳至个人项目
      }
    },
    radiod8Checded: function(e) {
      if (e == "5") {
        this.d9d10model = false;
      } else {
        this.d9d10model = true; //D8. 户口登记地选择5 户口待定跳转至D11
      }
    },
    radiod9Checded: function(e) {
      if (e == "1") {
        this.d10model = false;
      } else {
        this.d10model = true; //D9. 离开户口登记地时间选择1 没有离开户口登记地，跳至至D11
      }
    },
    onBlurCheckCard() {
      const val = this.idCardNo.length;
      const iden = this.idCardNo;
      let sexNum = null;
      let sex = null;
      let birth = null;
      const myDate = new Date();
      const month = myDate.getMonth() + 1;
      const day = myDate.getDate();
      let age = 0;

      if (val === 18) {
        age = myDate.getFullYear() - iden.substring(6, 10) - 1;
        sexNum = iden.substring(16, 17);
        if (
          iden.substring(10, 12) < month ||
          (iden.substring(10, 12) === month && iden.substring(12, 14) <= day)
        )
          age++;
        birth =
          iden.substring(6, 10) +
          "-" +
          iden.substring(10, 12) +
          "-" +
          iden.substring(12, 14);
      } else if (val === 15) {
        age = myDate.getFullYear() - iden.substring(6, 8) - 1901;
        sexNum = iden.substring(13, 14);
        if (
          iden.substring(8, 10) < month ||
          (iden.substring(8, 10) === month && iden.substring(10, 12) <= day)
        )
          age++;
        birth =
          "19" +
          iden.substring(6, 8) +
          "-" +
          iden.substring(8, 10) +
          "-" +
          iden.substring(10, 12);
      } else {
        this.errMsg.idCardNo = "您的身份证号有误！请输入你真实的身份证号!";
        return false;
      }
      //sex的值需要根据情况而定1, '男'2, '女'3, '未知'
      if (sexNum % 2 === 0) {
        sexNum = 2;
        sex = "女";
      } else {
        sexNum = 1;
        sex = "男";
      }
      var birthTime = new Date(birth);
      //6周岁及以上（2014年10月31日以前出生）的人填报的项目
      var sixYearsOldEnd = new Date("2014-10-31");
      if (birthTime <= sixYearsOldEnd) {
        this.d11d12Model = true;
      } else {
        this.d11d12Model = false;
      }
      this.errMsg.idCardNo = "";
      return true;
    },
    onSubmit(values) {
      console.log("submit", values);
    },
    onFailed(errorInfo) {
      console.log('failed', errorInfo);
    },
  }
};
</script>

<style scoped lang="less">
.right-error {
  
}
.demo-block {
  padding: 0 15px 10px 15px;
  .demo-img {
    padding: 15px;
    width: 100%;
    height: 150px;
    margin: 10px 0 0;
    background-color: white;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
    background-size: 315px 250px;
    background-position: 15px;
    background-repeat: no-repeat;
    box-sizing: border-box;
  }
}
//带有输入框的信息竖向显示
.third-div {
  margin: 5px 0px 0px 20px;
  display: flex;
  flex-direction: column;
  //竖向显示的文本
  .fill-in {
    display: flex;
    flex-direction: row;
  }
  //输入框样式
  /deep/ .van-cell {
    padding: 0;
    width: 60px;
    height: 13px;
    line-height: 6px;
    background: #f0f0f0;
    border-bottom: 1px solid #000000;
  }
  //输入框字体大小
  /deep/ .van-field__control {
    font-size: 7px;
  }
}
//带有输入框的信息水平显示
.levelthird-div {
  margin: 5px 0px 0px 20px;
  display: flex;
  justify-content: flex-start;
  //水平显示的文本
  .levelfill-in {
    display: flex;
    justify-content: flex-start;
    width: 100px;
  }
  //输入框样式
  /deep/ .van-cell {
    padding: 0;
    width: 60px;
    height: 13px;
    line-height: 6px;
    background: #f0f0f0;
    border-bottom: 1px solid #000000;
  }
  //输入框字体大小
  /deep/ .van-field__control {
    font-size: 7px;
  }
}
//地址信息栏
.addressTitle {
  .third-div {
    margin-left: 10px;
    display: flex;
    flex-direction: column;
    //竖向显示的文本
    .fill-in {
      display: flex;
      flex-direction: row;
      margin-bottom: 10px;
    }
  }
}
//所有radio前面圈的样式
/deep/ .van-radio__icon .van-icon {
  display: block;
  // box-sizing: border-box;
  width: 5px;
  height: 5px;
  color: transparent;
  font-size: 0.8em;
  line-height: 5px;
  text-align: inherit;
  border: 1px solid #323233;
  margin: 9px 0 0 5px;
  border-color: #323233;
}
.h1 {
  margin-left: 10px;
  height: 80px;
}
.h2 {
  margin-left: 10px;
  height: 60px;
}
.h3,
.h4,
.h6,
.h7 {
  margin-left: 10px;
  height: 50px;
}
.h5 {
  margin-left: 10px;
  height: 140px;
  .h5radio {
    display: flex;
    margin-bottom: 10px;
  }
  .h5radio3 {
    white-space: nowrap;
    margin-bottom: 10px;
    .van-radio {
      height: 20px;
      width: 312px;
      border-radius: 3px;
    }
    .h5radio3Span {
      font-size: 7px;
      white-space: nowrap;
    }
  }
}
.d1 {
  margin-left: 10px;
  height: 65px;
}
.d2,
.d9,
.d10 {
  margin: 20px 0 0 10px;
  height: 180px;
  .h5radio {
    display: flex;
    margin-bottom: 10px;
  }
}
.d3 {
  margin: 0 0 0 10px;
  height: 40px;
  //输入框样式
  .vanCell {
    margin-left: 20px;
    .van-cell {
      padding: 1px;
      background: #f0f0f0;
      width: 120px;
      /deep/ .van-field__control {
        border-bottom: 1px solid #000000;
        font-size: 11px;
      }
      /deep/ .van-field__error-message {
        font-size: 7px;
        height: 20px;
      }
      //输入框字体大小
      /deep/ .van-field__control {
        font-size: 7px;
      }
    }
  }
}
.d4 {
  margin: 0 0 0 10px;
  height: 50px;
}
.d5 {
  margin: 0 0 0 10px;
  height: 50px;
  .levelthird-div {
    margin: 10px 0px 0px 20px;
    //水平显示的文本
    .levelfill-in {
      display: flex;
      justify-content: flex-start;
      width: 100px;
    }
  }
}
.d6 {
  margin: 0 0 0 10px;
  height: 40px;
  .levelthird-div {
    margin-left: 20px;
    //水平显示的文本
    .levelfill-in {
      display: flex;
      justify-content: flex-start;
      width: 100px;
    }
  }
}
.d7 {
  margin: 0 0 0 10px;
  height: 255px;
  .d7radio {
    margin-top: 10px;
  }
  .radioFive {
    font-size: 7px;
    margin-top: 10px;
  }
  .van-radio {
    height: 20px;
    width: 250px;
    border-radius: 3px;
  }
}
.d8 {
  margin: 0 0 0 10px;
  height: 215px;
  .d8radio {
    margin-top: 10px;
  }
  .radioFive {
    font-size: 7px;
    margin-top: 10px;
  }
  .van-radio {
    height: 20px;
    width: 250px;
    border-radius: 3px;
  }
}
.d11 {
  margin: 20px 0 0 10px;
  height: 38px;
}

.d12 {
  margin: 20px 0 0 10px;
  height: 220px;
  .h5radio {
    display: flex;
    margin-bottom: 10px;
  }
}
.sidentifyInfo {
 .van-cell {
    height: 40px;
    width: 150px;
  }
  margin-left: 28px;
  display: flex;
  justify-content: flex-start;
  .sidentifyBut{
    font-size: 7px;
    margin-left: 5px;
  }
  .sidentifyBut{
    margin-top: 18px;
  }
}
.sidentifyBut .van-button--mini {
  background-color: transparent;
  border-color: transparent;
  color: blue;
}
</style>

