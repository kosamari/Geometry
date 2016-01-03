Distance between Two Points
===

### Basic concept
Distance `r` between point `K` and point `L` is calculated as follows.

![equation](http://www.sciweavers.org/tex2img.php?eq=r%20%3D%20%20%5Csqrt%7B%20%28xL%20-%20%20xK%29%5E%7B2%7D-%28yL%20-%20%20yK%29%5E%7B2%7D%20%20%7D%20&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

```javascript
function distance(xL, yL, xK, yK){
  const xLK = xL - xK
  const yLK = yL - yK
  const rsq = Math.pow(xLK,2) + Math.pow(yLK,2)
  const r = Math.sqrt(rsq)
  return r
}
```

### Check if line is shorter than the reference line
If `|xK - xL|` and `|yK - yL|` is less than that of reference line, we can say the line is shorter than the reference line.

```javascript
// let's say reference line is distance between (3,5) and (10,9)
const refX = Math.abs(3 - 10)
const refY = Math.abs(5 - 9)

function withinCheck(xL, yL, xK, yK){
  if(Math.abs(xK - xL) < refX && Math.abs(yK - yL) < refY){
    return distance(xL, yL, xK, yK)
  } else {
    return null
  }
}
```

### Check if line is longer the reference line
If `|xL - xK| + |yL - yK|` is larger than that of reference line, we can say the line is longer than the reference line.

```javascript
// let's say reference line is distance between (3,5) and (10,9)
const ref =  Math.abs(3 - 10) + Math.abs(5 - 9)

function outsideCheck(xL, yL, xK, yK){
  if ( Math.abs(xL - xK) + Math.abs(yL - yK) > ref){
    return distance(xL, yL, xK, yK)
  } else {
    return null
  }
}
```

### Other way to calculate distance
Used for very shot or very long distance calculation

```javascript
function distance(xL, yL, xK, yK){
  const xLK = Math.abs(xL - xK)
  const yLK = Math.abs(yL - yK)
  const min = Math.min(xLK, yLK)
  const max = Math.max(xLK, yLK)
  const div = min/max
  const r = max * Math.sqrt(1.0+Math.pow(div,2))
  return r
}
```
