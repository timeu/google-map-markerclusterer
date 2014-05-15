# &lt;google-map-markerclusterer&gt;

> Port of [Markerclusterer-Plus](http://google-maps-utility-library-v3.googlecode.com/svn/trunk/markerclustererplus/docs/reference.html) as a Web Component using Polymer.

![Markerclusterer-Plus](http://timeu.github.io/google-map-markerclusterer/preview.gif "google-map-markerclusterer")

## Demo
> [Check it live](http://timeu.github.io/google-map-markerclusterer/components/google-map-markerclusterer/demo.html).

## Install

Install the component using [Bower](http://bower.io/):

```sh
$ bower install google-map-markerclusterer --save
```

Or [download as ZIP](https://github.com/timeu/google-map-markerclusterer/archive/master.zip).

## Usage

1. Import Web Components' polyfill:

  ```html
<script src="bower_components/platform/platform.js"></script>
  ```

2. Import Custom Element:

  ```html
<link rel="import" href="bower_components/google-map-markerclusterer/google-map-markerclusterer.html">
  ```

3. Start using it!

  ```html
  <polymer-element name="my-app">
    <template>
      <google-map-markerclusterer map="{{map}}"></google-map-markerclusterer>
      <google-map map="{{map}}"></google-map>
    </template>
  </polymer-element>
  
  <my-app></my-app>
  ```

  or using javascript: 

  ```javascript
  var gmap = document.querySelector('google-map');
  gmap.addEventListener('api-load', function(e) {
    document.querySelector('google-map-markerclusterer').map = this.map;
  });
  ```


## Options

See the [component page](http://timeu.github.io/google-map-markerclusterer) for more information.

Attribute | Options         | Default                    | Description
---       | ---             | ---                        | ---
`map` | google.maps.Map object | null | the google-maps object
`markers`    | array (`<google-map-marker>` or `<google-map-overlayview-marker>`)    | null | The markers to be clustered
`batchSize`   | number           | `2000`                  | BatchSize specifies the amount of markers that should be processed per run.
`ignoreHidden` | boolean | false                  | If set ignores hidden markers when creating the clusters.
`gridSize`|  number | 60 | Specifies the size of the grid for each cluster in pixel.
`minimumClusterSize` | number | 2 | Sepcifies the minimum number of markers to show a cluster.
`averageCenter` | boolean | false | If set, the center of the cluster is set to the average of all locations of its containing markers.
`maxZoom` | number  |  null | Specifies the maximum zoom at which individual markers are shown.
`zoomOnClick` | boolean | true | If set, the map is zoomed far enough that all markers of the cluster fit inside the viewport.
`styles` | array of objects | null | Specifies the style (icon, offset) for the cluster markers. 

## Methods

Method     | Parameters     | Returns            | Description
---        | ---            | ---                | ---
`clearMarkers()` | None.          | Nothing.           | Removes all clusters and markers from the map and also removes all markers managed by the clsuterer.

##Events

Event      | Description
---        | ---
`clusteringbegin`  | Triggers the google-map-markerclusterer begins clustering markers.
`clusterend`    | Triggers when the google-map-markerclusterer stops clustering markers.
`clickcluster` | Triggers when a cluster is clicked.
`mouseovercluster` | Triggers when the mouse moves over a cluster.
`mouseoutcluster` | Triggers when the mouse moves out of a cluster.


##Custom markers

Instead of the default markers `<google-map-marker>` also custom markers can be used bei either 

 - extending `<google-map-overlayview-marker>` 
 - wrapping a custom-element (i.e `<my-element>` inside of a `<google-map-overlayview-marker>`)

See [demo](http://timeu.github.io/google-map-markerclusterer/components/google-map-markerclusterer/demo.html) page for an example.

##Custom cluster markers

There are 2 ways to have custom cluster markers: 

### Using the styles attribute

Pass an array of objects to the styles attribute of the `<google-map-markerclusterer>`: 

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

If the use-case is more advanced than just what the styles attribute provides, it's possible to specify a custom element as a replacement for the default cluster marker. There are two ways to do that: 
 - extend `<google-map-clustericon>` element 
 - wrapping a custom-element (i.e `<my-element>` inside of a `<google-map-clustericon>`)

```Html
<google-map-markerclusterer>
   <google-map-clustericon>
       <my-element />
   </google-map-clustericon>
</google-map-markerclusterer>
```
There is an example on the [demo](http://timeu.github.io/google-map-markerclusterer/components/google-map-markerclusterer/demo.html) page.



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
