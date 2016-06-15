## Concepts
BEM namingconvention

ITCSS

The idea behind ITCSS is to sort the css in a way, that rules do not need to be overridden on a regular basis. Start with a low specificity and end with the highest. Each following section must have at least the same specificity as the preceding.

![specificity graph](https://pbs.twimg.com/media/CiFbPYvWwAEPHH_.jpg)

Part | Specificity
-----| -----------
Settings | -
Tools | -
Generic | 0, 1
Elements | 1
Scoped Elements | 11
Components | 11
Trumps | 11+, !important



### Settings
Does not add anything to the CSS.

### Tools
Does not add anything to the CSS.
Mixins

### Generic
normalize.css
```css
* {}
p {}
```
Specificity: 0, 1

### Elements
```css
a {} # 0 - 0 - 1
p {} # 0 - 0 - 1
```

### Scoped elements

Styling elements in a scope is very useful for user generated content. The CMS/users must be able to use plain elements without
classes and still get styled results.

```css
.content a {} # 0 - 1 - 1
.content ul {} # 0 - 1 - 1

.blog__text p {} # 0 - 1 - 1
```

The problem with scoped elements is, that when using a component inside of a scope, the styles of the component will be overridden
by the scoped elements style.

The best solution is to not allow components inside user generated content. That might work in most cases, but can be a problem
for components like a button.

### Components
Components are the building-blocks of the page. Components may be nested.
```css
.button {} # 0 - 1 - 0
```

Common cases when using modifiers
```css
.button--big {} # 0 - 1 - 0
.button--big .button__text {} # 0 - 2 - 0
.button--big .button__text a {} # 0 - 2 - 1, modified scoped elements
```

### Trumps
```css
.hidden {
    display: none!important;
}
```
Specificity: 11+, !important
