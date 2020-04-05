<template>
<!-- VSCodeでは型をみてくれるようになった。しかしコンパイルエラーにはできない。 -->
<!-- またサジェストをしてくれるわけではない。 -->
<div>
  <p>TypedVue(html)</p>
  <p>value: {{ $props.value }}</p>
  <ul>
    <template v-for="(item, index) in $data.arr">
      <!-- ループ内の値の型もみてくれる -->
      <li :key="index">{{ item }}</li>
    </template>
  </ul>
</div>
</template>

<script lang="ts">
import { TypedVue, RecordPropsDefinition } from '@wintyo/typed-vue';

interface IProps {
  /** 値 */
  value: number;
  /** 日付 */
  date?: Date;
}

interface IData {
  /** 文字列 */
  str: string;
  /** リスト */
  arr: Array<number>;
}

export default TypedVue.typedExtend({
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
    // this直下のアクセスを禁止
    // this.date;
    // this.value;
    // this.str;
    // $props, $data経由でアクセスさせる
    this.$props.value;
    this.$props.date;
    this.$data.str;
  },
});
</script>

<style lang="scss" scoped>
//
</style>
