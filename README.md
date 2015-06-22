LifeSaver - 1.0.6
=========

Shorthand for all your Sass!



## Table of Contents

1. [Getting Started](#getting-started)
1. [Syntax](#syntax)
1. [Core Mixin](#core-mixins)
1. [Shorthand Property Mixins](#shorthand-property-mixins)
1. [Values](#values)
1. [Units](#units)
1. [Skipping](#skipping)
1. [Safe Units](#safe-units)
1. [Scale Compensation](#scale-compensation)
1. [Flags](#flags)
1. [Using LifeSaver as a Property Compressor](#using-lifesaver-as-a-property-compressor)



## Getting Started

Import LifeSaver into your project at the top of your Sass modules file (or whatever).

```scss
@import 'modules/lifesaver/main';
```

For the sake of convenience I've also included an all-in-one version of LifeSaver, in which case you would do this (or whatever).

```scss
@import 'modules/lifesaver-all-in-one';
```



## Syntax

There are two ways to use LifeSaver. You can either use the core mixin or a shorthand property mixin.

```scss
@include ls([properties], [values], [units], [scale compensation], [flag]);
@include margin([values], [units], [scale compensation], [flag]);
```



## Core Mixin

The core mixin is where all the hard work is done. The advantage of using just the core mixin directly instead of a shorthand property mixin is the ability to use multiple properties. A possible use case for this is a button where you want the same amount of padding and margin on the inside and outside.

Input:

```scss
@include ls(margin padding, 2 4 x 16, px rem);
```

Output:

```css
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
```

The disadvantage to this is that you can't pass any of the shorthand property values like `size` or `position-absolute` to the core mixin. All shorthand property logic is stored inside that property's mixin. This keeps the compile time quick and the code clean and maintainable.



## Shorthand Property Mixins

LifeSaver comes with it's own set of shorthand properties to keep your code even smaller and more readable.

Input:

```scss
@include margin(2 4 x 16, px rem);
```

Output:

```css
margin-top: 2px;
margin-right: 4px;
margin-left: 16px;
margin-top: 0.125rem;
margin-right: 0.25rem;
margin-left: 1rem;
```

The only disadvantage with using shorthand property mixins is that you can no longer use multiple properties. If you find yourself needing a specific combination often you can easily create your own property mixin.

Here's a list of all of the shorthand property mixins:

```scss
@include size();
@include min-size();
@include max-size();

@include margin();
@include padding();

@include border-width();
@include border-radius();

@include position();
@include position-absolute();
@include position-fixed();
@include position-inherit();
@include position-relative();
@include position-static();
@include position-sticky();

@include radius();

@include absolute();
@include fixed();
@include relative();
@include static();
@include sticky();
````



## Values

LifeSaver can take any value that can be used in CSS including strings like `auto` and `inherit`.



## Units

Just like how you can pass multiple properties to LifeSaver you can also pass multiple units. This is useful when you're coding a website that needs to use new standards but is also still compatible with older browsers. For example browsers don't support the `rem` unit, so here is how you might want to use a `px` fallback:

```scss
@include margin(2 x x x, px rem);
```

Output:

```css
margin-top: 2px;
margin-top: 0.125rem;
```

Since older browsers won't recognize the `rem` they will just throw it out and use the previous `px` value instead. In newer browsers the `rem` will simply override the `px`. Here's a list of all the units you can pass to LifeSaver:

```
px
em
rem
pct
vw
vh
```



## Skipping

In CSS there's a common problem when using the shorthand syntax, which is that you can't skip a value. In order to use the shorthand syntax in CSS you must define all the values. With LifeSaver you can skip values all you'd like by passing an `x` or `null` value.

Input:

```scss
@include margin(x auto);
```

Output:

```css
margin-left: auto;
margin-right: auto;
  ```



## Safe Units

LifeSaver has a set of functions for safely converting units to help prevent browser rounding errors that could potentially break a design.

Here's a list of all the safe unit functions:

```
scale-comp([value], [scale]);

convert([value]);
safe([value]);
ceil-convert([value]);
floor-convert([value]);
round-convert([value]);
safe-convert([value]);

un([value], [scale]);
em([value], [scale]);
rem([value], [scale]);
px([value], [scale]);
pct([value], [scale]);
vw([value], [scale]);
vh([value], [scale]);

floor-un([value]);
floor-em([value]);
floor-rem([value]);
floor-px([value]);

round-un([value]);
round-em([value]);
round-rem([value]);
round-px([value]);
```



## Scale Compensation

A common problem when using units like rem and em is that when you change the font size of an element it also changes anything else sized with rem and em. To circumvent this, leaving your margins visually the same, you can pass a scale compensation argument equal to the font size.

Input:

```scss
font-size: em(18);
@include margin(2 4 x 16, em, 18);
```

Output:

```css
font-size: 1.125em;
margin-top: 0.125em;
margin-right: 0.25em;
margin-left: 1em;
```



## Flags

Passing a flag argument tells LifeSaver to apply a flag to each property it generates.

Input:

```scss
@include margin(2 4 x 16, em, x, !important);
```

Output:

```css
margin-top: 0.125em !important;
margin-right: 0.25em !important;
margin-left: 1em !important;
```

If you only want to add a flag to only one of these generated properties, you'll have to add another include with only the value you want to add the flag to.

If you don't want to define scale compensation, but you want to pass a flag argument, you can do one of two things:

1. You can set the scale compensation to `x` or `null` telling LifeSaver to ignore this argument.
1. Pass the flag argument using the `$flag` variable as shown below.

```scss
@include margin(1 2, em, $flag: !important);
```



## Using LifeSaver as a Property Compressor

It's easy to incorporate LifeSaver into your own mixins. Doing this allows you to get all the benefits of LifeSaver, like compressing multiple properties into one shorthand property, safe units, and font size scale compensation, without having to redo any of the work.

Here's a real world example mixin that uses LifeSaver as a property compressor:

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

In this mixin, if you pass the arguments: `top right bottom left`, the output would look like this:

```css
display: inline-block;
border-style: solid;
border-color: #1f2327;
padding: 4px 8px;
border-width: 4px 8px;
```
