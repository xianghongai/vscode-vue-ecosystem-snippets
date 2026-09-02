# Vue Ecosystem Snippets (Visual Studio Code)

VS Code 中的 Vue 3 生态日常代码片段：VueUse、服务端状态、表单、数据校验、国际化、head 元信息、组合式函数模式、类名处理与测试。

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

[English](./README.md)

## 前缀清单

前缀遵循三种模式：

1. **API 名本身就是前缀** —— `useLocalStorage`、`onClickOutside`、`useForm`、`useHead`。库 API 的名字**就是**最终要写下的代码，中间没有翻译环节，无需先记一套映射。
2. **少数日常 API 另配短码** —— `uls` = `useLocalStorage`、`uf` = `useForm`、`uh` = `useHead`。两种形式挂在同一条片段上，短码是用熟之后的提速手段，而不是上手门槛。`useQuery` 与 `useMutation` 不配：此处有两个库都定义它们，单一缩写说不清指哪个。
3. **同库共用词干，场景在其后扩展** —— `pinia…`、`defineStore…`、`store.$…`、`query…`、`colada…`、`vv…`、`i18n…`、`head…`、`zod…`、`composable…`、`vtu…`、`recipe…`。打出词干就能在补全列表里摊开整个库。

### 客户端状态 — Pinia

这一组覆盖 Pinia 本身。`defineStore`、`defineStoreAsync`、`defineStoreOptions`、`defineStoreCompose`、`defineStoreForm`、`piniaSSR` 会从**文件名**推导 store 名和 id：在 `counter.ts` 中触发得到 `useCounterStore` 和 `'counter'`；在 `user-profile.ts` 或 `userProfile.ts` 中都得到 `useUserProfileStore` 和 `'user-profile'`。

| 前缀                 | 别名      | 插入内容                                                                 |
| -------------------- | --------- | ------------------------------------------------------------------------ |
| `acceptHMRUpdate`    | `phmr`    | store 的热更新（Vite）                                                   |
| `defineStore`        | `ds`      | 完整的 Setup Store 文件：state / getters / actions + HMR                 |
| `defineStoreAsync`   | `dsa`     | 带远程请求的列表 store，含 loading / error                               |
| `defineStoreCompose` | `dsc`     | 在一个 store 里组合另一个 store                                          |
| `defineStoreForm`    | `dsf`     | 表单 store，提交后 `$reset()`                                            |
| `defineStoreOptions` | `dso`     | 完整的 Option Store 文件                                                 |
| `disposePinia`       | `dp`      | 销毁整个实例                                                             |
| `getActivePinia`     | `gap`     | 读取当前激活的实例                                                       |
| `imma`               |           | 导入并展开 `mapActions()`                                                |
| `imms`               |           | 导入并展开 `mapState()`                                                  |
| `immws`              |           | 导入并展开 `mapWritableState()`                                          |
| `ims`                |           | 导入并实例化一个 store                                                   |
| `imss`               |           | 导入并展开 `mapStores()`                                                 |
| `imstr`              |           | 导入 `storeToRefs()` 并解构 state                                        |
| `ma`                 |           | `mapActions()`——actions 映射为 methods                                   |
| `ms`                 |           | `mapState()`——state 和 getters 映射为只读 computed                       |
| `mss`                |           | `mapStores()`——整个 store 映射为 computed                                |
| `mws`                |           | `mapWritableState()`——state 映射为可写 computed，用于 `v-model`          |
| `pinia`              | `cp`      | 应用入口——创建并安装 pinia 实例                                          |
| `pinia.state`        | `pstate`  | 读取或替换所有 store 的根 state                                          |
| `pinia.use`          | `pu`      | 注册插件                                                                 |
| `piniaOnAction`      | `plog`    | 统一记录每个 action 耗时与错误的插件                                     |
| `piniaPersist`       | `pper`    | 用 `$subscribe()` 把单个 store 持久化到 localStorage                     |
| `piniaPlugin`        | `pplugin` | 给所有声明启用的 store 加持久化的插件                                    |
| `piniaSSR`           | `pssr`    | 用 `skipHydrate()` 的 SSR store                                          |
| `piniaTest`          | `ptest`   | store 单元测试文件                                                       |
| `piniaTestComponent` | `ptestc`  | 用 `createTestingPinia()` 的组件测试                                     |
| `setActivePinia`     | `sap`     | 无应用挂载时激活某个实例——测试、脚本、SSR                                |
| `setMapStoreSuffix`  | `smss`    | 修改 `mapStores()` 追加的后缀                                            |
| `shouldHydrate`      | `shy`     | 判断某个值是否参与 hydration                                             |
| `skipHydrate`        | `skh`     | 标记 state 不参与 hydration，SSR 载荷不会覆盖它                          |
| `store.$dispose`     | `sd`      | 停止单个 store 的副作用与订阅                                            |
| `store.$onAction`    | `sa`      | 监听 action，含 `after()` 与 `onError()`                                 |
| `store.$patch`       | `sp`      | 函数形式的 `$patch()`——集合操作只能用它表达                              |
| `store.$patchObject` | `spo`     | 对象形式的 `$patch()`                                                    |
| `store.$reset`       | `sr`      | 重置 state 到初始值                                                      |
| `store.$state`       | `sst`     | 整体替换某个 store 的 state                                              |
| `store.$subscribe`   | `ss`      | 监听 state 变化                                                          |
| `storeAction`        | `pact`    | Setup Store 的 `action()` 助手，让 `$onAction` 在 store 内部调用时也触发 |
| `useStore`           |           | 在 `<script setup>` 中使用 store，用 `storeToRefs()` 保持响应性          |
| `useStoreOptions`    | `uso`     | 在 Options API 中使用 store                                              |
| `useStoreOutside`    | `pout`    | 在组件外使用 store——路由守卫、拦截器                                     |

