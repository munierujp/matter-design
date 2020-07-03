# Matter Design
Design system for components

## Component types
### Elements
Elements are abstract components like HTML elements. These can contain Elements.

### Matters
Elements are concrete components. These can contain Elements, Matters.

### Pages
Pages are page components. These can contain Elements, Matters.

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
│   └── default.vue
└── pages
    └── index.vue
```

#### Elements
`components/elements/AppButton.vue`:

```vue
<template>
  <button @click="click">
    <slot />
  </button>
</template>

<script>
export default {
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
  <app-button @click="login">Login</app-button>
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
    <app-button>Cancel</app-button>
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

## Badge
You can use the badge to show that your project is using Matter Design.

[![using Matter Design](https://img.shields.io/badge/using-Matter%20Design-brightgreen)](https://github.com/munierujp/matter-design)

Markdown:

```md
[![using Matter Design](https://img.shields.io/badge/using-Matter%20Design-brightgreen)](https://github.com/munierujp/matter-design)
```

HTML:

```html
<a href="https://github.com/munierujp/matter-design"><img src="https://img.shields.io/badge/using-Matter%20Design-brightgreen" alt="using Matter Design"></a>
```
