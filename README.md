# glamor

![build status](https://travis-ci.org/threepointone/glamor.svg)

css for component systems

`npm install glamor --save`

usage 
```jsx
import { style, hover } from 'glamor'

// make css rules 
let rule = style({ 
  color: 'red',
  ':hover': {
    color: 'pink'
  },
  '@media(min-width: 300px)': {
    color: 'green',
    ':hover': {
      color: 'yellow'
    }
  }
})

// add as data attributes
<div {...rule} {...another}>
  zomg
</div>

// or as classes 
<div className={`${rule} ${another}`}>
  zomg
</div>

// compose rules for great justice 
let mono = style({
  fontFamily: 'monospace'
})

let bolder = style({
  fontWeight: 'bolder'
})

<div {...merge(mono, bolder)}>
  bold code!
</div>

```

motivation
---

This expands on ideas from @vjeux's [2014 css-in-js talk](https://speakerdeck.com/vjeux/react-css-in-js).
We introduce an api to annotate arbitrary dom nodes with style definitions ("rules") for, um, the greater good.

features
---

- really small / fast / efficient, with a fluent api
- framework independent
- adds vendor prefixes / fallback values 
- supports all the pseudo :classes/::elements
- `@media` queries
- `@font-face` / `@keyframes`
- escape hatches for parent and child selectors 
- dev helper to simulate pseudo classes like `:hover`, etc
- server side / static rendering
- tests / coverage

(thanks to [BrowserStack](https://www.browserstack.com/) for providing the infrastructure that allows us to run our build in real browsers.)

docs 
---
- [api documentation](https://github.com/threepointone/glamor/blob/master/docs/api.md)
- [howto](https://github.com/threepointone/glamor/blob/master/docs/howto.md) - a comparison of css techniques in glamor
- [plugins](https://github.com/threepointone/glamor/blob/master/docs/plugins.md)
- [server side rendering](https://github.com/threepointone/glamor/blob/master/docs/server.md)

extras 
---

- `glamor/reset` - include a css reset
- `glamor/react` - helpers for [themes](https://github.com/threepointone/glamor/blob/master/docs/themes.md), [inline 'css' prop](https://github.com/threepointone/glamor/blob/master/docs/createElement.md), [`@vars`](https://github.com/threepointone/glamor/blob/master/docs/vars.md)
- `glamor/jsxstyle` - [react integration](https://github.com/threepointone/glamor/blob/master/docs/jsxstyle.md), à la [jsxstyle](https://github.com/petehunt/jsxstyle/)
- `glamor/aphrodite` - [shim](https://github.com/threepointone/glamor/blob/master/docs/aphrodite.md) for [aphrodite](https://github.com/Khan/aphrodite) stylesheets
- `glamor/utils` - a port of [postcss-utilities](https://github.com/ismamz/postcss-utilities)
- `glamor/ous` - a port of [the skeleton css framework](http://getskeleton.com)


characteristics
---

while glamor shares most common attributes of other inline style / css-in-js systems,
here are some key differences -

- uses 'real' stylesheets, so you can use all css features. 
- rules can be used as data-attributes or classNames. 
- simulate pseudo-classes with the `simulate` helper. very useful, especially when combined when hot-loading and/or editing directly in devtools.
- really fast, by way of deduping rules, and using [insertRule](https://developer.mozilla.org/en-US/docs/Web/API/CSSStyleSheet/insertRule) in production.


todo
---

- [planned enhancements](https://github.com/threepointone/glamor/issues?q=is%3Aopen+is%3Aissue+label%3Aenhancement)
- notes on composition
- ie8 compat

profit, profit
---

I get it
