# &lt;google-map-markerclusterer&gt;

> Port of [Markerclusterer-Plus](http://google-maps-utility-library-v3.googlecode.com/svn/trunk/markerclustererplus/docs/reference.html) as a Web Component using Polymer.

![Markerclusterer-Plus](https://raw.githubusercontent.com/timeu/google-map-markerclusterer/master/preview.gif "google-map-markerclusterer")

## Demo
> [Check it live](http://timeu.github.io/google-map-markerclusterer/components/google-map-markerclusterer/demo/index.html).

## Install

Install the component using [Bower](http://bower.io/):

```sh
$ bower install google-map-markerclusterer --save
```

Or [download as ZIP](https://github.com/timeu/google-map-markerclusterer/archive/master.zip).

## Usage

1. Import Web Components' polyfill:

  ```html
<script src="bower_components/webcomponentsjs/webcomponents-lite.js"></script>
  ```

2. Import Custom Element:

  ```html
<link rel="import" href="bower_components/google-map-markerclusterer/google-map-markerclusterer.html">
  ```

3. Start using it!

  ```html
  <template is="dom-bind" id="app">
    <template>
      <google-map-markerclusterer map="{{map}}"></google-map-markerclusterer>
      <google-map map="{{map}}"></google-map>
    </template>
  </template>

  <my-app></my-app>
  ```

  or using javascript:

  ```javascript
  var gmap = document.querySelector('google-map');
  gmap.addEventListener('google-map-ready', function(e) {
    document.querySelector('google-map-markerclusterer').map = this.map;
  });
  ```


## Options

See the [component page](http://timeu.github.io/google-map-markerclusterer) for more information.


##Custom markers

Instead of the default markers `<google-map-marker>` also custom markers can be used by implementing the behavior: `Markerclusterer.GoogleMapOverlayViewMarkerBehavior`

##Custom cluster markers

There are 2 ways to have custom cluster markers:

### Using the styles attribute

Pass an array of objects to the styles property of the `<google-map-markerclusterer>`:

```Javascript
var styles = [{
    url: 'http://google-maps-utility-library-v3.googlecode.com/svn/trunk/markerclustererplus/images/conv30.png',
    width: "30px",
    height: "27px",
    anchorText: ["-3px", "0px"],
    anchorIcon: ["27px", "28px"],
    textColor: '#ff00ff',
    textSize: "10px"
}, {
    url: 'http://google-maps-utility-library-v3.googlecode.com/svn/trunk/markerclustererplus/images/conv40.png',
    width: "40px",
    height: "36px",
    anchorText: ["-4px", "0px"],
    anchorIcon: ["36px", "37px"],
    textColor: '#ff0000',
    textSize: "11px"
}, {
    url: 'http://google-maps-utility-library-v3.googlecode.com/svn/trunk/markerclustererplus/images/conv50.png',
    width: "50px",
    height: "45px",
    anchorText: ["-5px", "0px"],
    anchorIcon: ["45px", "46px"],
    textColor: '#0000ff',
    textSize: "12px"
}]
```

```Html
<google-map-markerclusterer styles="{{styles}}"></google-map-markerclusterer>
```
or using javascript:

```Javascript
var markerclusterer = document.querySelector("google-map-markerclusterer");
markerclusterer.styles = styles;
```

###Wrapping a custom element

If the use-case is more advanced than just what the styles attribute provides, it's possible to specify a custom element as a replacement for the default cluster marker. Create a custom element (i.e `<my-element>`) that implements the `Markerclusterer.ClusterIconBehavior` behavior and add it to the `google-map-markerclusterer`.
**Important:** Make sure to add a *cluster-icon* classname to your custom cluster icon element.


```Html
<google-map-markerclusterer>
   <my-element class="cluster-icon" />
</google-map-markerclusterer>
```

The various customizations can be viewed on the [demo page](http://timeu.github.io/google-map-markerclusterer/components/google-map-markerclusterer/demo/) page.


## Browser Support

![IE](https://raw.github.com/paulirish/browser-logos/master/internet-explorer/internet-explorer_48x48.png) | ![Chrome](https://raw.github.com/paulirish/browser-logos/master/chrome/chrome_48x48.png) | ![Firefox](https://raw.github.com/paulirish/browser-logos/master/firefox/firefox_48x48.png) | ![Opera](https://raw.github.com/paulirish/browser-logos/master/opera/opera_48x48.png) | ![Safari](https://raw.github.com/paulirish/browser-logos/master/safari/safari_48x48.png)
--- | --- | --- | --- | --- |
IE 10+ ✔ | Latest ✔ | Latest ✔ | Latest ✔ | Latest ✔ |

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## History

Check [Release](https://github.com/timeu/google-map-markerclusterer/releases) list.

## License

[MIT License](http://timeu.mit-license.org/) © Ümit Seren