### VueUse

| 前缀                      | 缩写  | 插入内容                                                                                   |
| ------------------------- | ----- | ------------------------------------------------------------------------------------------ |
| `computedAsync`           |       | 由异步计算派生值，并用标志位表示是否仍在进行                                               |
| `createGlobalState`       |       | 不经 provider，让某个组合式函数的状态在所有调用方之间共用同一份实例                        |
| `createInjectionState`    |       | 通过 provide/inject 把组合式函数的状态限定在某棵子树内，第一个函数负责提供、第二个负责读取 |
| `onClickOutside`          | `oco` | 点击落在元素之外时收起或关闭                                                               |
| `refDebounced`            | `rd`  | 对值而非函数做防抖，适合作为查询键或侦听源                                                 |
| `refThrottled`            |       | 对变化中的值做节流                                                                         |
| `syncRef`                 |       | 让两个 ref 单向或双向保持同步                                                              |
| `until`                   |       | 等待响应式条件成立，而不是轮询它                                                           |
| `useAsyncState`           | `uas` | 执行 promise 并暴露其状态，适合无需缓存的一次性加载                                        |
| `useClipboard`            | `uc`  | 复制文本到剪贴板，copied 会短暂保持为真以便界面给出反馈                                    |
| `useColorMode`            |       | 跟踪超出明暗两态的配色模式，取值会写入 html 元素的 class                                   |
| `useCounter`              |       | 管理带上下界的数值计数器                                                                   |
| `useDark`                 | `ud`  | 跟踪并切换暗色模式，结果会持久化并与系统偏好同步                                           |
| `useDateFormat`           |       | 不引入日期库即可格式化响应式日期                                                           |
| `useDebounceFn`           | `udf` | 对函数防抖，调用停止后才执行一次                                                           |
| `useDropZone`             |       | 在元素上接收拖放文件并给出悬停状态                                                         |
| `useElementSize`          | `ues` | 跟踪元素的渲染尺寸                                                                         |
| `useElementVisibility`    |       | 跟踪元素是否处于视口内                                                                     |
| `useEventListener`        | `uel` | 订阅 DOM 事件，作用域销毁时自动移除                                                        |
| `useEventSource`          |       | 订阅服务端推送的事件流                                                                     |
| `useFetch`                |       | 以响应式方式请求 URL，url 传 ref 时其变化会触发重新请求                                    |
| `useFocus`                |       | 读取并设置元素的聚焦状态                                                                   |
| `useFullscreen`           |       | 对元素或整页操作 Fullscreen API                                                            |
| `useIdle`                 |       | 跟踪用户是否已静默超过给定时长                                                             |
| `useInfiniteScroll`       |       | 滚动容器接近底部时加载下一页，canLoadMore 在列表耗尽后阻止继续触发                         |
| `useIntersectionObserver` |       | 元素进出视口时执行回调                                                                     |
| `useIntervalFn`           | `uif` | 按间隔执行回调，可暂停与恢复，作用域销毁时自动停止                                         |
| `useLocalStorage`         | `uls` | 把响应式值持久化到 localStorage                                                            |
| `useMagicKeys`            |       | 按组合键名称响应按键                                                                       |
| `useMediaQuery`           | `umq` | 以响应式布尔值跟踪 CSS 媒体查询                                                            |
| `useMouse`                |       | 跟踪指针位置及其来源类型                                                                   |
| `useNow`                  |       | 以响应式 Date 跟踪当前时间                                                                 |
| `useOnline`               |       | 跟踪网络可用状态                                                                           |
| `usePermission`           |       | 跟踪 Permissions API 的授权状态，不主动发起请求                                            |
| `usePreferredDark`        |       | 只读取系统的暗色偏好，不接管选择权                                                         |
| `useRefHistory`           |       | 记录 ref 的历史并提供撤销与重做                                                            |
| `useResizeObserver`       |       | 元素尺寸变化时执行回调                                                                     |
| `useScroll`               |       | 跟踪滚动位置、方向以及是否触达边界                                                         |
| `useSessionStorage`       |       | 仅在当前标签页内持久化响应式值                                                             |
| `useStorage`              | `us`  | 把响应式值持久化到 Storage 并跨标签页同步                                                  |
| `useSwipe`                |       | 识别元素上的触摸滑动及其方向                                                               |
| `useThrottleFn`           | `utf` | 对函数节流，每个间隔内最多执行一次                                                         |
| `useTimeoutFn`            |       | 延迟后执行一次回调，可手动启动与停止                                                       |
| `useToggle`               | `ut`  | 管理布尔值，toggle 也接受显式的下一个值                                                    |
| `useVModel`               |       | 把 prop 暴露成可写 ref 并自动发出更新事件，用于封装接受 v-model 的组件                     |
| `useWebSocket`            |       | 维持带重连与心跳的 WebSocket 连接                                                          |
| `vueuseImport`            |       | 导入 VueUse 14 组合式函数                                                                  |
| `watchDebounced`          |       | 侦听来源，但等其稳定后才执行                                                               |
| `watchIgnorable`          |       | 侦听来源的同时可写入而不触发回调，用于打断双向同步的死循环                                 |
| `watchOnce`               |       | 侦听来源，首次变化后即停止                                                                 |
| `watchThrottled`          |       | 侦听来源，每个间隔内最多响应一次                                                           |

