---
theme: ./theme
title: "Gems of Nuxt: 8 Features Every Nuxt Developer Should Know!"
website: lichter.io
handle: TheAlexLichter
favicon: https://lichter.io/img/me@2x.jpg
highlighter: shiki
lineNumbers: true
layout: intro
transition: fade
---

---
layout: intro
preload: false
transition: none
---

<h1 class="mt-12 flex justify-center items-center" v-motion :initial="{ x: -500 }" :enter="{ x: 0, transition: { duration: 500 } }">

<logos-nuxt-icon class="text-10xl"/>

</h1>


---
layout: intro
preload: false
clicks: 1
---

<h1 class="mt-12">

<logos-nuxt-icon class="text-10xl transition ease-in-out animate-ping" style="animation: ping 2s cubic-bezier(0, 0, 0.2, 1) infinite !important"/>

</h1>

---
layout: intro
preload: false
transition: none
---

<h1 class="mt-12 flex justify-center items-center" v-motion :initial="{ y: 0 }" :enter="{ y: -500, transition: { duration: 1000 } }">

<logos-nuxt-icon class="text-10xl"/>

</h1>


---
layout: intro
---

# <noto-gem-stone /> Gems of <span class="text-[#41b883]">Nuxt</span> <noto-gem-stone />

## 8 Features <span class="text-[#41b883] font-semibold">Every Nuxt Developer</span> Should Know!

### VueConf US 2025

<style>

h2 {
  @apply !mt-16;
}

h3 {
  @apply !mt-32 !text-lg;
}
</style>

---
layout: two-cols
heading: About me
---

<template v-slot:default>
<div class="flex flex-col justify-center items-center h-full">
  <img class="w-75 rounded-full" src="https://lichter.io/img/me@2x.webp" />
  <h2 class="mt-4">Alexander Lichter</h2>
</div>
</template>

<template v-slot:right>
<VClicks class="space-y-2 mt-10 text-xl h-full">

