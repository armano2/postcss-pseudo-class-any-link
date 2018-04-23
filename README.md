# :any-link [<img src="https://postcss.github.io/postcss/logo.svg" alt="PostCSS Logo" width="90" height="90" align="right">][postcss]

[![NPM Version][npm-img]][npm-url]
[![CSS Standard Status][css-img]][css-url]
[![Build Status][cli-img]][cli-url]
[![Support Chat][git-img]][git-url]

[:any-link] lets you to use the proposed [`:any-link`] pseudo-class in CSS.

`:any-link` simplifies selectors targeting links, as the naming of `:link` is misleading; it specifically means unvisited links only, rather than all links.

```css
nav :any-link > span {
	background-color: yellow;
}

/* becomes */

nav :link > span, nav :visited > span {
	background-color: yellow;
}
```

From the [proposal]:

> The [`:any-link`] pseudo-class represents an element that acts as the source anchor of a hyperlink. It matches an element if the element would match [`:link`] or [`:visited`].

## Usage

Add [:any-link] to your build tool:

```bash
npm install postcss-pseudo-class-any-link --save-dev
```

#### Node

Use [:any-link] to process your CSS:

```js
require('postcss-pseudo-class-any-link').process(YOUR_CSS);
```

#### PostCSS

Add [PostCSS] to your build tool:

```bash
npm install postcss --save-dev
```

Use [:any-link] as a plugin:

```js
postcss([
	require('postcss-pseudo-class-any-link')()
]).process(YOUR_CSS);
```

#### Gulp

Add [Gulp PostCSS] to your build tool:

```bash
npm install gulp-postcss --save-dev
```

Use [:any-link] in your Gulpfile:

```js
var postcss = require('gulp-postcss');

gulp.task('css', function () {
	return gulp.src('./src/*.css').pipe(
		postcss([
			require('postcss-pseudo-class-any-link')()
		])
	).pipe(
		gulp.dest('.')
	);
});
```

#### Grunt

Add [Grunt PostCSS] to your build tool:

```bash
npm install grunt-postcss --save-dev
```

Use [:any-link] in your Gruntfile:

```js
grunt.loadNpmTasks('grunt-postcss');

grunt.initConfig({
	postcss: {
		options: {
			use: [
				require('postcss-pseudo-class-any-link')()
			]
		},
		dist: {
			src: '*.css'
		}
	}
});
```

### Alternatives

Here are a few other ways to simulate the effect of [PostCSS Pseudo-Class Any-Link].

```css
/* Use @custom-selector; supported nowhere yet */

@custom-selector :--any-link :link, :visited;

:--any-link { /* ... */ }

/* Use :matches; supported in Firefox 4+, Chrome 12+, Opera 15+, Safari 5.1+ */

:matches(:link, :visited) { /* ... */ }

/* Use :link and :visited; supported everywhere */

:link, :visited { /* ... */ }
```

[cli-img]: https://img.shields.io/travis/jonathantneal/postcss-pseudo-class-any-link.svg
[cli-url]: https://travis-ci.org/jonathantneal/postcss-pseudo-class-any-link
[css-img]: https://jonathantneal.github.io/cssdb/badge/any-link-pseudo-class.svg
[css-url]: https://jonathantneal.github.io/cssdb/#any-link-pseudo-class
[git-img]: https://img.shields.io/badge/chat-gitter-blue.svg
[git-url]: https://gitter.im/postcss/postcss
[npm-img]: https://img.shields.io/npm/v/postcss-pseudo-class-any-link.svg
[npm-url]: https://www.npmjs.com/package/postcss-pseudo-class-any-link

[`:any-link`]: http://dev.w3.org/csswg/selectors/#any-link-pseudo
[`:link`]: http://dev.w3.org/csswg/selectors/#link-pseudo
[`:visited`]: http://dev.w3.org/csswg/selectors/#visited-pseudo
[:any-link]: https://github.com/jonathantneal/postcss-pseudo-class-any-link
[Gulp PostCSS]: https://github.com/postcss/gulp-postcss
[Grunt PostCSS]: https://github.com/nDmitry/grunt-postcss
[PostCSS]: https://github.com/postcss/postcss
[proposal]: http://dev.w3.org/csswg/selectors/
