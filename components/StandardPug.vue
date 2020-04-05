<template lang="pug">
//- pugではVSCodeだとtype checkできない
div
  p 標準Vue.js(pug)
  p value: {{ value }}
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
}

export default Vue.extend({
  props: {
    value: { type: Number },
    date: { type: Date },
  } as RecordPropsDefinition<IProps>,
  data(): IData {
    return {
      str: 'hoge',
    };
  },
  created() {
    // 全て型がつく
    this.date;
    this.value;
    this.str;
    // $propsはanyなので型チェックがまるでできないorz
    this.$props.value;
  },
});

Vue.extend({
  props: {
    date: { type: Date },
  },
  created() {
    // Date型がstringと推論されてしまう・・・！
    this.date;
  },
});
</script>

<style lang="scss" scoped>
//
</style>
