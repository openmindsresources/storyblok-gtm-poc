<template>
  <div>
    <StoryblokComponent v-if="story" :blok="story.content" />
    <!-- Chat Container -->
    <div class="fixed bottom-0 right-4">
      <button x-on:click="open = !open" class="fixed bottom-2 right-4 z-10 w-[50px] h-[50px] bg-blue-500 text-white rounded-full">
        <i class="ph ph-chat"></i>
      </button>
      <div id="chat-container" class="w-[400px] h-[500px] rounded-lg overflow-hidden mb-15" x-show="open"></div>
    </div>
  </div>
</template>
<script setup>
const { slug } = useRoute().params
    
const country = 'my';

const story = await useAsyncStoryblok(
    slug && slug.length > 0 ? slug.join('/') : '',
    { version: 'draft' }
);

async function fetchDataSourceValue(datasource, entryName) {  
  try {
    const { data } = await useStoryblokApi().get('cdn/datasource_entries', {
      datasource,
    });

    if (data.datasource_entries && data.datasource_entries.length > 0) {
      const entry = data.datasource_entries.find(entry => entry.name === entryName);
      if (entry) {
        return entry.value;
      }
      return null;
    }
  } catch (error) {
    return null;
  }
}

const gtmContainerId = await fetchDataSourceValue('gtm-containers', country);
const googleTagId = await fetchDataSourceValue('google-tags', country);

useHead(() => {
  const scriptArray = [];
  const noscriptArray = [];

  const linkArray = [
    {
      rel: 'stylesheet',
      href: 'https://cdn.jsdelivr.net/npm/@phosphor-icons/web@2.1.1/src/regular/style.css',
    },
    {
      rel: 'stylesheet',
      href: 'https://cdn.jsdelivr.net/npm/@phosphor-icons/web@2.1.1/src/fill/style.css',
    }
  ];

  if(googleTagId || gtmContainerId) {
    scriptArray.push({
      hid: 'dataLayer',
      innerHTML: `window.dataLayer = window.dataLayer || [];`,
      type: 'text/javascript',
    });
  }

  // Dynamically add scripts on the presence of googleTagId
  if (googleTagId) {
    scriptArray.push({
      src: `https://www.googletagmanager.com/gtag/js?id=${googleTagId}`,
    });

    scriptArray.push({
      hid: 'googleTagHead',
      innerHTML: `function gtag(){dataLayer.push(arguments);}
      gtag('js', new Date());
      gtag('config', '${googleTagId}');`,
      type: 'text/javascript',
    });
  }

  // Dynamically add scripts and noscripts based on the presence of gtmContainerId
  if (gtmContainerId) {
    scriptArray.push({
      hid: 'gtmHead',
      innerHTML: `(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','${gtmContainerId}');`,
      type: 'text/javascript',
      async: true,
    });

    noscriptArray.push({
      tagPosition: 'bodyOpen',
      innerHTML: `<iframe src="https://www.googletagmanager.com/ns.html?id=${gtmContainerId}" height="0" width="0" style="display:none;visibility:hidden"></iframe>`,
    });
  }

  const allScriptArray = [
    ...scriptArray,
    {
      src: 'https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4',
    },
    {
      src: '//unpkg.com/alpinejs',
      defer: true,
    },
    {
      src: 'https://nsbluescope-my.web.app/flutter_bootstrap.js',
      tagPosition: 'bodyClose',
    },
    {
      src: 'https://nsbluescope-my.web.app/chat.js',
      tagPosition: 'bodyClose',
    }
  ];

  return {
    script: allScriptArray,
    noscript: noscriptArray,
    link: linkArray,
    bodyAttrs: {
      'x-data': '{ open: false }',
    },
  };
});
</script>