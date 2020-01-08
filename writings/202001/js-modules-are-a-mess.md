# JS Modules are a Mess

Over the 2019 winter holiday, I was asked to quickly throw together a small single-page webapp using React and TypeScript. Although I had never done any rapid prototyping using this stack (and to be quite honest, it's been quite a while since I've done *any* rapid prototyping at all), I was pretty shocked at how inefficient the whole thing was. I'm not really thinking about efficiency from a performance standpoint, or even from an application bundle size standpoint. I'm thinking in terms of *human efficiency*. How much human labor should it really take to put together a simple form that merely hits a JSON endpoint and stores some data locally? I found that, when using React and TypeScript (even with an initial productivity boost from `create-react-app`), it takes quite a lot.

Not only does the React/TypeScript stack require that the human operator master an enormous amount of technical knowledge (over and above the fundamental web platform), but you'll also need to "figure out everything before you figure out anything". You'll need to decide on a state management library and the global "shape" of your application state. You'll need to figure out how events coming from the web platform are going to flow through to that state. And you'll need to think very carefully about how those changes will result in component rendering. And all of this for a simple form. It's almost enough to send one crying back to jQuery, really.

A couple of years ago, I started working on a little library called [straylight](https://github.com/zenparsing/straylight) that would allow you to inject HTML into the document using tagged template literals, like this:

```js
import { applyTemplate, html } from 'straylight';

applyTemplate('#main', html`
  <p>Hello world</p>
`);
```

As is so often the case, I later found out that some Google devs were working on the same idea in the context of their Polymer (custom elements) project. I shelved the project, even though it was basically complete, as I didn't see any point in competing with the Goog.

Anyway, this recent experience with React had me wondering: would [straylight](https://github.com/zenparsing/straylight) allow me to build a simple prototype faster? And so I began the process of rewriting the prototype using my own libraries, from the ground up.
