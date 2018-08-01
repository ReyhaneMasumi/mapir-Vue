# Mapir Vue Component 🔥

[**Map.ir** map](http://map.ir) Vue component uses `leaflet` package as it's dependency and make creating a map using defined directives available in eas.

## Installation

---

In order to add Map.ir inside your Vue project, few steps should be followed:

### Download

install `mapir-vue` npm module as dependancy in your project:

```shell
npm i mapir-vue
```

Also install `leaflet` npm module as dependancy in your project:

```shell
npm i leaflet --save
```

### Preparation

#### CSS
Add the following stylesheets to your index.html head tag:
```css
<link 
  rel="stylesheet"
  href="https://unpkg.com/leaflet@1.3.1/dist/leaflet.css"
  integrity="sha512-ksm5RenBEKSKFjgI3a41vrjkw4EVPlJ3+OiI65vTjIdo9brlAacEuKOiQ5OFh7cOI1bkDwLqdLw3Zg0cRJAAQ=="
/>
```
### Getting started
---

#### Basic map

import vue module:
```js
import ShivehMap from 'mapir-vue'
```
Define ShivehMap component in components:
```js
'ShivehMap': ShivehMap
```

#### Using Component
Use ShivehMap component where you want

```js
<ShivehMap></ShivehMap>
```               

#### Props
You can give props to the component

```js
<ShivehMap
:lat="35"
:lng="52"
:zoom="6"
>
</ShivehMap>
```

Default prop values are

```js
:lat="33.1375"
:lng="56.2170"
:zoom="6"
```

#### Marker
Add Marker by giving a position:

```js
<ShivehMap 
:markerLatLng="[[lat1,lng1], [lat2,lng2], ...]"
>
</ShivehMap>
```
#### Popup
Add popup to your markers by giving a text:
```js
<ShivehMap 
:markerName="['marker1', 'marker2', ...]"
>
</ShivehMap>
```      
