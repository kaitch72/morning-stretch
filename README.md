# morning-stretch

# Morning Stretch

A single-page stretch timer: pick your poses, hit start, and it runs pose → transition → pose → … until the routine's done. No ads, no video buffering, no parts you don't like.

It's one file (`index.html`) with everything inline — no build step, no dependencies to install.

## Try it locally

Double-click `index.html` and it opens in your browser. That's it.

## Add your own photos

Create a `poses` folder next to `index.html` and drop your photos in, then point each pose at its file inside `index.html`:

```js
{ id: "neck-side", name: "Neck Side Stretch", sides: true, image: "poses/neck-side.jpg" }
```

If a photo is missing, the app just shows a plain placeholder instead of breaking — so you can add photos gradually.

**Use your own photos, not screenshots from the YouTube video** — those images belong to the creator.

## Edit the routine

Near the top of the `<script>` tag in `index.html` there's a `POSES` array. Add, remove, or reorder poses freely:

```js
var POSES = [
  { id: "neck-side", name: "Neck Side Stretch", sides: true, image: "poses/neck-side.jpg" },
  // ...
];
```

- `sides: true` automatically splits a pose into a "Left side" step and a "Right side" step.
- `id` just needs to be unique — it's used to remember which poses you've turned off.

Two constants control timing for the whole routine:

```js
var POSE_SECONDS = 30;
var TRANSITION_SECONDS = 5;
```

People using the page can also uncheck poses they don't want from the "Customize routine" list on the start screen — that choice is remembered in the browser (`localStorage`), so nothing needs to be re-coded for a quick tweak.

## Other things it does

- Announces each pose out loud (Web Speech API) so you don't have to keep glancing at the screen.
- Keeps the screen from auto-locking while a routine is running (Wake Lock API, where the browser supports it).
- Pause, skip, and restart controls.
- Works fine on a phone screen.

## Host it on GitHub Pages (free)

1. Create a new GitHub repository (e.g. `morning-stretch`).
2. Add `index.html` (and your `poses` folder, if you made one) to the repo, then commit and push.
3. On GitHub, go to **Settings → Pages**.
4. Under "Build and deployment", set **Source** to "Deploy from a branch", pick the `main` branch and `/ (root)` folder, then save.
5. GitHub gives you a URL like `https://yourusername.github.io/morning-stretch/` within a minute or two — bookmark that on your phone or add it to your home screen for a one-tap morning routine.