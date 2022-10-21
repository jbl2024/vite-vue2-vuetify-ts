# Vue 2 + TypeScript + Vite + Vuetify

<p align="center">
  <img src="https://user-images.githubusercontent.com/480173/157433906-7f7910d4-6430-49f4-857a-044945e71360.png" alt="logo" width="300" height="300" />
</p>

This is a [starter project](https://github.com/logue/vite-vue2-ts-starter) that uses [Vuetify](https://vuetifyjs.com/) as the UI framework.

Vuetify3 version is [here](https://github.com/logue/vite-vuetify-ts-starter).

## Description

This template is for using Vue2 with TypeScript in Vite. Includes [vue-router](https://router.vuejs.org/) and [Vuex](https://vuex.vuejs.org/).

In addition, [ESLint](https://eslint.org/), [Stylelint](https://stylelint.io/), and [Prettier](https://prettier.io/) are also included and are set to be executed automatically at runtime and commit. (Since these settings are set strictly, please relax yourself.)

Also, when the development server is executed, it is checked in real time by [vite-plugin-checker](https://github.com/fi3ework/vite-plugin-checker).

[Vitest](https://github.com/vuejs/vue-test-utils) is included in the program for testing.

### Known issue

`vue-tsc` outputs an error with `v-checkbox`. (Because of the specification to write `v-model` and `value` together)

If you encounter this kind of trouble, set `vueTsc: false` in `vite-plugin-checker` in `vite.config.ts` and remove `vue-tsc --noEmit` from the `build` command in `package.json`.

### Composition API

With the standard support for [Composition API](https://composition-api.vuejs.org/) in vue 2.7, the default format is composition api.

[vue-property-decorator](https://github.com/kaorun343/vue-property-decorator) has been dropped since 0.9.1. Please install manually if necessary.

### Teleport

Vue3 adds a mechanism called [`Teleport`](https://v3.vuejs.org/guide/teleport.html), which allows you to install vue components anywhere.
This starter template is for vue2, but you can do the same with [@logue/vue2-helpers/vue2-teleport](https://github.com/logue/vue2-helpers).

#### Teleport JSON-LD Example

If you want to include [JSON-LD](https://json-ld.org/), enter as follows.

```vue
<template>
  <div class="container">
    ... Some Content
    <teleport to="head">
      <component :is="'script'" type="application/ld+json" v-text="jsonLd" />
    </teleport>
  </div>
</template>

<script>
import { defineComponent, ref } from 'vue';

export default defineComponent({
  setup() {
    const jsonLd = ref(
      JSON.stringfy({
        '@schema': 'https://json.schemastore.org/jsonld.json',
        '@context': 'http://schema.org',
        '@type': 'WebSite',
        name: 'Vite Vue2 Vuetify TypeScript Startar',
        url: 'https://github.com/logue/vite-vue2-vuetify-ts-starter',
        description: 'Vite Vue2 Vuetify TypeScript Demo Page',
      })
    );

    return {
      jsonLd,
    };
  },
});
</script>
```

JSON-LD is literally a `script`, so it can't be embedded directly, so it's a roundabout thing like this, but simple things like `meta` tags are reflected by simply inserting a tag.

⚠ Notice: `<component :is="'script'" ... />` becomes `<component :as="'script'" ... />` in Vue3.

### Vue i18n

If you want to use [vue-i18n](https://kazupon.github.io/vue-i18n/), please install [intlify-unplugin-vue-i18n](https://github.com/intlify/bundle-tools/tree/main/packages/unplugin-vue-i18n) and call the instance with `useI18n()`.

In addition, the conventional method using `$t()` written in non composition-api can be used as it is.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=vue.volar) (and disable Vetur).

## Commands

| Command       | Description                                        |
| ------------- | -------------------------------------------------- |
| dev           | Start devserver.                                   |
| clean         | Clear devserver cache.                             |
| lint          | Run ESLint and prettier.                           |
| lint:style    | Run Stylelint.                                     |
| lint:markup   | Check vue markup.                                  |
| test          | Run vitest                                         |
| coverage      | Output Coverage Report.                            |
| build         | Build for production.                              |
| build:analyze | Execute Bundle Analyzer                            |
| build:deploy  | Build for production without checking.             |
| build:clean   | Clear production build files.                      |
| preview       | Run the program generated by the production build. |

⚠ Notice: Be sure to use `build:deploy` as the build command for auto-deploying to Github Pages, Vercel, CloudFlare pages, etc. `build` is for checking whether the build passes locally, and an error occurs because it is executed without `Meta.ts` being created.

## Migrate from VueCli

It also works when migrating from VueCLI.

However, when importing a stylesheet with `@import`, it cannot be specified from the library directory. Must be specified from `./node_modules/`.

## Troubleshooting

When adding or deleting files, an error may occur and even if the error is corrected, it may not be reflected in devserver. In that case, stop devserver and delete all the files in the `node_modules/.vite` directory. You can also run it with the `clean` command.

Due to [yarn issues](https://github.com/yarnpkg/berry/issues/4448), it may not work properly if the path contains non-ASCII characters (such as 日本語 or 한국어, 中文 etc.).

From 0.7.4, the default project type is module. If you find a plugin that doesn't work, remove `"type": "module"` from package.json.

## Checklist

When you use this template, try follow the checklist to update your info properly

- [ ] Change the author name in `LICENSE` and `package.json`
- [ ] Change the favicon in `public` and `src/assets`
- [ ] Remove the `.github` folder which contains the funding info
- [ ] Clean up the READMEs and remove routes

## See Also

- [@logue/vue2-helpers](https://github.com/logue/vue2-helpers)
- [vite-vue2-ts-starter](https://github.com/logue/vite-vue2-ts-starter)
- [laravel9-vite-vue2-starter](https://github.com/logue/laravel9-vite-vue2-starter) - for Laravel + Breeze.
- [vite-vue2-ts-ssr-starter](https://github.com/logue/vite-vue2-ts-ssr-starter) - SSR (Server Side Rendering) Version.