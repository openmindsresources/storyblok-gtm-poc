<template>
  <a
    v-editable="blok"
    class="w-full p-12 bg-[#f7f6fd] rounded-[5px] text-center"
    :href="blok.filename"
    :data-id="blok.id"
  >
  {{ blok.meta_data && blok.meta_data.title ? blok.meta_data.title : 'Download' }}
</a>
</template>

<script lang="ts"setup>
defineProps({ blok: Object });
</script>