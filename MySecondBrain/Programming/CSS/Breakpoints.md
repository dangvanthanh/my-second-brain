Tags: #css, #javascript

---

# Breakpoints

## JavaScript

```javascript
const screen = [0, 576, 768, 992, 1200, 1440, 1902]
const breakpoints = {
	xs: 0,
	sm: 1,
	md: 2,
	lg: 3,
	xl: 4,
	xxl: 5,
	xxxl: 6
}

function mq(minWidth) {
	return `@media screen and (min-width: ${breakpoints[minWidth]}px)`
}

export { mq, breakpoints }
```

Then use

```javascript
if (mq(breakpoints.xs)) {}
if (mq(breakpoints.sm)) {}
if (mq(breakpoints.md)) {}
if (mq(breakpoints.lg)) {}
if (mq(breakpoints.xl)) {}
if (mq(breakpoints.xxl)) {}
if (mq(breakpoints.xxxl)) {}
```

## CSS in Root

```css
:root {
  --xs: 0px;
  --sm: 576px;
  --md: 768px;
  --lg: 992px;
  --xl: 1200px;
  --xxl: 1440px;
  --xxxl: 1920px;
}

body {
  max-width: var(--lg);
}
```

## CSS with Custom Media

Using PostCSS plugins:

- [postcss-preset-env](https://preset-env.cssdb.org/features#custom-media-queries)
- [postcss-custom-media](https://github.com/postcss/postcss-custom-media)

```css
@custom-media --xs (>= 0)
@custom-media --sm (>= 576px)
@custom-media --md (>= 768px)
@custom-media --lg (>= 992px)
@custom-media --xl (>= 1200px)
@custom-media --xxl (>= 1440px)
@custom-media --xxxl (>= 1920px)
```