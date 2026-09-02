# Vue Ecosystem Snippets (Visual Studio Code)

Everyday Vue 3 ecosystem patterns for VS Code: VueUse, server state, forms, validation, i18n, head metadata, composable patterns, class names and tests.

<p>
  <a href="https://github.com/xianghongai/vscode-vue-ecosystem-snippets">
    <img src="https://img.shields.io/github/repo-size/xianghongai/vscode-vue-ecosystem-snippets?color=4ac51c&style=plastic" alt="Repo Size">
  </a>
  <a href="https://marketplace.visualstudio.com/items?itemName=nicholashsiang.vscode-vue-ecosystem-snippets">
    <img src="https://vsmarketplacebadges.dev/version/nicholashsiang.vscode-vue-ecosystem-snippets.svg?style=plastic&color=4ac51c" alt="Visual Studio Marketplace Version">
  </a>
  <a href="https://marketplace.visualstudio.com/items?itemName=nicholashsiang.vscode-vue-ecosystem-snippets">
    <img src="https://vsmarketplacebadges.dev/downloads-short/nicholashsiang.vscode-vue-ecosystem-snippets.svg?style=plastic&color=4ac51c" alt="Downloads">
  </a>
  <a href="https://marketplace.visualstudio.com/items?itemName=nicholashsiang.vscode-vue-ecosystem-snippets">
    <img src="https://vsmarketplacebadges.dev/rating-short/nicholashsiang.vscode-vue-ecosystem-snippets.svg?style=plastic&color=4ac51c" alt="Rating">
  </a>
  <a href="https://github.com/xianghongai/vscode-vue-ecosystem-snippets/blob/HEAD/LICENSE">
    <img src="https://img.shields.io/github/license/xianghongai/vscode-vue-ecosystem-snippets?color=4ac51c&style=plastic" alt="License">
  </a>
</p>

[中文文档](./README_CN.md)

## Prefixes

Prefixes follow three patterns:

1. **The API name is the prefix** — `useLocalStorage`, `onClickOutside`, `useForm`, `useHead`. A library API's name _is_ the code you are about to write, so there is no mapping to memorize first.
2. **A few daily APIs also answer to a short alias** — `uls` = `useLocalStorage`, `uf` = `useForm`, `uh` = `useHead`. Both forms sit on the same snippet, so the alias is a speed-up once you know it, never the way in. `useQuery` and `useMutation` get none: two libraries here define them, so a single alias could not say which.
3. **A library shares a stem, its scenarios extend it** — `pinia…`, `defineStore…`, `store.$…`, `query…`, `colada…`, `vv…`, `i18n…`, `head…`, `zod…`, `composable…`, `vtu…`, `recipe…`. Type the stem and the completion list lays the whole library out.

### Client state — Pinia

These snippets cover Pinia itself. `defineStore`, `defineStoreAsync`, `defineStoreOptions`, `defineStoreCompose`, `defineStoreForm` and `piniaSSR` derive the store name and id from the **file name**: `counter.ts` yields `useCounterStore` / `'counter'`; both `user-profile.ts` and `userProfile.ts` yield `useUserProfileStore` / `'user-profile'`.

