<script setup lang="ts">
// import { isClient } from "@vueuse/core";
// import { fairyDustCursor } from "cursor-effects";

// translate
const { t } = useI18n()

// fullpage.js options
const options = {
  licenseKey: 'gplv3-license',
  anchors: ['home', 'projects', 'contact'],
  navigation: true,
  navigationTooltips: ['Home', 'Projects', 'Contact'],
  credits: {enabled: false},
}

// cursor effects
// if (isClient) {
  // new fairyDustCursor();
// }

function reloadOnce()
{
  if (typeof window !== 'undefined')
  // if( window.localStorage )
  {
    if( !localStorage.getItem('firstLoad') )
    {
      localStorage['firstLoad'] = true;
      window.location.reload();
    }  
    else
      localStorage.removeItem('firstLoad');
  }
}

reloadOnce();
</script>

<template>
  <div id="app">
    <ClientOnly>
    <full-page ref="fullpage" :options="options" id="fullpage">
      <div class="section">
        <Welcome></Welcome>
      </div>

      <div class="section">
        <h2 text-5xl font-700>{{ t('projects.title') }}</h2>
        <h3 text-3 pb-6>{{ t('projects.note') }}</h3>
        <ProjectsCarousel></ProjectsCarousel>
      </div>

      <div class="section">
        <Contact></Contact>
      </div>

    </full-page>
    </ClientOnly>
  </div>
</template>

<route lang="yaml">
meta:
  layout: home
</route>

<style>
</style>