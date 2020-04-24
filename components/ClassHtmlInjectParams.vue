<template>
<!-- VSCodeでは型をみてくれるようになった。しかしコンパイルエラーにはできない。 -->
<!-- またサジェストをしてくれるわけではない。 -->
<div>
  <p>$data, $props直定義クラス(html)</p>
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
import Vue from 'vue';
import { RecordPropsDefinition } from 'vue/types/options';
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

@Component({
  props: {
    value: { type: Number },
    date: { type: Date },
  } as RecordPropsDefinition<IProps>,
  data(): IData {
    return {
      str: 'hoge',
      arr: [1, 2],
    };
  },
})
export default class ClassHtml extends Vue {
  $props!: Readonly<IProps>;
  $data!: IData;

  created() {
    console.log(this.$props.value);
  }
}
</script>

<style lang="scss" scoped>
//
</style>