| Prefix               | Alias     | Inserts                                                                      |
| -------------------- | --------- | ---------------------------------------------------------------------------- |
| `acceptHMRUpdate`    | `phmr`    | Hot Module Replacement for a store (Vite)                                    |
| `defineStore`        | `ds`      | A complete Setup Store file: state / getters / actions + HMR                 |
| `defineStoreAsync`   | `dsa`     | A remote list store with loading and error state                             |
| `defineStoreCompose` | `dsc`     | One store composed from another                                              |
| `defineStoreForm`    | `dsf`     | Form state with `$reset()` after submit                                      |
| `defineStoreOptions` | `dso`     | A complete Option Store file                                                 |
| `disposePinia`       | `dp`      | Dispose an entire instance                                                   |
| `getActivePinia`     | `gap`     | Read the currently active instance                                           |
| `imma`               |           | Import and spread `mapActions()`                                             |
| `imms`               |           | Import and spread `mapState()`                                               |
| `immws`              |           | Import and spread `mapWritableState()`                                       |
| `ims`                |           | Import a store and instantiate it                                            |
| `imss`               |           | Import and spread `mapStores()`                                              |
| `imstr`              |           | Import `storeToRefs()` and destructure state                                 |
| `ma`                 |           | `mapActions()` — actions as methods                                          |
| `ms`                 |           | `mapState()` — state and getters as readonly computed                        |
| `mss`                |           | `mapStores()` — whole stores as computed                                     |
| `mws`                |           | `mapWritableState()` — state as writable computed, for `v-model`             |
| `pinia`              | `cp`      | Application entry — create and install the pinia instance                    |
| `pinia.state`        | `pstate`  | Read or replace the root state of every store                                |
| `pinia.use`          | `pu`      | Register a plugin                                                            |
| `piniaOnAction`      | `plog`    | A plugin that logs every action's timing and errors                          |
| `piniaPersist`       | `pper`    | Persist one store to localStorage with `$subscribe()`                        |
| `piniaPlugin`        | `pplugin` | A plugin that persists every store that opts in                              |
| `piniaSSR`           | `pssr`    | An SSR store using `skipHydrate()`                                           |
| `piniaTest`          | `ptest`   | A store unit test file                                                       |
| `piniaTestComponent` | `ptestc`  | A component test with `createTestingPinia()`                                 |
| `setActivePinia`     | `sap`     | Make an instance active with no app mounted — tests, scripts, SSR            |
| `setMapStoreSuffix`  | `smss`    | Change the suffix `mapStores()` appends                                      |
| `shouldHydrate`      | `shy`     | Check whether a value is hydratable                                          |
| `skipHydrate`        | `skh`     | Mark state as non-hydratable so the SSR payload leaves it alone              |
| `store.$dispose`     | `sd`      | Stop one store's effects and subscriptions                                   |
| `store.$onAction`    | `sa`      | Watch actions, with `after()` and `onError()`                                |
| `store.$patch`       | `sp`      | `$patch()` with a function — the only form that expresses collections        |
| `store.$patchObject` | `spo`     | `$patch()` with a partial state object                                       |
| `store.$reset`       | `sr`      | Reset state to its initial value                                             |
| `store.$state`       | `sst`     | Replace a store's whole state                                                |
| `store.$subscribe`   | `ss`      | Watch state changes                                                          |
| `storeAction`        | `pact`    | Setup Store `action()` helper, so `$onAction` fires from inside the store    |
| `useStore`           |           | Use a store in `<script setup>`, keeping state reactive with `storeToRefs()` |
| `useStoreOptions`    | `uso`     | Use a store from the Options API                                             |
| `useStoreOutside`    | `pout`    | Use a store outside components — router guards, interceptors                 |

### VueUse

