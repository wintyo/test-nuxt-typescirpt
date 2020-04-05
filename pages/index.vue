<template lang="pug">
div
  .block
    StandardPug(
      :value="10"
    )
  .block
    StandardHtml(
      :value="100"
    )
  .block
    TypedVueHtml(
      :value="0"
    )
  .block
    ClassHtml(
      :value="5"
    )
  .block
    ClassTypedVueHtml(
      :value="5"
    )
</template>

<script lang="ts">
import StandardPug from '@/components/StandardPug.vue';
import StandardHtml from '@/components/StandardHtml.vue';
import TypedVueHtml from '@/components/TypedVueHtml.vue';
import ClassHtml from '@/components/ClassHtml.vue';
import ClassTypedVueHtml from '@/components/ClassTypedVueHtml.vue';

export default {
  components: {
    StandardPug,
    StandardHtml,
    TypedVueHtml,
    ClassHtml,
    ClassTypedVueHtml,
  },
}
</script>

<style lang="scss" scoped>
.block {
  padding: 10px;
  border: solid 1px #000;
}
</style>