### VueUse 集成层

| 前缀           | 缩写 | 插入内容                             |
| -------------- | ---- | ------------------------------------ |
| `useAxios`     |      | 以响应式方式调用 Axios 实例          |
| `useCookies`   |      | 以响应式方式读写 cookie              |
| `useFocusTrap` |      | 把键盘焦点困在对话框或抽屉内         |
| `useSortable`  |      | 让列表可拖拽排序，并把新顺序写回数组 |

### 服务端状态 — TanStack Vue Query

| 前缀               | 缩写 | 插入内容                                                                       |
| ------------------ | ---- | ------------------------------------------------------------------------------ |
| `queryDependent`   |      | 输入就绪前挂起查询，避免以 undefined 作为键发起请求                            |
| `queryImport`      |      | 导入 TanStack Vue Query 5 API                                                  |
| `queryOptimistic`  |      | 在服务端确认前先行应用变更，失败时回滚                                         |
| `queryOptions`     | `qo` | 定义可复用的查询选项，让键与请求函数绑在一起                                   |
| `queryPlugin`      |      | 在应用上安装 TanStack Vue Query                                                |
| `queryPrefetch`    |      | 在悬停或聚焦时预热缓存，使下一个视图立即渲染                                   |
| `queryReactiveKey` |      | 把 ref 直接放进 queryKey：Vue Query 会解包并在其变化时重新请求，无需另写侦听器 |
| `useInfiniteQuery` |      | 分页浏览无限列表，TanStack Query 5 要求提供 initialPageParam                   |
| `useMutation`      |      | 向服务端写入并刷新受影响的数据                                                 |
| `useQuery`         |      | 读取服务端状态并暴露等待与错误状态                                             |

### 服务端状态 — Pinia Colada

