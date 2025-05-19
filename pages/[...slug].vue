<template>
  <div v-if="blok && blok.content" class="flex flex-col gap-4">
    <StoryblokComponent v-for="blok_item in blok.content.body" :key="blok_item._uid" :blok="blok_item"/>

    <!-- Chat Flutter Container -->
    <!-- <div class="fixed bottom-0 right-4">
      <button x-on:click="open = !open" class="fixed bottom-2 right-4 z-10 w-[50px] h-[50px] bg-blue-500 text-white rounded-full">
        <i class="ph ph-chat"></i>
      </button>
      <div id="chat-container" class="w-[400px] h-[500px] rounded-lg overflow-hidden mb-15" x-show="open"></div>
    </div> -->

    <!-- Chat Widget Web -->
    <div id="chat-widget-container" data-user-id="nsbs-user" data-backend-url="https://backend--nsbluescope-my.us-central1.hosted.app/api/chat/"></div>
  </div>
</template>
<script setup>
const { params } = useRoute();

const slug = params.slug && params.slug.length > 0 ? params.slug.join('/') : '';
    
const country = 'my';

const blok = await useAsyncStoryblok(slug, { version: 'draft' });

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
  ];

  // Install Chat Flutter
  // allScriptArray.push({
  //   src: 'https://nsbluescope-my.web.app/flutter_bootstrap.js',
  //   tagPosition: 'bodyClose',
  // });
  // allScriptArray.push({
  //   src: 'https://nsbluescope-my.web.app/chat.js',
  //   tagPosition: 'bodyClose',
  // });
  // allScriptArray.push({
  //   src: 'https://cdn.jsdelivr.net/npm/@phosphor-icons/web@2.1.1/src/regular/style.css',
  //   tagPosition: 'bodyClose',
  // });
  // allScriptArray.push({
  //   src: 'https://cdn.jsdelivr.net/npm/@phosphor-icons/web@2.1.1/src/fill/style.css',
  //   tagPosition: 'bodyClose',
  // });
  // allScriptArray.push({
  //   src: 'https://cdn.jsdelivr.net/npm/@phosphor-icons/web@2.1.1/src/regular/style.css',
  //   tagPosition: 'bodyClose',
  // });

  // Install ChatWidget
  allScriptArray.push({
    src: 'https://nsbs-chat-plugin.web.app/stream-chat-widget.js',
    tagPosition: 'bodyClose',
  });
  allScriptArray.push({
    hid: 'chatWidget',
    innerHTML: `
        document.addEventListener('alpine:init', () => {
            if (window.StreamAiChatWidget && window.StreamAiChatWidget.init) {
                window.StreamAiChatWidget.init('#chat-widget-container');
            }
        });`,
    type: 'text/javascript',
    tagPosition: 'bodyClose',
  });
  linkArray.push({
    rel: 'stylesheet',
    href: 'https://nsbs-chat-plugin.web.app/stream-chat-widget.css',
  });

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