LifeSaver
=========

Shorthand for all your Sass!


## Table of Contents

1. [Getting Started](#getting-started)
1. [Syntax](#syntax)
1. [Core Mixin](#core-mixins)
1. [Property Mixins](#property-mixins)
1. [Values](#values)
1. [Units](#units)
1. [Skipping](#skipping)
1. [Safe Units and Convert Functions](#safe-units-and-convert-functions)
1. [Scale Compensation](#scale-compensation)
1. [Flags](#flags)
1. [Extending LifeSaver](#extending-lifesaver)


## Getting Started

Install LifeSaver via Bower.

```
bower install lifesaver
```

Import LifeSaver.

```scss
@import 'bower_components/lifesaver/main';
```


## Syntax

There are two ways to use LifeSaver; the core mixin or a property mixin.

```scss
// Core
@include ls([properties], [values], [units], [scale compensation], [flag]);

// Property mixin
@include margin([values], [units], [scale compensation], [flag]);
```


## Core Mixin

The advantage of using the core instead of a property is the ability to use multiple properties at once with the same values and units. A use case for this would be a button where you want the values for margin and padding.

The disadvantage of using the core is that you can't pass any property mixins as arguments. Property mixins sometimes have have extended functionality specific to that mixin.

Input:

```scss
button {
  @include ls(margin padding, 2 4 x 16, px rem);
}
```

Output:

```css
button {
  margin-top: 2px;
  margin-right: 4px;
  margin-left: 16px;
  margin-top: 0.125rem;
  margin-right: 0.25rem;
  margin-left: 1rem;
  padding-top: 2px;
  padding-right: 4px;
  padding-left: 16px;
  padding-top: 0.125rem;
  padding-right: 0.25rem;
  padding-left: 1rem;
}
```


## Property Mixins

Property mixins aim to keep your code compressed by offering extended functionality unique to each property.

The only disadvantage with using a property mixin is that you can't use multiple properties.

Input:

```scss
button {
  @include margin(2 4 x 16, px rem);
}
```

Output:

```css
button {
  margin-top: 2px;
  margin-right: 4px;
  margin-left: 16px;
  margin-top: 0.125rem;
  margin-right: 0.25rem;
  margin-left: 1rem;
}
```

Here's a list of all of the properties:

```scss
@include width();
@include min-width();
@include max-width();

@include height();
@include min-height();
@include max-height();

@include margin();
@include margin-top();
@include margin-right();
@include margin-bottom();
@include margin-left();

@include padding();
@include padding-top();
@include padding-right();
@include padding-bottom();
@include padding-left();

@include border-width();
@include border-radius();

@include position();

@include font-size();
@include line-height();
````

```scss
@include size();
@include min-size();
@include max-size();

@include radius();

@include position-absolute();
@include position-fixed();
@include position-relative();
@include position-static();
@include position-sticky();

@include position-inherit();
@include position-initial();
@include position-unset();

@include absolute();
@include fixed();
@include relative();
@include static();
@include sticky();
```


## Values

LifeSaver can parse values that can be used in CSS including strings like `auto` and `inherit`.

Using null values in LifeSaver unit functions to prevent properties from being output will no longer cause errors and will totally work!

```scss
// Input
$margin: null;

.block {
  margin: em($margin);
  background: orange;
}

// Output
.block {
  background: orange;
}
```

Similarly this is also true for CSS strings, except the string will be output instead of nullified.

```scss
// Input
$margin: auto;

.block {
  margin: em($margin);
  background: orange;
}

// Output
.block {
  margin: auto;
  background: orange;
}
```

## Units

Just like passing multiple properties you can also pass multiple units. This is useful when you need to use new units but stay compatible with older browsers.

For example, older browsers don't support the `rem`. They will just throw out the properties using the `rem` units and use the properties using the `px` values instead. In newer browsers the `rem` will simply override the `px`.

```scss
.block {
  @include margin(2 x x x, px rem);
}
```

Output:

```css
.block {
  margin-top: 2px;
  margin-top: 0.125rem;
}
```

Here's a list of all the units you can pass to LifeSaver:

```
px
em
rem
pct
vw
vh
```


## Skipping

In CSS when using the shorthand syntax you can't skip values. In order to use the shorthand syntax in CSS you must define all the values. You *could* set a value to 0, but you might not always want to have a 0 margin or padding. You could also manually look up the previously set value, but this might not always be the same depending on the situation. With LifeSaver you can skip values all you'd like by passing an `x` or `null` value.

Note: With CSS3's `unset` this isn't necessarily true anymore, though, it's not well supported just yet.

Input:

```scss
.center {
  @include margin(x auto);
}
```

Output:

```css
.center {
  margin-left: auto;
  margin-right: auto;
}
```


## Safe Units and Convert Functions

LifeSaver has a set of functions for safely converting units to help prevent browser rounding errors that could potentially break a design.

Note: While the effectiveness of this may vary from browser to browser, it certainly can't hurt anything.

Here's a list of all the unit and convert functions:

```
convert([value]);
safe([value]);

ceil-convert([value]);
floor-convert([value]);
round-convert([value]);
safe-convert([value]);

// These functions automatically use the `safe-convert` function internally:
un([value], [scale]);
em([value], [scale]);
rem([value], [scale]);

// This function automatically uses the `safe` function internally:
px([value], [scale]);

// These functions don't use the `safe-convert` function because it's not necessary.
pct([value], [scale]);
vw([value], [scale]);
vh([value], [scale]);
```


## Scale Compensation

When using units like rem and em, when you change the font size of an element it also effects other properties that use rem and em. To circumvent this, leaving your units visually the same, you can pass a scale compensation argument equal to the font size.

Input:

```scss
.bigger-font-only {
  font-size: em(24);
  @include margin(2 4 x 16, em, 24);
}
```

Output:

```css
.bigger-font-only {
  font-size: 1.125em;
  margin-top: 0.08203125em;
  margin-right: 0.16796875em;
  margin-left: 0.75em;
}
```


## Flags

Passing a flag argument tells LifeSaver to apply a flag to each property it generates.

If you only want to add a flag to only one of the generated properties, you'll have to add another include with only the value you want to add the flag to or just use regular CSS for these one-off cases.

Input:

```scss
.warning {
  @include margin(2 4 x 16, em, x, !important);
}
```

Output:

```css
.warning {
  margin-top: 0.125em !important;
  margin-right: 0.25em !important;
  margin-left: 1em !important;
}
```

If you don't want to define scale compensation, but you want to pass a flag argument, you can do one of two things:

1. You can set the scale compensation to `x` or `null` telling LifeSaver to ignore this argument.
2. Pass the flag argument using the `$flag` variable as shown below.

```scss
.warning {
  @include margin(1 2, em, $flag: !important);
}
```


## Extending LifeSaver

Incorporating LifeSaver into your own mixins allows you to get all the benefits of LifeSaver, like compressing multiple properties into one property, multiple properties, multiple units, safe units, and font size scale compensation.

Here's an example that takes advantage of LifeSaver's property compression.

```scss
@mixin line($side, $color: black, $style: solid, $padding: 4) {
  display: inline-block;
  border-style: $style;
  border-color: $color;

  $p1: $padding;
  $p2: $padding * 2;

  $t: null;
  $r: null;
  $b: null;
  $l: null;

  @if index($side, box) {
    $t: $p1;
    $r: $p2;
    $b: $p1;
    $l: $p2;
  }
  @else {
    $t: if(index($side, top), $p1, null);
    $r: if(index($side, right), $p2, null);
    $b: if(index($side, bottom), $p1, null);
    $l: if(index($side, left), $p2, null);
  }

  @include padding($t $r $b $l, px);
  @include border-width($t $r $b $l, px);
}
```
