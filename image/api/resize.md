# resize — Resize current image

## Description
    
> public Intervention\Image\Image resize ( integer $width, integer $height, [Closure $callback] )

Resizes current image based on given **width** and/or **height**. To contraint the resize command, pass an optional Closure **callback** as third parameter.
    
## Parameters

### width
The new width of the image

### height
The new height of the image

### callback (optional)

Closure callback defining constraints on the resize. It's possible to contraint the **aspect-ratio** and/or a unwanted **upsizing** of the image. See examples below.

#### aspectRatio

> public Intervention\Image\Size aspectRatio()

Constraint the current aspect-ratio if the image.

#### upsize

> public Intervention\Image\Size upsize()

Keep image from being upsized.

    
## Return Values
Resized instance of Intervention\Image

## Examples

```php
// create instance
$img = Image::make('public/foo.jpg')

// resize image to fixed size
$img->resize(300, 200);

// resize only the width of the image
$img->resize(300, null);

// resize only the height of the image
$img->resize(null, 200);

// resize the image to a width of 300 and constrain aspect ratio (auto height)
$img->resize(300, null, function ($constraint) {
    $constraint->aspectRatio();
});

// resize the image to a height of 200 and constrain aspect ratio (auto width)
$img->resize(null, 200, function ($constraint) {
    $constraint->aspectRatio();
});

// prevent possible upsizing
$img->resize(null, 400, true, function ($constraint) {
    $constraint->aspectRatio();
    $constraint->upsize();
});
```

## See also

- [widen](/api/widen)
- [heighten](/api/heighten)
- [fit](/api/fit)
- [resizeCanvas](/api/resizeCanvas)
- [crop](/api/crop)
- [trim](/api/trim)
