<template>
<!-- VSCodeでは型をみてくれるようになった。しかしコンパイルエラーにはできない。 -->
<!-- またサジェストをしてくれるわけではない。 -->
<div>
  <p>クラス(html)</p>
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
import { Component, Prop } from 'vue-property-decorator';

@Component({})
export default class ClassHtml extends Vue {
  /** 値 */
  @Prop({ type: Number })
  readonly value!: number;
  /** 日付 */
  @Prop({ type: Date })
  readonly date!: Date;

  /** 文字列 */
  str = 'hoge';
  /** リスト */
  arr = [1, 2, 3];
}
</script>

<style lang="scss" scoped>
//
</style>
