# Matter Design
Design system for components

## Component types
* **Pages** - page components
* **Matters** - concrete components
  * e.g. `<app-login-button>`
* **Elements** - abstract components like HTML elements
  * e.g. `<app-button>`

## Example
### Nuxt.js
#### Pages
`pages/index.vue`:

```vue
<template>
  <app-button label="Cancel" />
  <app-login-button />
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
