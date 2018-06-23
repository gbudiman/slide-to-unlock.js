# slide-to-unlock.js
Slide To Unlock with Promise

# Usage
## Including
Include `jQuery` and `Bootstrap`
```html
<script type='text/javascript' src='https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js'></script>
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css" integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp" crossorigin="anonymous">
<script type='text/javascript' src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>
```

Then include `slide-to-unlock.js` and `and slide-to-unlock.css`
```html
<script type='text/javascript' src='slide-to-unlock.js'></script>
<link rel="stylesheet" href='slide-to-unlock.css'>
```

## DOM Setup
```html
<div id='slider-1'></div>
```

## Very Basic Example: Activating
Call ```init()``` and pass the DOM referrer
```javascript
var slider_1 = SlideToUnlock.init('#slider-1')
```

That's it!

![Basic Usage](https://github.com/gbudiman/slide-to-unlock.js/blob/master/img/basic_usage.png)

# Technical Details
SlideToUnlock has 4 states:
- ```disabled```
- ```idle```
- ```slid```
- ```done```

Object enters ```slid``` state when the slider touches the right-end of the bar. You can then perform asynchronous function calls or ```Promise``` which must be ```then()```-able. On fulfillment, the object then enters ```done``` state.

## Options
Pass options as a hash like the following:
```javascript
var slider_1 = SlideToUnlock.init('#slider-1', {
  text_idle: 'Idling...',
  func_slid: function() {
    return new Promise((resolve, reject) => {
      // do AJAX things
      // Recommended to pass return value in one hash
      resolve({ success: true })
    }
  }
})
```

Full list of options:
- ```height: h.height || 64,```
- ```font_size: (h.font_size || 24)```
- ```margin_top: (h.margin_top || -48)```
- ```text_idle: h.text_idle || 'Slide To Unlock &raquo'```
- ```text_disabled: h.text_disabled || 'This element is disabled'```
- ```text_slid: h.text_slid || 'Unlocking...'```
- ```text_done: h.text_done || 'Unlocked'```
- ```func_slid: h.func_slid```
- ```func_done: h.func_done```
- ```style_bg_done: h.style_bg_done || '#337ab7'```
- ```style_color_done: h.style_color_done || '#fff'```
- ```style_bg_slid: h.style_bg_slid || '#ffbb33'```
- ```style_color_slid: h.style_color_slid || '#fff'```
- ```style_bg_idle: h.style_bg_idle || '#eee'```
- ```style_color_idle: h.style_color_idle || '#333'```
- ```style_bg_disabled: h.style_bg_disabled || '#ccc'```
- ```style_color_disabled: h.style_color_disabled || '#888'```
- ```start_disabled: h.start_disabled || false```

```func_slid``` and ```func_done``` **MUST** be a ```Promise``` object and be ```then()```-able. You can pass a single object with arbitrary members that can be passed around to each state transitions' event handlers.

## Methods
```init()``` returns a DOM element, not a ```jQuery``` object of DOM arrays
```javascript
var slider_1 = SlideToUnlock.init('#slider-1')
slider_1.slider_enable(false)
slider_1.set_slid_text('Fully slid...')
```

Full list of recommended methods to manipulate object:
- ```slider_reset()```
- ```slider_enable(bool)```
- ```slider_toggle()```
- ```set_slid_text(string)```
- ```set_done_text(string)```

## Events
```javascript
var slider_1 = SlideToUnlock.init('#slider-1')
$(slider).on('slider-slid', function(event, data) {
  // consume data
})
```

Full list of events:
- ```slider-hit```, parameters: ```None```. Triggered when the slider hits the right-edge
- ```slider-slid```, parameters: ```data```. Triggered once func_slid() is fulfilled
- ```slider-done```, parameters: ```data```. Triggered once func_done() is fulfulled
