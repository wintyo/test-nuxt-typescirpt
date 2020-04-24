<template lang="pug">
div
  .block
    StandardPug(
      ref="comStandardPug"
      :value="10"
    )
  .block
    StandardHtml(
      ref="comStandardHtml"
      :value="100"
    )
  .block
    TypedVueHtml(
      com="comTypedVueHtml"
      :value="0"
    )
  .block
    ClassHtml(
      ref="comClassHtml"
      :value="5"
    )
  .block
    ClassHtmlInjectParams(
      ref="comClassHtmlInjectParams"
      :value="5"
    )
  .block
    ClassTypedVueHtml(
      ref="comClassTypedVueHtml"
      :value="5"
    )
  .block
    CompositionHtml(
      ref="comCompositionHtml"
      :value="0"
    )
</template>

<script lang="ts">
import Vue from 'vue';
import { Vue as IVue, VueConstructor as IVueConstructor } from 'vue/types/vue';

// components
import StandardPug from '@/components/StandardPug.vue';
import StandardHtml from '@/components/StandardHtml.vue';
import TypedVueHtml from '@/components/TypedVueHtml.vue';
import ClassHtml from '@/components/ClassHtml.vue';
import ClassHtmlInjectParams from '@/components/ClassHtmlInjectParams.vue';
import ClassTypedVueHtml from '@/components/ClassTypedVueHtml.vue';
import CompositionHtml from '@/components/CompositionHtml.vue';

interface IExtendedVue extends IVue {
  $refs: {
    comStandardPug: InstanceType<typeof StandardPug>;
    comStandardHtml: InstanceType<typeof StandardHtml>;
    comTypedVueHtml: InstanceType<typeof TypedVueHtml>;
    // クラスはそのまま指定できる
    comClassHtml: ClassHtml;
    // InstanceTypeの書き方でもできる
    // comClassHtml: InstanceType<typeof ClassHtml>;
    comClassHtmlInjectParams: ClassHtmlInjectParams;
    comClassTypedVueHtml: ClassTypedVueHtml;
    comCompositionHtml: InstanceType<typeof CompositionHtml>;
  }
}

export default (Vue as IVueConstructor<IExtendedVue>).extend({
  components: {
    StandardPug,
    StandardHtml,
    TypedVueHtml,
    ClassHtml,
    ClassHtmlInjectParams,
    ClassTypedVueHtml,
    CompositionHtml,
  },
  mounted() {
    this.$refs.comStandardPug;
    this.$refs.comClassHtml;
    this.$refs.comClassHtmlInjectParams.$props;
  },
});
</script>

<style lang="scss" scoped>
.block {
  padding: 10px;
  border: solid 1px #000;
}
</style>
