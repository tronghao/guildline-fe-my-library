<template>
  <div class="mt-5">
    <div>
      <h4 class="font-bold">Utils</h4>
      <div class="grid grid-cols-5 gap-5 gap-y-[10rem] p-10">
        <div>
          <el-input v-model="input"></el-input>
          <el-checkbox v-model="select">select</el-checkbox>
          <div>
            Response: {{ getMinutes(input ? parseInt(input) : 5, select) }}
          </div>
          <div class="code mt-2 text-black">
            getMinutes(step = 5, select = false)
          </div>
        </div>
        <div>
          <el-input v-model="input"></el-input>
          <el-checkbox v-model="subName">subName</el-checkbox>
          <el-checkbox v-model="select">select</el-checkbox>
          <div>Response: {{ daysInMonth(input, subName, select) }}</div>
          <div class="code mt-2 text-black">
            daysInMonth(dateString, subName = true, select = false)
          </div>
          <div class="mt-2">Ex: 1990-01-01</div>
          <div>or New Date: {{ new Date() }}</div>
        </div>
        <div>
          <el-input v-model="input"></el-input>
          <div>Not Response</div>
          <div class="code mt-2 text-black">scrollToTop(top)</div>
          <div class="mt-2">
            <el-button
              type="primary"
              class="bg-[#409eff]"
              @click="scrollToTop(parseInt(input))"
              >Try</el-button
            >
          </div>
        </div>
        <div>
          <el-input v-model="input"></el-input>
          <div>Response: {{ formatDate(input) }}</div>
          <div class="code mt-2 text-black">formatDate(date)</div>
          <div class="mt-2">Ex: 1990-01-01</div>
          <div>or New Date: {{ new Date() }}</div>
        </div>
        <div>
          <el-input v-model="input"></el-input>
          <div>Response: {{ stripHtml(input) }}</div>
          <div class="code mt-2 text-black">stripHtml(html)</div>
          <div class="mt-2">
            Ex: {{ `
            <div><p>123</p></div>
            ` }}
          </div>
        </div>
        <div>
          <el-input v-model="input"></el-input>
          <div>Response: {{ checkOnlyNumber(input) ? "true" : "false" }}</div>
          <div class="code mt-2 text-black">checkOnlyNumber(string)</div>
        </div>
        <div>
          <el-input v-model="input"></el-input>
          <div>Response: {{ convertBase64(input) }}</div>
          <div class="code mt-2 text-black">convertBase64(val)</div>
        </div>
      </div>
    </div>
    <div>
      <h4 class="font-bold mt-[5rem]">Vue 3 - Component</h4>
      <div class="grid grid-cols-5 gap-5 gap-y-[10rem] p-10">
        <div>
          <el-checkbox v-model="loading">loading</el-checkbox>
          <div class="code mt-2 text-black">SpinnerV3</div>
          <SpinnerV3 :loading="loading"></SpinnerV3>
        </div>
      </div>
    </div>
  </div>
  <router-view />
</template>

<script>
import { reactive, toRefs } from "vue";

import {
  convertBase64,
  checkOnlyNumber,
  stripHtml,
  formatDate,
  scrollToTop,
  daysInMonth,
  getMinutes,
} from "@/module";
import { SpinnerV3 } from "@/module";

export default {
  components: {
    SpinnerV3,
  },
  setup() {
    const state = reactive({
      input: "",
      subName: false,
      select: false,
      loading: false,
    });

    return {
      ...toRefs(state),
      convertBase64,
      checkOnlyNumber,
      stripHtml,
      formatDate,
      scrollToTop,
      daysInMonth,
      getMinutes,
    };
  },
};
</script>

<style lang="scss">
.wrap-modules {
  overflow: hidden;
  img {
    transition: 0.3s;
  }
  &:hover {
    img {
      transform: scale(1.1);
    }
  }
}
.code {
  color: red;
}
</style>
