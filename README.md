# svg.intersections.js
Intersections plugin for svg.js

AMD and CommonJS supported.
 
You can also include a compiled version in ./dist folder.
It will add a global `SVGIntersections`

## Usage

```javascript
var draw = SVG('drawing').size(400, 400),
    line  = draw.line(19, 127, 252, 386).stroke('blueviolet'),
    path  = draw.path('M140 45 L 12 250').stroke('darkorange'),
    intersectionPoints;
```
Then

```javascript
intersectionPoints = path.intersectsLine(line);
```
Or

```javascript
intersectionPoints = line.intersectsPath(path);
```

Result

```javascript
[ 
    {
        x: 62.453914292554465,
        y: 175.3028489346421
    }
]
```

When checking with a path, first it splits it into line segments and checks a line-line intersection.

`segmentLength` specifies the lengs of a segment.

Longer segment -> faster and less accurate

Be **carefull** checking intersections of two paths, with a hight accuracy it can be really slow.

### Avaliable methods

#### SVG.Path

`.intersectsLine(line [, segmentLength])`

`.intersectsPath(path [, segmentLength])`

#### SVG.Line

`.intersectsLine(line)`

`.intersectsPath(path [, segmentLength])`

## API<a name="module_SVGIntersections"></a>

## SVGIntersections

* [SVGIntersections](#module_SVGIntersections)
    * [~path_linePos(pathEl, linePos, [segmentLength])](#module_SVGIntersections..path_linePos) ⇒ <code>Array.&lt;Point&gt;</code>
    * [~linePos_linePos(line1Pos, line2Pos)](#module_SVGIntersections..linePos_linePos) ⇒ <code>Point</code> &#124; <code>undefined</code>
    * [~Position](#module_SVGIntersections..Position) : <code>Object</code>
    * [~Point](#module_SVGIntersections..Point) : <code>Object</code>

<a name="module_SVGIntersections..path_linePos"></a>

### SVGIntersections~path_linePos(pathEl, linePos, [segmentLength]) ⇒ <code>Array.&lt;Point&gt;</code>
Get intersection points for a path element and a line position.
Devides a path into line segments and finds line-to-line intersection.

**Kind**: inner method of <code>[SVGIntersections](#module_SVGIntersections)</code>  
**Returns**: <code>Array.&lt;Point&gt;</code> - - Array of intersection points  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| pathEl | <code>Object</code> |  | SVG.Path element |
| linePos | <code>Position</code> |  | Line start&end position |
| [segmentLength] | <code>Number</code> | <code>10</code> | Path segment length. Used for accuracy |

<a name="module_SVGIntersections..linePos_linePos"></a>

### SVGIntersections~linePos_linePos(line1Pos, line2Pos) ⇒ <code>Point</code> &#124; <code>undefined</code>
Get intersection point for 2 lines depending on their start&end position points.
[Original function](http://jsfiddle.net/justin_c_rounds/Gd2S2/)

**Kind**: inner method of <code>[SVGIntersections](#module_SVGIntersections)</code>  
**Returns**: <code>Point</code> &#124; <code>undefined</code> - - Intersection point or undefined  

| Param | Type | Description |
| --- | --- | --- |
| line1Pos | <code>Position</code> | First line start&end position |
| line2Pos | <code>Position</code> | Second line start&end position |

<a name="module_SVGIntersections..Position"></a>

### SVGIntersections~Position : <code>Object</code>
**Kind**: inner typedef of <code>[SVGIntersections](#module_SVGIntersections)</code>  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| x1 | <code>number</code> | Start point x |
| y1 | <code>number</code> | Start point y |
| x2 | <code>number</code> | End point x |
| y2 | <code>number</code> | End point y |

<a name="module_SVGIntersections..Point"></a>

### SVGIntersections~Point : <code>Object</code>
**Kind**: inner typedef of <code>[SVGIntersections](#module_SVGIntersections)</code>  
**Properties**

| Name | Type |
| --- | --- |
| x | <code>number</code> | 
| y | <code>number</code> | 

## Dependencies

- [svg.js](https://github.com/wout/svg.js)
- [distance-to-line-segment](https://github.com/scottglz/distance-to-line-segment)

## License

MIT