| 前缀                 | 缩写  | 插入内容                                                        |
| -------------------- | ----- | --------------------------------------------------------------- |
| `coladaImport`       |       | 导入 Pinia Colada 1 API                                         |
| `coladaInvalidate`   |       | 重新拉取某个查询，未设置 exact 时连同其键下的所有子查询一并失效 |
| `coladaOptimistic`   |       | 在服务端确认前先行应用变更，失败时回滚                          |
| `coladaPlugin`       |       | 在应用上安装 Pinia Colada                                       |
| `coladaReactiveKey`  |       | 把 key 写成 getter，输入变化时查询即重新执行                    |
| `defineQuery`        |       | 把查询封装成组合式函数，所有调用方共用同一实例及其周边状态      |
| `defineQueryOptions` | `dqo` | 定义可复用的查询选项，组件可展开后按需覆盖其中的项              |
| `useMutation`        |       | 向服务端写入并使受影响的查询失效                                |
| `useQuery`           |       | 用 Pinia Colada 读取服务端状态                                  |

### 表单

| 前缀              | 缩写  | 插入内容                                                                        |
| ----------------- | ----- | ------------------------------------------------------------------------------- |
| `defineField`     | `df`  | 绑定单个字段：第一个值用 v-model，第二个用 v-bind 绑到输入框上                  |
| `useField`        |       | 把自定义或非原生输入封装成表单字段                                              |
| `useFieldArray`   | `ufa` | 管理可重复的字段组，fields 的每一项带有稳定的 key                               |
| `useForm`         | `uf`  | 以 Zod schema 驱动表单，defineField 返回可 v-model 的值与需绑定到输入框的 props |
| `vvFieldMarkup`   |       | 渲染单个字段及其标签与错误信息                                                  |
| `vvFormComponent` |       | 在模板而非脚本中声明表单                                                        |
| `vvImport`        |       | 导入 VeeValidate 4 API                                                          |
| `vvSetErrors`     |       | 把被拒绝的提交映射回服务端指出的字段上                                          |

### 数据校验

| 前缀                    | 缩写 | 插入内容                                                |
| ----------------------- | ---- | ------------------------------------------------------- |
| `zodArray`              |      | 定义带最小长度的数组 schema                             |
| `zodCoerceNumber`       |      | 对以字符串形式到达的表单或查询串输入做数值转换与校验    |
| `zodDiscriminatedUnion` |      | 定义按字面量字段区分的联合类型，解析结果可依该字段收窄  |
| `zodEnum`               |      | 把取值限定在固定的字符串集合内                          |
| `zodImport`             |      | 导入 Zod 4 的 schema 构造器                             |
| `zodInputOutput`        |      | 从带 transform 的 schema 推导出各不相同的输入与输出类型 |
| `zodObject`             | `zo` | 定义对象 schema                                         |
| `zodOptional`           |      | 为对象结构添加可选字段                                  |
| `zodSafeParse`          |      | 校验来路不明的数据且不抛错                              |
| `zodTransform`          |      | 定义会改写解析结果的 schema                             |

### 国际化

| 前缀                 | 缩写 | 插入内容                                                                      |
| -------------------- | ---- | ----------------------------------------------------------------------------- |
| `i18nChangeLanguage` |      | 切换当前语言，locale 是可写 ref                                               |
| `i18nFormat`         |      | 按语言格式化数字与日期，具名格式来自实例上的 numberFormats 与 datetimeFormats |
| `i18nImport`         |      | 导入 Vue I18n 11 API                                                          |
| `i18nInit`           |      | 为组合式 API 创建 i18n 实例，legacy 必须为 false，useI18n 才可用              |
| `i18nInterpolation`  |      | 带具名参数翻译，消息中用 {name} 占位                                          |
| `i18nPlural`         |      | 翻译复数键，消息中各形态以竖线分隔                                            |
| `i18nScoped`         |      | 把组件的文案放在组件旁而非全局目录里                                          |
| `i18nT`              |      | 把组件插入到译文中，而不是拼接字符串                                          |
| `i18nTypes`          |      | 以真实的语言模块为准推导消息键的类型，写错键即类型报错                        |
| `useI18n`            | `ui` | 取得翻译函数与当前语言                                                        |

### Head 与 SEO

| 前缀                | 缩写  | 插入内容                                           |
| ------------------- | ----- | -------------------------------------------------- |
| `headInit`          |       | 在应用上安装 Unhead                                |
| `headReactive`      |       | 由状态派生标题，getter 会随来源变化重新求值        |
| `headTitleTemplate` |       | 为每个页面标题套用站点级模板，在根组件设置一次即可 |
| `useHead`           | `uh`  | 为当前组件设置文档标题与 meta 标签                 |
| `useSeoMeta`        | `usm` | 以扁平键声明社交与搜索元数据，无需手写 meta 标签   |

