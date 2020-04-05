<template>
<!-- VSCodeでは型をみてくれるようになった。しかしコンパイルエラーにはできない。 -->
<!-- またサジェストをしてくれるわけではない。 -->
<div>
  <p>標準Vue.js(html)</p>
  <p>value: {{ value }}</p>
  <ul>
    <template v-for="(item, index) in arr">
      <!-- ループ内の値の型もみてくれる -->
      <li :key="index">{{ item }}</li>
    </template>
  </ul>
</div>
</template>

<script lang="ts">
import Vue from 'vue';
import { RecordPropsDefinition } from 'vue/types/options';

interface IProps {
  /** 値 */
  value: number;
  /** 日付 */
  date: Date;
}

interface IData {
  /** 文字列 */
  str: string;
  /** リスト */
  arr: Array<number>;
}

export default Vue.extend({
  props: {
    value: { type: Number },
    date: { type: Date },
  } as RecordPropsDefinition<IProps>,
  data(): IData {
    return {
      str: 'hoge',
      arr: [1, 2, 3],
    };
  },
  created() {
    // 全て型がつく
    this.date;
    this.value;
    this.str;
    // $dataはanyなので型チェックがまるでできないorz
    this.$data.value;
  },
});
</script>

<style lang="scss" scoped>
//
</style>
