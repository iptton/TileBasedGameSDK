摘自[http://www.whatwg.org/specs/web-apps/current-work/multipage/the-canvas-element.html]

`getContext('2d')` 获取2d上下文;


### state

`state`包括以下信息：

	transformation matrix(变换矩阵）
	clipping region
	strokeStyle, fillStyle, globalAlpha, 
	lineWidth, lineCap, lineJoin, 
	miterLimit, shadowOffsetX, shadowOffsetY, 
	shadowBlur, shadowColor, 
	globalCompositeOperation, 
	font, textAlign, textBaseline


- save()
- restore()


### DrawingStyle Objects

*线条样式*

- lineWidth value: number
- lineCap  values: [butt,round,square]
- lineJoin values: [bevel,round,miter]

*文本样式*

- font
- textAlign values: [start,end,left,right,center]
- textBaseLine values: [alphabetic,top,middle,ideographic,bottom]

*路径*

- moveTo(x, y)
- closePath()
- lineTo(x, y)
- quadraticCurveTo(cpx, cpy, x, y)
- bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)
- arcTo(x1, y1, x2, y2, radiusX [, radiusY, rotation ]) (绘制 [x0,y0,x1,y1]与[x1,y1,x2,y2] 切圆的一段弧)
- arc(x, y, radius, startAngle, endAngle [, anticlockwise ] )
- ellipse(x, y, radiusX, radiusY, rotation, startAngle, endAngle, anticlockwise)
- rect(x, y, w, h)

*变换 transformations*

- currentTransform 
- scale(x, y)
- rotate(angle)
- translate(x, y)
- setTransform(a, b, c, d, e, f) //直接赋值
- transform(a, b, c, d, e, f);   //以相乘结果赋值
- resetTransform()

*填充及笔触样式 Fill and stroke style*
- fillStyle     values: CSS color, or a CanvasGradient or CanvasPattern
- strokeStyle   values: CSS color, or a CanvasGradient or CanvasPattern

		CanvasGradient
		  createLinearGradient(x0, y0, x1, y1)
		  createRadialGradient(x0, y0, r0, x1, y1, r1)
		CanvasPattern
		  createPattern(image, repetition) repetition: repeat,repeat-x,repeat-y,no-repeat
		  pattern.setTransform(transform)

### 绘制距形

- clearRect(x, y, w, h)
- fillRect(x, y, w, h)
- strokeRect(x, y, w, h)

### 绘制文本

- fillText(text, x, y [, maxWidth ] )
- strokeText(text, x, y [, maxWidth ] )

		metrics = context.measureText(text)
		//Returns a TextMetrics object with the metrics of the given text in the current font.
		metrics.width
		metrics.actualBoundingBoxLeft
		metrics.actualBoundingBoxRight
		metrics.fontBoundingBoxAscent
		metrics.fontBoundingBoxDescent
		metrics.actualBoundingBoxAscent
		metrics.actualBoundingBoxDescent
		metrics.emHeightAscent
		metrics.emHeightDescent
		metrics.hangingBaseline
		metrics.alphabeticBaseline
		metrics.ideographicBaseline
		//Returns the measurement described below.

### 绘制路径

- beginPath()
- fill()
- clip() //clip前先save，clip后仅path上的元素会更新，恢复使用restore
- isPointInPath(x, y)

### 绘制图像

- drawImage(image, dx, dy)
- drawImage(image, dx, dy, dw, dh)
- drawImage(image, sx, sy, sw, sh, dx, dy, dw, dh)

### 位图操作

- createImageData(sw, sh)
- getImageData(sx, sy, sw, sh)
- putImageData(imagedata, dx, dy [, dirtyX, dirtyY, dirtyWidth, dirtyHeight ])
