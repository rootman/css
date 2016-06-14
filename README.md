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
a {}
p {}
```
Specificity: 1

### Scoped elements

```css
.content a {}
.content ul {}
```
Specificity : 10 + 1 = 11

### Components
Components are the building-blocks of the page. Components may be nested.
```css
html .button {}
```
Specificity : 1 + 10 = 11

### Trumps
```css
.hidden {
	display: none!important;
}
```
Specificity: 11+, !important
