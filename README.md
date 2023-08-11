# Grapesjs Links

All the links you need for multi-paged GrapesJs

[DEMO](https://codepen.io/lexoyo/full/oNQrGRM)

### Overview

This GrapesJS plugin, named "internal-links", provides functionality for managing internal links within a GrapesJS project. It allows users to set links to different types such as URL, Email, and Page. The plugin also updates links when a page link changes and marks links as issues if a page is removed.

### Installation

To use this plugin, you need to import it and add it to your GrapesJS initialization:

```typescript
import { internalLinksPlugin } from 'path-to-plugin/internal-links';

grapesjs.init({
    // ... other GrapesJS options
    plugins: [internalLinksPlugin],
});
```

Features

1. **Link Types**: The plugin supports different link types including:
   - URL
   - Email
   - Page

2. **Automatic Link Updates**: If a page's name changes, all links pointing to that page will be automatically updated.

3. **Error Handling**: If a page is removed, all links pointing to that page will be marked as issues.

4. **Custom UI**: The plugin provides a custom UI as a trait for setting and managing links, making it intuitive for users to set link types and attributes.

### Overview

The GrapesJS Internal Links Plugin is designed to ensure the integrity of internal links even when pages are renamed or deleted. This section provides insights into how the plugin manages these scenarios.

### Page Renaming

When a page is renamed:

1. **Automatic Link Updates**: The plugin automatically scans all the links within the project.
2. If a link is found that points to the renamed page using its old name, the link is updated to use the new page name.
3. This ensures that links remain valid and functional even after a page is renamed.

### Page Deletion

When a page is deleted:

1. **Link Integrity Check**: The plugin checks all the links to see if any of them point to the deleted page.
2. **Issue Reporting**: Links that point to the deleted page are considered "issues". These problematic links are collected into an array.
3. **Error Handling with `onError`**: If there are any links in the issues array, the `onError` callback is triggered. This callback can be customized to handle these issues in a manner that suits your project's needs. For instance:
   - Display a warning to the user informing them of broken links.
   - Automatically remove or disable the problematic links.
   - Log the issues for debugging or further action.

### HTML
```html
<link href="https://unpkg.com/grapesjs/dist/css/grapes.min.css" rel="stylesheet">
<script src="https://unpkg.com/grapesjs"></script>
<script src="https://unpkg.com/@silexlabs/grapesjs-links"></script>

<div id="gjs"></div>
```

### JS
```js
const editor = grapesjs.init({
	container: '#gjs',
  height: '100%',
  fromElement: true,
  storageManager: false,
  plugins: ['@silexlabs/grapesjs-links'],
});
```

### CSS
```css
body, html {
  margin: 0;
  height: 100%;
}
```


## Summary

* Plugin name: `@silexlabs/grapesjs-links`
* Trait to turn any element into a link

## Options

| Option | Description | Default |
|-|-|-
| `onError` | Description option | - |



## Download

* CDN
  * `https://unpkg.com/@silexlabs/grapesjs-links`
* NPM
  * `npm i @silexlabs/grapesjs-links`
* GIT
  * `git clone https://github.com/silexlabs/@silexlabs/grapesjs-links.git`



## Usage

Directly in the browser
```html
<link href="https://unpkg.com/grapesjs/dist/css/grapes.min.css" rel="stylesheet"/>
<script src="https://unpkg.com/grapesjs"></script>
<script src="path/to/@silexlabs/grapesjs-links.min.js"></script>

<div id="gjs"></div>

<script type="text/javascript">
  var editor = grapesjs.init({
      container: '#gjs',
      // ...
      plugins: ['@silexlabs/grapesjs-links'],
      pluginsOpts: {
        '@silexlabs/grapesjs-links': {
           onError: components => console.log('These components are links to pages which have been deleted', components)
	}
      }
  });
</script>
```

Modern javascript
```js
import grapesjs from 'grapesjs';
import plugin from '@silexlabs/grapesjs-links';
import 'grapesjs/dist/css/grapes.min.css';

const editor = grapesjs.init({
  container : '#gjs',
  // ...
  plugins: [plugin],
  pluginsOpts: {
    [plugin]: { /* options */ }
  }
  // or
  plugins: [
    editor => plugin(editor, { /* options */ }),
  ],
});
```



## Development

Clone the repository

```sh
$ git clone https://github.com/silexlabs/@silexlabs/grapesjs-links.git
$ cd @silexlabs/grapesjs-links
```

Install dependencies

```sh
$ npm i
```

Start the dev server

```sh
$ npm start
```

Build the source

```sh
$ npm run build
```



## License

MIT