| Prefix                    | Alias | Inserts                                                                                                           |
| ------------------------- | ----- | ----------------------------------------------------------------------------------------------------------------- |
| `computedAsync`           |       | Derive a value from an async computation, with a flag telling whether it is still running                         |
| `createGlobalState`       |       | Share one instance of a composable's state across every caller, without a provider                                |
| `createInjectionState`    |       | Scope a composable's state to a subtree through provide and inject; the first function provides, the second reads |
| `onClickOutside`          | `oco` | Close or dismiss when a click lands outside an element                                                            |
| `refDebounced`            | `rd`  | Debounce a value rather than a function, for use as a query key or watcher source                                 |
| `refThrottled`            |       | Throttle a changing value                                                                                         |
| `syncRef`                 |       | Keep two refs in sync in one or both directions                                                                   |
| `until`                   |       | Await a reactive condition instead of polling it                                                                  |
| `useAsyncState`           | `uas` | Run a promise and expose its state, for one-off loads that do not need a cache                                    |
| `useClipboard`            | `uc`  | Copy text to the clipboard; copied stays true briefly so the UI can confirm                                       |
| `useColorMode`            |       | Track a color mode beyond light and dark; the value is written to a class on the html element                     |
| `useCounter`              |       | Manage a numeric counter with bounds                                                                              |
| `useDark`                 | `ud`  | Track and toggle dark mode, persisted and synced with the system preference                                       |
| `useDateFormat`           |       | Format a reactive date without pulling in a date library                                                          |
| `useDebounceFn`           | `udf` | Debounce a function so it runs once the calls stop                                                                |
| `useDropZone`             |       | Accept dropped files on an element and report hover state                                                         |
| `useElementSize`          | `ues` | Track an element's rendered size                                                                                  |
| `useElementVisibility`    |       | Track whether an element is in the viewport                                                                       |
| `useEventListener`        | `uel` | Subscribe to a DOM event and remove it when the scope is disposed                                                 |
| `useEventSource`          |       | Subscribe to a server-sent event stream                                                                           |
| `useFetch`                |       | Fetch a URL reactively; passing a ref as the url refetches when it changes                                        |
| `useFocus`                |       | Read and set an element's focus state                                                                             |
| `useFullscreen`           |       | Drive the Fullscreen API for an element or the page                                                               |
| `useIdle`                 |       | Track whether the user has been inactive for a given duration                                                     |
| `useInfiniteScroll`       |       | Load the next page as the scroll container nears its end; canLoadMore stops it firing once the list is exhausted  |
| `useIntersectionObserver` |       | Run a callback as an element enters or leaves the viewport                                                        |
| `useIntervalFn`           | `uif` | Run a callback on an interval that can be paused and resumed; it stops when the scope is disposed                 |
| `useLocalStorage`         | `uls` | Persist a reactive value to localStorage                                                                          |
| `useMagicKeys`            |       | React to a key combination by name                                                                                |
| `useMediaQuery`           | `umq` | Track a CSS media query as a reactive boolean                                                                     |
| `useMouse`                |       | Track the pointer position and where it came from                                                                 |
| `useNow`                  |       | Track the current time as a reactive Date                                                                         |
| `useOnline`               |       | Track network availability                                                                                        |
| `usePermission`           |       | Track a Permissions API state without requesting it                                                               |
| `usePreferredDark`        |       | Read the system dark-mode preference without owning the choice                                                    |
| `useRefHistory`           |       | Track a ref's history and expose undo and redo                                                                    |
| `useResizeObserver`       |       | Run a callback whenever an element is resized                                                                     |
| `useScroll`               |       | Track scroll offset, direction and whether an edge has been reached                                               |
| `useSessionStorage`       |       | Persist a reactive value for the current tab only                                                                 |
| `useStorage`              | `us`  | Persist a reactive value to a Storage backend and keep it in sync across tabs                                     |
| `useSwipe`                |       | Detect touch swipes on an element and their direction                                                             |
| `useThrottleFn`           | `utf` | Throttle a function so it runs at most once per interval                                                          |
| `useTimeoutFn`            |       | Run a callback once after a delay, with manual start and stop                                                     |
| `useToggle`               | `ut`  | Manage a boolean with a toggle that also accepts an explicit next value                                           |
| `useVModel`               |       | Expose a prop as a writable ref that emits its update event, for wrapping a component that takes v-model          |
| `useWebSocket`            |       | Hold a WebSocket connection with reconnection and heartbeat                                                       |
| `vueuseImport`            |       | Import a VueUse 14 composable                                                                                     |
| `watchDebounced`          |       | Watch a source but wait until it settles                                                                          |
| `watchIgnorable`          |       | Watch a source while being able to write to it without triggering the watcher, which breaks two-way sync loops    |
| `watchOnce`               |       | Watch a source and stop after the first change                                                                    |
| `watchThrottled`          |       | Watch a source at most once per interval                                                                          |

### VueUse integrations

| Prefix         | Alias | Inserts                                                             |
| -------------- | ----- | ------------------------------------------------------------------- |
| `useAxios`     |       | Call an Axios instance reactively                                   |
| `useCookies`   |       | Read and write cookies reactively                                   |
| `useFocusTrap` |       | Trap keyboard focus inside a dialog or drawer                       |
| `useSortable`  |       | Make a list drag-sortable and write the new order back to the array |

### Server state — TanStack Vue Query

| Prefix             | Alias | Inserts                                                                                                                |
| ------------------ | ----- | ---------------------------------------------------------------------------------------------------------------------- |
| `queryDependent`   |       | Hold a query until its input exists, so it never runs with an undefined key                                            |
| `queryImport`      |       | Import a TanStack Vue Query 5 API                                                                                      |
| `queryOptimistic`  |       | Apply a change before the server confirms it and roll back on failure                                                  |
| `queryOptions`     | `qo`  | Define reusable query options so key and fetcher stay together                                                         |
| `queryPlugin`      |       | Install TanStack Vue Query on the application                                                                          |
| `queryPrefetch`    |       | Warm the cache on hover or focus so the next view renders immediately                                                  |
| `queryReactiveKey` |       | Put a ref straight into the query key: Vue Query unwraps it and refetches whenever it changes, so no watcher is needed |
| `useInfiniteQuery` |       | Page through an infinite list; TanStack Query 5 requires initialPageParam                                              |
| `useMutation`      |       | Write to the server and refresh what the change affects                                                                |
| `useQuery`         |       | Read server state and expose its pending and error states                                                              |

