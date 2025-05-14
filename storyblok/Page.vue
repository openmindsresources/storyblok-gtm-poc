<template>
  <div v-editable="blok" class="px-4">
    <noscript v-if="blok.gtm_container_id">
      <iframe v-bind:src="`https://www.googletagmanager.com/ns.html?id=${blok.gtm_container_id}`" height="0" width="0" style="display:none;visibility:hidden"></iframe>
    </noscript>
    <StoryblokComponent v-for="blok_item in blok.body" :key="blok_item._uid" :blok="blok_item" />
  </div>
</template>

<script setup>
const props = defineProps({ blok: Object });

useHead(() => {
  const script_array = [];
  const noscript_array = [];

  if (props.blok && props.blok.gtm_container_id) {
    script_array.push({
      hid: 'gtm-head',
      innerHTML: `(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','${props.blok.gtm_container_id}');`,
      type: 'text/javascript',
      async: true,
    });
  }

  if (props.blok && props.blok.gtm_container_id) {
    noscript_array.push({
      tagPosition: 'bodyOpen',
      innerHTML: `<iframe src="https://www.googletagmanager.com/ns.html?id=${props.blok.gtm_container_id}" height="0" width="0" style="display:none;visibility:hidden"></iframe>`,
    });
  }

  return {
    script: script_array,
    noscript: noscript_array,
  };
});
</script>
