# Real World Vue.js Boilerplate
This project based on real world practice and ready to use. Have a fun!

## Features
- Http request class that implements API calls with Auth and tokens refresh based on Axios
- Data access layer/API calls
- Response wrapper/Response error wrapper
- Base common and layout components
- Some help mixins

## Project structure
- [`index.html`](#indexhtml)
- [`src`](#src)
  - [`assets`](#assets)
  - [`components`](#components)
  - [`config`](#config)
  - [`directives`](#directives)
  - [`layout`](#layout)
  - [`mixins`](#mixins)
  - [`pages`](#pages)
  - [`plugins`](#plugins)
  - [`router`](#router)
  - [`scss`](#scss)
  - [`services`](#services)
  - [`store`](#store)
  - [`.env.js`](#envjs)
  - [`app.init.js`](#appinitjs)
  - [`global.helpers.js`](#globalhelpersjs)

### `index.html`
Main index HTML file.

### `src`
Source =)

### `assets`
Images/Fonts/Other media stuff.

### `components`
Shared components folder.
- `DataBox` wrap in this component any received data. It represents loading(spinloader animation), error and empty statuses (examaple in `src/pages/News.vue`).
- `ImgLoader` - `img` tag wrapper. Shows image loading(pulseloader animation) status and animate onloading as option.
- `ModalWindow` - simple modal window.
- `PulseLoading` and `SpinnerWave` - loading animation.
- `UploadMulti` and `UploadSingle` - file upload example components.
- ...

### `config`
App config files. Each category in separate file.

### `directives`
Directives.
- Handy debounce directive

### `layout`
Base app layout components.
- `Header`, `Footer` components and main layout wrapper.

### `mixins`
- One method/prop per file principle.
- Name files same as method/prop.
- `currentUser` - Includes current user object from store. Global.
- `formatDateTime` - Datetime moment formatters. Global.
- `jumpTo` - Help jump to some DOM element. Global.
- `prepareFetchParamsMixin` - Prepare params for data fetching (examaple in `src/pages/News.vue`).
- `prepareQueryParamsMixin` - Prepare params for setting it in URL (examaple in `src/pages/News.vue`).
- `setModelMixin` - Use to set same fields from response that declared in front-end model.

### `pages`
Page wrapper components(Pages) and Local components.

### `plugins`
- `globalEventBus` - $bus.

### `router`
Router instance and routing declaration.
- `index` - router initialization.
- `routes` - routing.
- `middlewares`:
  - `initCurrentUserStateMiddleware` - Current user state initialization (each time app loads, check refresh token and fetch current user if token exist.)
  - `checkAccessMiddleware` - Each time user change route, check permissions to route.
  - `setPageTitleMiddleware` - Each time user change route, set page title.
- `util`:
  - `routePropResolver` - Pass params from URL to component as props (example in `src/router/routes.js`)

### `scss`
Style files(partials, variables, mixins, reset).

### `services`
Data access layer/API calls.
- ES6 API calls classes.
- API calls must be represented in separate classes (not in vuex action).
- `auth.service` - Auth methods and API calls.
- `http.init` - Http request class.
- `util`:
  - `ResponseWrapper` - Represent response object.
  - `ErrorWrapper` - Represent error object.
  - `clearData` - Uses to clear request data before send it. Helper.

### `store`
App store with separate modules.

### `.env.js`
Environment variables (add this to git ignore).

### `app.init.js`
Root app initialization file.

### `global.helpers.js`
Add global helpers to window object. Yepp globals ... =)

### How to declare global SCSS variables/mixins etc... ?
In `/build/utils.js` >> `generateLoaders('sass')`

## Utils/Helpers

###  What about debounce ?
```
import debounce from '../directives/debounce'
directives: {
  debounce
}
```
And use it in template.
```
<input type="text" v-model="name" v-debounce="500" @debounce-change="runSomeMethod">
```

## Build Setup
``` bash
# clone repo
git clone https://github.com/zmts/vuejs-boilerplate.git

# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

# TODO
- Add toast
- Refact imports in `app.init`
