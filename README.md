# Styling

- [Styling](#styling)
  - [Data Binding - Styles](#data-binding---styles)
  - [CSS - Classes](#css---classes)
  - [CSS - Classes - 2](#css---classes---2)
  - [CSS - Java script based](#css---java-script-based)
  - [CSS - Class Array](#css---class-array)

## Data Binding - Styles

- `v-bind:style` or `:style`
- Uses camelcase for css attributes

```html
<div
  class="demo"
  @click="boxSelected('A')"
  :style="{borderColor: boxASelected ? 'red' : '#ccc'}"
></div>
```

```js
const app = Vue.createApp({
  data() {
    return {
      boxASelected: false,
      boxBSelected: false,
      boxCSelected: false,
    };
  },
  methods: {
    boxSelected(box) {
      if (box === 'A') this.boxASelected = !this.boxASelected;
      else if (box === 'B') this.boxBSelected = !this.boxBSelected;
      else this.boxCSelected = !this.boxCSelected;
    },
  },
});
app.mount('#styling');
```

## CSS - Classes

- `v-bind:style` or `:style`
- Uses camelcase for css attributes

```html
<div
  @click="boxSelected('A')"
  :class="boxASelected ? 'demo active' : 'demo'"
></div>
```

## CSS - Classes - 2

- Here `demo` class is alwas active
- `active` class ifs active when `boxASelected` is true
- `demo:` true can be substituted with `class="demo"` as it will always be active

```html
<div
  @click="boxSelected('A')"
  :class="{ demo: true, active: boxASelected }"
></div>
```

## CSS - Java script based

- Classes are provided dynamically using javascript

```html
<div @click="boxSelected('A')" class="demo" :class="boxAClasses"></div>
```

```js
...
computed: {
    boxAClasses() {
      return {active: this.boxASelected}
    }
},
...
```

## CSS - Class Array

- Providing an array of classes

```html
<div
  @click="boxSelected('A')"
  :class="['demo', { active: boxBSelected }]"
></div>
```
