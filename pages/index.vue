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
</template>

<script lang="ts">
import StandardPug from '@/components/StandardPug.vue';
import StandardHtml from '@/components/StandardHtml.vue';
import TypedVueHtml from '@/components/TypedVueHtml.vue';

export default {
  components: {
    StandardPug,
    StandardHtml,
    TypedVueHtml,
  },
}
</script>

<style lang="scss" scoped>
.block {
  padding: 10px;
  border: solid 1px #000;
}
</style>