### 组合式函数模式

| 前缀                 | 缩写 | 插入内容                                                                                                          |
| -------------------- | ---- | ----------------------------------------------------------------------------------------------------------------- |
| `composableArgument` |      | 读取可能是值、ref 或 getter 的参数并对其变化作出响应                                                              |
| `composableCleanup`  |      | 在所属作用域结束时释放资源                                                                                        |
| `composableFile`     |      | 完整的类型化组合式函数：参数同时接受值、ref 与 getter，副作用自行清理请求，返回的状态为只读，写入权只留在函数内部 |
| `composableScope`    |      | 把若干副作用归入一个作用域以便统一销毁，适用于生命周期长于单个组件、或按需创建的状态                              |
| `composableShared`   |      | 只创建一次状态并把同一实例交给所有调用方                                                                          |

### 类名处理

| 前缀         | 缩写 | 插入内容                                                     |
| ------------ | ---- | ------------------------------------------------------------ |
| `clsx`       |      | 拼接条件类名                                                 |
| `clsxImport` |      | 导入 clsx 2 以拼接条件类名                                   |
| `cnUtility`  |      | 完整的工具函数：一次调用完成条件类名拼接与 Tailwind 冲突消解 |
| `twMerge`    |      | 合并 Tailwind 工具类，冲突时后者生效                         |

### 测试

| 前缀                | 缩写 | 插入内容                                                            |
| ------------------- | ---- | ------------------------------------------------------------------- |
| `testComposable`    |      | 不挂载组件即可测试组合式函数，effectScope 为其副作用与清理提供归属  |
| `testFlushPromises` |      | 在断言渲染结果前先让挂起的 promise 结算                             |
| `testQueryWrapper`  |      | 为每个用例配置独立的 query client，避免重试与共享缓存在用例之间串味 |
| `vtlRender`         |      | 完整的测试，经由无障碍树而非内部状态驱动                            |
| `vtuEmitted`        |      | 断言组件发出的事件及其载荷                                          |
| `vtuMount`          |      | 完整的组件交互测试                                                  |

### 组合场景

| 前缀                     | 缩写 | 插入内容                                                                                      |
| ------------------------ | ---- | --------------------------------------------------------------------------------------------- |
| `recipeFormMutation`     |      | 完整的表单组件：一份 Zod schema 负责校验，mutation 负责写入，失败回落到字段上、成功后刷新列表 |
| `recipeHeadI18n`         |      | 让文档标题与 html 的 lang 属性跟随当前语言                                                    |
| `recipePendingIndicator` |      | 完整的全局请求指示器，覆盖应用内任何进行中的请求，在根部挂载一次即可                          |
| `recipeQueryZod`         |      | 在边界处校验响应，让格式不符的数据以查询错误的形式失败，而不是流入组件                        |
| `recipeSearchQuery`      |      | 完整的搜索组件：防抖后的词即缓存键，每个稳定下来的词只请求一次并被缓存，过短的词不会触发请求  |

## 官方依据

- [VS Code 片段格式与 scope](https://code.visualstudio.com/docs/editing/userdefinedsnippets)
- [Pinia —— 核心概念](https://pinia.vuejs.org/zh/core-concepts/)
- [Pinia —— 插件](https://pinia.vuejs.org/zh/core-concepts/plugins.html)
- [Pinia —— 服务端渲染](https://pinia.vuejs.org/zh/ssr/)
- [Pinia —— 测试 Store](https://pinia.vuejs.org/zh/cookbook/testing.html)
- [VueUse 函数索引](https://vueuse.org/functions.html)
- [TanStack Query for Vue](https://tanstack.com/query/latest/docs/framework/vue/overview)
- [Pinia Colada](https://pinia-colada.esm.dev/)
- [VeeValidate 组合式 API](https://vee-validate.logaretm.com/v4/guide/composition-api/getting-started/)
- [Zod 基础](https://zod.dev/basics)
- [Vue I18n 组合式 API](https://vue-i18n.intlify.dev/guide/advanced/composition.html)
- [Unhead for Vue](https://unhead.unjs.io/docs/vue/head/guides/get-started/installation)
- [Vue Test Utils](https://test-utils.vuejs.org/)

MIT 许可，见 LICENSE。
