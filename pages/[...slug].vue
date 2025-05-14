<template>
  <StoryblokComponent v-if="story" :blok="story.content" />
</template>
<script setup>
import { ref, onMounted } from 'vue';

const { slug } = useRoute().params
    
const story = await useAsyncStoryblok(
    slug && slug.length > 0 ? slug.join('/') : 'home',
    { version: 'draft' }
)

const gtmContainerId = ref('');
const country = 'my';

async function fetchGtmContainerId() {
  try {
    const response = await fetch(`https://api.storyblok.com/v2/cdn/datasource_entries?datasource=configuration&token=${process.env.STORYBLOK_ACCESS_TOKEN}`);
    const data = await response.json();

    if (data.datasource_entries && data.datasource_entries.length > 0) {
      const gtmEntry = data.datasource_entries.find(entry => entry.name === country);

      if (gtmEntry) {
        gtmContainerId.value = gtmEntry.value;
      }
    }
  } catch (error) {
  }
}

await fetchGtmContainerId();

useHead(() => {
  const script_array = [];
  const noscript_array = [];

  if (gtmContainerId.value) {
    script_array.push({
      hid: 'gtm-head',
      innerHTML: `(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','${gtmContainerId.value}');`,
      type: 'text/javascript',
      async: true,
    });
  }

  if (gtmContainerId.value) {
    noscript_array.push({
      tagPosition: 'bodyOpen',
      innerHTML: `<iframe src="https://www.googletagmanager.com/ns.html?id=${gtmContainerId.value}" height="0" width="0" style="display:none;visibility:hidden"></iframe>`,
    });
  }

  return {
    script: script_array,
    noscript: noscript_array,
  }
});
</script>