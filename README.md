# Matter Design
Design system for components

## Component types
* **Elements** - abstract components like HTML elements
  * e.g. `<app-button>`
* **Matters** - concrete components
  * e.g. `<app-login-button>`
* **Pages** - page components

## Example
### Nuxt.js
```
.
├── components
│   │── elements
│   │   └── AppButton.vue
│   └── matters
│       └── AppLoginButton.vue
├── layouts
│   ├── default.vue
└── pages
    └── index.vue
```

#### Elements
`components/elements/AppButton.vue`:

```vue
<template>
  <button @click="click">{{ label }}</button>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      required: true
    }
  },
  methods: {
    click (e) {
      this.$emit('click', e)
    }
  }
}
</script>
```

#### Matters
`components/matters/AppLoginButton.vue`:

```vue
<template>
  <app-button label="Login" @click="login" />
</template>

<script>
import AppButton from '~/components/elements/AppButton'

export default {
  components: {
    AppButton
  },
  methods: {
    login () {
      // login
    }
}
</script>
```

#### Pages
`layouts/default.vue`:

```vue
<template>
  <div id="app">
    <main>
      <nuxt />
    </main>
  </div>
</template>
```

`pages/index.vue`:

```vue
<template>
  <div>
    <app-button label="Cancel" />
    <app-login-button />
  </div>
</template>

<script>
import AppButton from '~/components/elements/AppButton'
import AppLoginButton from '~/components/matters/AppLoginButton'

export default {
  components: {
    AppButton,
    AppLoginButton
  }
}
</script>
```
