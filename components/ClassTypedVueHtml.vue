<template>
<!-- VSCodeでは型をみてくれるようになった。しかしコンパイルエラーにはできない。 -->
<!-- またサジェストをしてくれるわけではない。 -->
<div>
  <p>TypedVueを継承したクラス(html)</p>
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
import { TypedVue, RecordPropsDefinition } from '@wintyo/typed-vue';
import { Component, Prop } from 'vue-property-decorator';

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

const baseVue = TypedVue.extend({
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
});

@Component({})
export default class ClassTypedVueHtml extends baseVue {
  created() {
    // 標準の型設定が入るため$dataはanyになる。。。
    this.$data.str;
    this.str;
  }
}
</script>

<style lang="scss" scoped>
//
</style>