### Server state — Pinia Colada

| Prefix               | Alias | Inserts                                                                                                                   |
| -------------------- | ----- | ------------------------------------------------------------------------------------------------------------------------- |
| `coladaImport`       |       | Import a Pinia Colada 1 API                                                                                               |
| `coladaInvalidate`   |       | Refetch a query and, unless exact is set, everything nested under its key                                                 |
| `coladaOptimistic`   |       | Apply a change before the server confirms it and roll back on failure; what onMutate returns is handed to the later hooks |
| `coladaPlugin`       |       | Install Pinia Colada on the application; it builds on Pinia, so Pinia must be installed first                             |
| `coladaReactiveKey`  |       | Make the key a getter so the query refetches when its input changes                                                       |
| `defineQuery`        |       | Wrap a query in a composable so every caller shares one instance and any extra state around it                            |
| `defineQueryOptions` | `dqo` | Define reusable query options that a component can spread and override per call                                           |
| `useMutation`        |       | Write to the server and invalidate what the change affects                                                                |
| `useQuery`           |       | Read server state with Pinia Colada                                                                                       |

### Forms

| Prefix            | Alias | Inserts                                                                                                 |
| ----------------- | ----- | ------------------------------------------------------------------------------------------------------- |
| `defineField`     | `df`  | Bind one field: v-model the first value and v-bind the second onto the input                            |
| `useField`        |       | Wrap a custom or non-native input as a form field; passing the name as a getter keeps it reactive       |
| `useFieldArray`   | `ufa` | Manage a repeatable group of fields; each entry of fields carries a stable key                          |
| `useForm`         | `uf`  | Drive a form from a Zod schema; defineField returns a v-model target and the props to bind on the input |
| `vvFieldMarkup`   |       | Render one field with its label and error message                                                       |
| `vvFormComponent` |       | Declare a form in the template instead of the script                                                    |
| `vvImport`        |       | Import a VeeValidate 4 API                                                                              |
| `vvSetErrors`     |       | Map a rejected submission onto the fields the server complained about                                   |

### Validation

| Prefix                  | Alias | Inserts                                                                                       |
| ----------------------- | ----- | --------------------------------------------------------------------------------------------- |
| `zodArray`              |       | Define an array schema with a minimum length                                                  |
| `zodCoerceNumber`       |       | Coerce and validate a numeric field, for form and query-string input that arrives as a string |
| `zodDiscriminatedUnion` |       | Define a union discriminated by a literal field, so the parsed value narrows on that field    |
| `zodEnum`               |       | Restrict a value to a fixed set of strings                                                    |
| `zodImport`             |       | Import the Zod 4 schema builder                                                               |
| `zodInputOutput`        |       | Derive the distinct input and output types of a transforming schema                           |
| `zodObject`             | `zo`  | Define an object schema                                                                       |
| `zodOptional`           |       | Add an optional field to an object shape                                                      |
| `zodSafeParse`          |       | Validate unknown data without throwing                                                        |
| `zodTransform`          |       | Define a schema that reshapes its parsed value                                                |

### i18n

| Prefix               | Alias | Inserts                                                                                                            |
| -------------------- | ----- | ------------------------------------------------------------------------------------------------------------------ |
| `i18nChangeLanguage` |       | Switch the active locale; locale is a writable ref                                                                 |
| `i18nFormat`         |       | Format numbers and dates per locale; the named formats come from numberFormats and datetimeFormats on the instance |
| `i18nImport`         |       | Import a Vue I18n 11 API                                                                                           |
| `i18nInit`           |       | Create the i18n instance for the Composition API; legacy must be false for useI18n to work                         |
| `i18nInterpolation`  |       | Translate a key with named values; the message uses {name} placeholders                                            |
| `i18nPlural`         |       | Translate a plural key; the message separates its forms with a pipe                                                |
| `i18nScoped`         |       | Keep a component's messages next to the component instead of in the global catalogue                               |
| `i18nT`              |       | Interpolate components into a translated message instead of concatenating strings                                  |
| `i18nTypes`          |       | Type message keys from the actual locale module, so a wrong key is a type error                                    |
| `useI18n`            | `ui`  | Get the translate function and the active locale                                                                   |

### Head and SEO

