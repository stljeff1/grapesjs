---
title: Selector Manager
---

# Selector Manager

<p align="center"><img :src="$withBase('/selector-manager.jpg')" alt="GrapesJS - Selector Manager"/></p>


The [Selector] allows the reuse of styles across all of your [Components] in the project (exactly what classes do in HTML) and the main goal of the Selector Manager is to collect them and indicate the current state of the selection.

::: warning
This guide is referring to GrapesJS v0.17.28 or higher
:::

[[toc]]


## Configuration

To change the default configurations you have to pass the `selectorManager` property with the main configuration object.

```js
const editor = grapesjs.init({
  ...
  selectorManager: {
    ...
  }
});
```

Check the full list of available options here: [Selector Manager Config](https://github.com/artf/grapesjs/blob/master/src/selector_manager/config/config.js)


## Initialization

The Selector Manager starts to collect data once componenets and styles are loaded. The default UI is displayed along with the default panels provided by GrapesJS core, in case you need to setup the editor with your own panels we recommend following the [Getting Started] guide.

In the example below we init the editor with already provided components and styles.

```js
const editor = grapesjs.init({
  container: '#gjs',
  height: '100%',
  storageManager: false,
  components: `
    <div class="class-a">Element A</div>
    <div class="class-a class-b">Element A-B</div>
    <div class="class-a class-b class-c">Element A-B-C</div>
  `,
  style: `
    .class-a { color: red }
    .class-b { color: green }
    .class-c { color: blue }
  `,
});
```
Internally, the example above will provide to Selector Manager 3 selectors: `class-a`, `class-b` and `class-c`.

Without any selected component, the Selector Manager UI is hidden by default (along with the Style Manager). By selecting the `Element A-B-C` you will see the current selection of what will be actually styled.

<img :src="$withBase('/sm-selected-component.jpg')" alt="Selected component" style="display: block; margin: auto"/>

The label **Selected** indicates on which CSS query styles will be applied, so if you try to change the color of the current selection, this is what you'll get in the final code:

```css
.class-a.class-b.class-c {
  color: #483acb;
}
```





## Programmatic usage
If you need to manage your selectors programmatically you can use its [APIs][Selector API].


Below an example of commonly used methods.
```js
// ...
```





## Customization

The default UI is great for simple things, but except the possibility to tweak some CSS style, adding more complex elements requires a replace of the defualt UI.





## Events

For a complete list of available events, you can check it [here](/api/selector_manager.html#available-events).


[Selector]: </api/selector.html>
[Style Manager]: <Style-manager.html>
[Component]: </api/component.html>
[Components]: <Components.html>
[Getting Started]: </getting-started.html>
[Selector API]: </api/selector_manager.html>
[Component Definition]: <Components.html#component-definition>