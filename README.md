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
```html
var slider_1 = SlideToUnlock.init('#slider-1')
```
