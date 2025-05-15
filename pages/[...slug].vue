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
    slug && slug.length > 0 ? slug.join('/') : 'home',
    { version: 'draft' }
);

async function fetchGtmContainerId() {
  try {
    const response = await fetch(`https://api.storyblok.com/v2/cdn/datasource_entries?datasource=configuration&token=${process.env.STORYBLOK_ACCESS_TOKEN}`);
    const data = await response.json();

    if (data.datasource_entries && data.datasource_entries.length > 0) {
      const gtmEntry = data.datasource_entries.find(entry => entry.name === country);

      if (gtmEntry) {
        return gtmEntry.value;
      }

      return null;
    }
  } catch (error) {
    return null;
  }
}

const gtmContainerId = await fetchGtmContainerId();

useHead(() => {
  const script_array = [
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

  const link_array = [
    {
      rel: 'stylesheet',
      href: 'https://cdn.jsdelivr.net/npm/@phosphor-icons/web@2.1.1/src/regular/style.css',
    },
    {
      rel: 'stylesheet',
      href: 'https://cdn.jsdelivr.net/npm/@phosphor-icons/web@2.1.1/src/fill/style.css',
    }
  ];

  const noscript_array = [];
  
  if (gtmContainerId) {
    script_array.push({
      hid: 'gtm-head',
      innerHTML: `(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','${gtmContainerId}');`,
      type: 'text/javascript',
      async: true,
    });

    noscript_array.push({
      tagPosition: 'bodyOpen',
      innerHTML: `<iframe src="https://www.googletagmanager.com/ns.html?id=${gtmContainerId}" height="0" width="0" style="display:none;visibility:hidden"></iframe>`,
    });
  }

  return {
    script: script_array,
    noscript: noscript_array,
    link: link_array,
    bodyAttrs: {
      'x-data': '{ open: false }',
    },
  };
});
</script>