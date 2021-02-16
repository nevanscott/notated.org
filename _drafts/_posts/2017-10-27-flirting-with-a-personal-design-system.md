---
title: "Flirting with a personal design system"
date: "2017-10-27T20:23:22+02:00"
draft: true
---

Over the past year, I've been developing a new look and feel for my personal website, and recently I flipped the switch on a similar look and feel for this blog. To mark the occasion, I thought I'd share some notes on my approach.

## 1. Use descriptive markup

Wherever possible, I'm using the simplest, most essential HTML to markup content. For example, at a top level, the page structure looks like:

```html
<body>
	<header role="banner">
		...
	</header>
	<main role="main">
	  ...
	</main>
	<footer role="contentinfo">
	  ...
	</footer>
</body>
```

Semantic elements and proper [ARIA roles][] provide rich hooks for selectors without the need for many CSS classes.

*[ARIA]: Accessible Rich Internet Applications
*[CSS]: Cascading Style Sheets

[ARIA roles]: https://www.w3.org/TR/wai-aria/roles

## 2.
