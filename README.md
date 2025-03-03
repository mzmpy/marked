<a href="https://marked.js.org">
  <img width="60px" height="60px" src="https://marked.js.org/img/logo-black.svg" align="right" />
</a>

# Marked

[![npm](https://badgen.net/npm/v/marked)](https://www.npmjs.com/package/marked)
[![gzip size](https://badgen.net/badgesize/gzip/https://cdn.jsdelivr.net/npm/marked/marked.min.js)](https://cdn.jsdelivr.net/npm/marked/marked.min.js)
[![install size](https://badgen.net/packagephobia/install/marked)](https://packagephobia.now.sh/result?p=marked)
[![downloads](https://badgen.net/npm/dt/marked)](https://www.npmjs.com/package/marked)
[![github actions](https://github.com/markedjs/marked/workflows/Tests/badge.svg)](https://github.com/markedjs/marked/actions)
[![snyk](https://snyk.io/test/npm/marked/badge.svg)](https://snyk.io/test/npm/marked)

- ⚡ built for speed
- ⬇️ low-level compiler for parsing markdown without caching or blocking for long periods of time
- ⚖️ light-weight while implementing all markdown features from the supported flavors & specifications
- 🌐 works in a browser, on a server, or from a command line interface (CLI)

## Statement

This is a project that forked from [marked](https://github.com/markedjs/marked). [Katex](https://github.com/KaTeX/KaTeX) 
is be introduced into it for supporting rendering latex. User should be noticed that the package is not be tested for the 
part of using katex. So it should be only used for individual purpose.

## Demo

Checkout the [demo page](https://marked.js.org/demo/) to see marked in action ⛹️

## Docs

Our [documentation pages](https://marked.js.org) are also rendered using marked 💯

Also read about:

* [Options](https://marked.js.org/#/USING_ADVANCED.md)
* [Extensibility](https://marked.js.org/#/USING_PRO.md)

## Compatibility

**Node.js:** Only [current and LTS](https://nodejs.org/en/about/releases/) Node.js versions are supported. End of life Node.js versions may become incompatible with Marked at any point in time.

**Browser:** Not IE11 :)

## Installation

**CLI:** 

```sh 
npm install -g marked
```

**In-browser:** 

```sh
npm install marked
npm install @types/marked # For TypeScript projects
```

## Usage

### Warning: 🚨 Marked does not [sanitize](https://marked.js.org/#/USING_ADVANCED.md#options) the output HTML. Please use a sanitize library, like [DOMPurify](https://github.com/cure53/DOMPurify) (recommended), [sanitize-html](https://github.com/apostrophecms/sanitize-html) or [insane](https://github.com/bevacqua/insane) on the *output* HTML! 🚨

```
DOMPurify.sanitize(marked.parse(`<img src="x" onerror="alert('not happening')">`));
```

**CLI**

``` bash
# Example with stdin input
$ marked -o hello.html
hello world
^D
$ cat hello.html
<p>hello world</p>
```

```bash
# Print all options
$ marked --help
```

**Browser**

```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8"/>
  <title>Marked in the browser</title>
</head>
<body>
  <div id="content"></div>
  <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
  <script>
    document.getElementById('content').innerHTML =
      marked.parse('# Marked in the browser\n\nRendered by **marked**.');
  </script>
</body>
</html>
```

**Used to render katex(should used with bundler like webpack concurrently)**
```javascript
import { marked } from '@npmzm/marked'
import 'katex/dist/katex.css'

const html = marked('There are some Greek letter `$\alpha$`, `$\beta$` and `$\lambda$`.\n\n```katex\nE = mc^{2}\n```')
```

**Used to render katex in browser**
```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Marked with Katex in the browser</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.4/dist/katex.css" integrity="sha384-ko6T2DjISesD0S+wOIeHKMyKsHvWpdQ1s/aiaQMbL+TIXx3jg6uyf9hlv3WWfwYv" crossorigin="anonymous">
  </head>
  <body>
    <div id="content"></div>
  </body>
  <script src="https://cdn.jsdelivr.net/npm/katex@0.16.4/dist/katex.js" integrity="sha384-tsPOhveNsi36uhglzMBNOAA2xd7LlEqQuQHFKi4DwP+6UKrrLGub1MD77Zx18F8e" crossorigin="anonymous"></script>
  <script type="text/javascript" src="./marked/marked.min.js"></script>
  <script type="text/javascript">
    document.getElementById('content').innerHTML = marked.marked('There are some Greek letter \`\$\\alpha\$\`, \`\$\\beta\$\` and \`\$\\lambda\$\`.\n\n\`\`\`katex\nE = mc^{2}\n\`\`\`')
  </script>
</html>
```

## License

Copyright (c) 2011-2022, Christopher Jeffrey. (MIT License)
