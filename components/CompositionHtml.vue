<template>
<!-- VSCodeでは型をみてくれるようになった。しかしコンパイルエラーにはできない。 -->
<!-- またサジェストをしてくれるわけではない。 -->
<div>
  <p>Composition API(html)</p>
  <!-- propsの型推論がおかしい -->
  <p>value: {{ props.value }}</p>
  <ul>
    <template v-for="(item, index) in data.arr">
      <!-- ループ内の値の型もみてくれる -->
      <li :key="index">{{ item }}</li>
    </template>
  </ul>
</div>
</template>

<script lang="ts">
import { defineComponent, reactive } from '@vue/composition-api';

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

export default defineComponent({
  props: {
    value: { type: Number },
    date: { type: Date },
  },
  // 上のpropsの設定と合わせられない
  setup(props: IProps) {
    props.date;
    const data = reactive<IData>({
      str: 'hoge',
      arr: [1, 2, 3],
    });
    return {
      props,
      data,
    };
  },
});
</script>

<style lang="scss" scoped>
//
</style>