| Prefix              | Alias | Inserts                                                                           |
| ------------------- | ----- | --------------------------------------------------------------------------------- |
| `headInit`          |       | Install Unhead on the application                                                 |
| `headReactive`      |       | Derive the title from state; a getter is re-evaluated whenever its source changes |
| `headTitleTemplate` |       | Wrap every page title in a site-wide pattern; set it once in the root component   |
| `useHead`           | `uh`  | Set the document title and meta tags for the current component                    |
| `useSeoMeta`        | `usm` | Declare social and search metadata as flat keys instead of hand-writing meta tags |

### Composable patterns

| Prefix               | Alias | Inserts                                                                                                                                                                                 |
| -------------------- | ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `composableArgument` |       | Read an argument that may be a value, a ref or a getter, and react to it changing                                                                                                       |
| `composableCleanup`  |       | Release a resource when the surrounding scope ends                                                                                                                                      |
| `composableFile`     |       | Complete typed composable: the argument accepts a value, a ref or a getter, the effect cleans up its own request, and the returned state is read-only so only this composable writes it |
| `composableScope`    |       | Group several effects so they can be disposed together, for state that outlives one component or is created on demand                                                                   |
| `composableShared`   |       | Create a composable's state once and hand the same instance to every caller                                                                                                             |

### Class names

| Prefix       | Alias | Inserts                                                                                       |
| ------------ | ----- | --------------------------------------------------------------------------------------------- |
| `clsx`       |       | Compose conditional class names                                                               |
| `clsxImport` |       | Import clsx 2 for conditional class names                                                     |
| `cnUtility`  |       | Complete helper that composes conditional classes and resolves Tailwind conflicts in one call |
| `twMerge`    |       | Merge Tailwind utility classes so a later conflicting class wins                              |

### Tests

| Prefix              | Alias | Inserts                                                                                                       |
| ------------------- | ----- | ------------------------------------------------------------------------------------------------------------- |
| `testComposable`    |       | Test a composable without mounting a component; the scope gives it a place for its effects and cleanup to run |
| `testFlushPromises` |       | Let pending promises settle before asserting on what rendered                                                 |
| `testQueryWrapper`  |       | Give each test its own query client, so retries and a shared cache do not leak between cases                  |
| `vtlRender`         |       | Complete test driven through the accessibility tree rather than internal state                                |
| `vtuEmitted`        |       | Assert the events a component emitted and the payloads it sent                                                |
| `vtuMount`          |       | Complete component interaction test                                                                           |

### Recipes

| Prefix                   | Alias | Inserts                                                                                                                                     |
| ------------------------ | ----- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `recipeFormMutation`     |       | Complete form component: one Zod schema validates, the mutation writes, a failure lands back on the field and success refreshes the list    |
| `recipeHeadI18n`         |       | Keep the document title and the html lang attribute in step with the active locale; both are getters, so switching language rewrites them   |
| `recipePendingIndicator` |       | Complete indicator for any request in flight anywhere in the application; mount it once near the root                                       |
| `recipeQueryZod`         |       | Validate a response at the boundary so malformed data fails as a query error instead of reaching the component                              |
| `recipeSearchQuery`      |       | Complete search component: the debounced term is the cache key, so each settled term is fetched once and cached, and short terms never fire |

## References

- [VS Code snippet format and scopes](https://code.visualstudio.com/docs/editing/userdefinedsnippets)
- [Pinia — core concepts](https://pinia.vuejs.org/core-concepts/)
- [Pinia — plugins](https://pinia.vuejs.org/core-concepts/plugins.html)
- [Pinia — server-side rendering](https://pinia.vuejs.org/ssr/)
- [Pinia — testing stores](https://pinia.vuejs.org/cookbook/testing.html)
- [VueUse functions](https://vueuse.org/functions.html)
- [TanStack Query for Vue](https://tanstack.com/query/latest/docs/framework/vue/overview)
- [Pinia Colada](https://pinia-colada.esm.dev/)
- [VeeValidate composition API](https://vee-validate.logaretm.com/v4/guide/composition-api/getting-started/)
- [Zod basics](https://zod.dev/basics)
- [Vue I18n composition API](https://vue-i18n.intlify.dev/guide/advanced/composition.html)
- [Unhead for Vue](https://unhead.unjs.io/docs/vue/head/guides/get-started/installation)
- [Vue Test Utils](https://test-utils.vuejs.org/)

MIT licensed. See LICENSE.
