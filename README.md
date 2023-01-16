# sveltekit-web-app
Sveltekit example on importing javascript files for web application.

src/routes/+page.svelte
```html
<script>
    import Compo from './compo.svelte';
    import * as lib from './utils';
    import { generateHeader } from '/src/js/app.js';
</script>

{@html generateHeader()}
<Compo {lib}/>
<canvas on:mousedown={lib.log} id="canvas" style="border:1px solid"></canvas>
```

src/routes/utils.js
```js
export function log(evt) {
    console.log(evt.target)
}
```

src/routes/compo.svelte
```html
<script>
    export let lib;
</script>

<button on:click={lib.log}>Click</button>
```

src/js/app.js
```js
export function generateHeader() {
    return buildHeader()
}

function buildHeader() {
    return '<h1>Header</h1>'
}
```