* <VoidzeroIconsVoidzeroLogo class="text-white" width="4rem" height="auto" /> DevRel
* <mdi-account-check class="dark:text-green-100 text-green-700" /> **Web Engineering Consultant**
* <mdi-microphone /> Speaker & Instructor
* <logos-nuxt-icon /> Nuxt.js Team
* <mdi-github /><logos-bluesky class="text-sm mb-1 text-blue-400" /><mdi-youtube class="text-red-500" /><mdi-twitch class="text-purple-700" /> @TheAlexLichter
* <mdi-web /> [https://lichter.io](https://lichter.io)

</VClicks>
</template>

---
layout: intro
---

# Nuxt 4

<noto-drum class="text-10" />
<noto-drum class="text-10" />
<noto-drum class="text-10" />

---
layout: image
image: https://preview.redd.it/swmwroeby8171.png?width=1080&crop=smart&auto=webp&s=aa0a5f2b3e03bc979225e4794e19c444f38b602c
backgroundSize: contain
---

---

# Nuxt 4


* Release is still pending


<VClicks>

* But you can opt-in to the breaking changes today!

</VClicks>

---

# Nuxt 4

* Release is still pending
* But you can opt-in to the breaking changes today!

<Code file="nuxt.config.ts">

````md magic-move
```ts
export default defineNuxtConfig({
})
```
```ts
export default defineNuxtConfig({
  future: {
    compatibilityVersion: 4,
  }
})
```
````

</Code> 

---
layout: intro
---

<div class="text-4xl!">

`pnpm create nuxt -t v4-compat`

</div>

<p class="pt-4" v-click>
To start a new project with Nuxt 4 breaking changes.
</p>

<!--
  DEMO New Wizard
-->



---
layout: intro
---

# New folder structure

---

# New folder structure

````md magic-move
```sh
.nuxt/
assets/
components/
composables/
layouts/
middleware/
pages/
utils/
app.vue
router.options.ts
modules/
layers/
node_modules/
public/
server/
  api/
  middleware/
  plugins/
  routes/
  utils/
nuxt.config.ts
```
```sh
.nuxt/
app/
  assets/
  components/
  composables/
  layouts/
  middleware/
  pages/
  utils/
  app.vue
  router.options.ts
modules/
layers/
node_modules/
public/
server/
  api/
  middleware/
  plugins/
  routes/
  utils/
nuxt.config.ts
```
```sh
.nuxt/
app/
modules/
layers/
node_modules/
public/
server/
nuxt.config.ts
```
```sh
.nuxt/
app/
modules/
layers/
node_modules/
public/
server/
shared/
nuxt.config.ts
```
````

---

# `shared` folder

<VClicks>

* Ideal for shared code that can be used in both app and server (contextless)
* Import protection so you can't import a Vue component, h3 helper or Nitro utility in the wrong place
* Auto-import for `shared/utils` and `shared/types`

</VClicks>

---
layout: intro
---

# Lazy/Delayed/Partial Hydration

---

# Lazy/Delayed/Partial Hydration

<VClicks>

* Implemented in Vue 3.5
* First class citizen in Nuxt 3.16

</VClicks>

---

<Hydration class="h-80 w-full" />

---

# Lazy/Delayed/Partial Hydration

<Code file="pages/index.vue">

````md magic-move
```vue
<template>
  <div>
    <h1>Lazy Hydration</h1>
    <p>This is a demo of lazy hydration.</p>
    <!-- Default hydration -->
    <MyComponentHere />
  </div>
</template>
```
```vue
<template>
  <div>
    <h1>Lazy Hydration</h1>
    <p>This is a demo of lazy hydration.</p>
    <!-- No hydration -->
    <LazyMyComponentHere hydrate-never />
  </div>
</template>
```
```vue
<template>
  <div>
    <h1>Lazy Hydration</h1>
    <p>This is a demo of lazy hydration.</p>
    <!-- Hydration when visible -->
    <LazyMyComponentHere hydrate-on-visible />
  </div>
</template>
```
```vue
<template>
  <div>
    <h1>Lazy Hydration</h1>
    <p>This is a demo of lazy hydration.</p>
    <!-- Hydration when browser is idle -->
    <LazyMyComponentHere hydrate-on-idle />
  </div>
</template>
```
````

</Code>

<VClicks>

* Will *not* load the JS by default
* Needs auto-imports and SFCs

</VClicks>

---

# Lazy Hydration Macros

<Code file="future.vue">

```vue
<script setup lang="ts">
const LazyHydrationMyComponent = defineLazyHydrationComponent(
  'never',
  () => import('./components/MyComponent.vue')
)
</script>
<template>
  <div>
    <!-- This component will never be hydrated by Vue. -->
    <LazyHydrationMyComponent />
  </div>
</template>
```

</Code>

<VClicks>

* Macros to use them without auto-imports as well
* [PR pending](https://github.com/nuxt/nuxt/pull/31192)

</VClicks>


---
layout: intro
---

# [LLMs.txt](https://nuxt.com/llms.txt)
## And a [Nuxt MCP](https://github.com/antfu/nuxt-mcp)

---
layout: intro
---

# Find the bug


---

# Find the bug

<Code file="MyComponent.vue">

````md magic-move
```vue
<script setup>
const someStore = useUserStore()

const { data } = useAsyncData(async () => {
  const response = await $fetch('/api/some-api')
  someStore.user = response.user
})
</script>
```
````

</Code>

<VClicks>

* `useAsyncData` **must be side-effect free**
* Instead, use `callOnce`!

</VClicks>

---

# `callOnce`

<Code file="MyComponent.vue">

````md magic-move
```vue
<script setup>
const someStore = useUserStore()

const { data } = useAsyncData(async () => {
  const response = await $fetch('/api/some-api')
  someStore.user = response.user
})
</script>
```
```vue
<script setup>
const someStore = useUserStore()

callOnce(async () => {
  const response = await $fetch('/api/some-api')
  someStore.user = response.user
})
</script>
```
```vue
<script setup>
const someStore = useUserStore()
// Do it on every navigation change
callOnce(async () => {
  const response = await $fetch('/api/some-api')
  someStore.user = response.user
}, { mode: 'navigation' })
</script>
```
````

</Code>

---
layout: intro
---

# Nuxt without <logos-vitejs />

---

# Nuxt without <logos-vitejs />


<VClicks>

* Nuxt is a multi-bundler Framework
* You can use it with Webpack, rspack or Vite (default)
* Just install `@nuxt/rspack-builder` and set `builder: 'rspack'` in your config
* Done!
* Why would you? Requirements are weird sometimes 🙈
* But it is possible!

</VClicks>

---
layout: intro
---

# Caching + BFF with Nitro

---

# Caching + BFF with Nitro


<VClicks>

* Use Nitro to build a **full-stack** application
* Can wrap your existing backend
* E2E type safety
* Caching on the server easily possible
* Storage and runtime-agnostic

</VClicks>

---
layout: intro
---

# `nuxt.config.ts`

---

# `nuxt.config.ts` - But env-aware

<VClicks>

* Need some caching enabled in production only?
* Want to use a different API URL in development?
* Or just want to have different settings for different environments?
* No problem!

</VClicks>

---

# `nuxt.config.ts` - But env-aware

````md magic-move
```ts
export default defineNuxtConfig({
  // some config before
  $production: {
    routeRules: {
      '/api/**': {
        cache: {
          maxAge: 60
        }
      }
    }
  },
})
```
```ts
export default defineNuxtConfig({
  // some config before
  $production: {
    routeRules: {
      '/api/**': {
        cache: {
          maxAge: 60
        }
      }
    }
  },
  
  $development: {
    app: {
      head: {
        title: 'We are in development! DO NOT PANIC!'
      }
    }
  }
}
```
```ts
export default defineNuxtConfig({
  // some config before
  $production: {
    routeRules: {
      '/api/**': {
        cache: {
          maxAge: 60
        }
      }
    }
  },
  $development: {
    app: {
      head: {
        title: 'We are in development! DO NOT PANIC!'
      }
    }
  },
  $env: {
    staging: {
      app: {
        head: {
          title: '[STAGING] Bro - Also check out my YT'
        }
      }
    }
  }
}
```
````

---
layout: intro
---

# `nuxt dev`

---

# `nuxt dev`

<VClicks>

* Why is the dev command a "hidden gem"?!?
* it is all about the arguments
* `nuxt dev --https` enables local HTTPS out of the box
* `nuxt dev --open` straight away opens the URL in the browser
* `nuxt dev --tunnel` exposes your local server to the internet (Be careful!)
* `nuxt dev --qr` shows a QR code for the public URL
* And there are more arguments to explore!

</VClicks>

---
layout: intro
---

## Ready for more? Then <span class="inline-block bg-gradient-to-r from-blue-600 via-red-500 to-green-400 bg-clip-text text-transparent">follow</span> along!

<div class="flex mx-32 mt-16 gap-8 my-auto justify-around items-center">
  <Qrcode v-click class="max-w-xl" url="https://www.youtube.com/@TheAlexLichter/">
    YouTube
    <span class="text-sm text-gray-500">lichter.link/yt</span>
  </Qrcode>
  <Qrcode v-click class="max-w-xl" url="https://dejavue.fm/?ref=vuejsde2024">
    The DejaVue Podcast
    <span class="text-sm text-gray-500">dejavue.fm</span>
  </Qrcode>
</div>

---
layout: intro
---

# Thanks a lot to my sponsors!
<img src="https://raw.githubusercontent.com/manniL/static/main/sponsors.svg" class="h-80 mx-auto" alt="My GitHub sponsors">

---
layout: two-cols
heading: Thank you for your attention!
---

<template v-slot:default>
<div class="flex flex-col justify-center items-center h-full">
<img
  class="w-75 rounded-full"
  src="https://lichter.io/img/me@2x.webp"
  />
  <h2 class="mt-4">Alexander Lichter</h2>
</div>
</template>

<template v-slot:right>

* <VoidzeroIconsVoidzeroLogo class="text-white" width="4rem" height="auto" /> DevRel
* <mdi-account-check class="dark:text-green-100 text-green-700" /> Web Engineering Consultant
* <mdi-microphone /> Speaker & Instructor
* <logos-nuxt-icon /> Nuxt.js Team
* <mdi-github /><logos-bluesky class="text-sm mb-1 text-blue-400" /><mdi-youtube class="text-red-500" /><mdi-twitch class="text-purple-700" /> @TheAlexLichter
* <mdi-web /> [https://lichter.io](https://lichter.io)

</template>

---
layout: intro
---

## Ready for more? Then <span class="inline-block bg-gradient-to-r from-blue-600 via-red-500 to-green-400 bg-clip-text text-transparent">follow</span> along!

<div class="flex mx-32 mt-16 gap-8 my-auto justify-around items-center">
  <Qrcode v-click class="max-w-xl" url="https://www.youtube.com/@TheAlexLichter/">
    YouTube
    <span class="text-sm text-gray-500">lichter.link/yt</span>
  </Qrcode>
  <Qrcode v-click class="max-w-xl" url="https://dejavue.fm/?ref=vuejsde2024">
    The DejaVue Podcast
    <span class="text-sm text-gray-500">dejavue.fm</span>
  </Qrcode>
</div>
