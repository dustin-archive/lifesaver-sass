LifeSaver
=========

Shorthand for all your Sass!

Note: If a shorthand mixin for Sass seems silly to you when you have to type out a giant `@include` statement before your properties and also wrap them up in parenthesis, check out the presass-lifesaver project for PostCSS, which takes care of this problem.

Note: Sass v4 might include a shorter syntax for includes, which would make this set of mixins dramatically more plausible to use. See the github issue ######.

## Table of Contents

1. [Getting Started](#getting-started)
1. [Syntax](#syntax)
1. [Save Mixin](#save-mixin)
1. [Property Mixins](#property-mixins)
1. [Values](#values)
1. [Units](#units)
1. [Unit Functions](#units-functions)
1. [Convert Functions](#convert-functions)
1. [Flags](#flags)

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

There are two ways to use LifeSaver.

```scss
@include save(properties values units style color scale flag);

@include property(values units scale flag);
```

## Save Mixin

The `save` mixin is the core of LifeSaver. It's mean to be as generic as possible. Because it's generic, it allows you to use multiple properties at once.

Input:

```scss
div {
  @include save(margin padding 16px);
}
```

Output:

```css
div {
  margin: 16px;
  padding: 16px;
}
```

## Property Mixins

While the `save` mixin is generic, property mixins offer extended functionality unique to each property.

Input:

```scss
div {
  @include size(2 4 px);
}
```

Output:

```css
div {
  width: 2px;
  height: 4px;
}
```

These are all the LifeSaver mixins:


```scss
@include save();

@include size();
@include min-size();
@include max-size();

@include width();
@include min-width();
@include max-width();

@include height();
@include min-height();
@include max-height();

@include margin();
@include padding();
@include border();
@include radius();

@include position();
@include absolute();
@include fixed();
@include relative();
@include static();
@include sticky();
```

## Values

In LifeSaver values work the same as CSS except in two ways: null values and unit position.

When passing a null value, LifeSaver splits the properties up and doesn't output the property with the null value.

If brevity is your thing, you can use x as null.

Input:

```scss
div {
  @include margin(1px null 3px 4px);
}

div {
  @include margin(1px x 3px 4px);
}
```

Output:

```css
div {
  margin-top: 1px;
  margin-bottom: 3px;
  margin-left: 4px;
}

div {
  margin-top: 1px;
  margin-bottom: 3px;
  margin-left: 4px;
}
```

For further brevity you also have the option to separate the unit declaration from the values.

Input:

```scss
div {
  @include margin(1 x 3 4 px);
}
```

Output:

```css
div {
  margin-top: 1px;
  margin-bottom: 3px;
  margin-left: 4px;
}
```

## Units

Just like passing multiple properties you can pass multiple units. This is useful for fallbacks.

With LifeSaver ems and rems are represented in pixel values based on a base font size of 16 pixels and then converted during compilation.

Note: the units are output in the order you define them. Order is critical if you want your fallback units to work.

```scss
div {
  @include margin(2 px rem);
}
```

Output:

```css
div {
  margin: 2px;
  margin: 0.125rem;
}
```

## Unit Functions

You can pass strings or null values to any unit function without errors. This is useful when you're storing values in variables.

```scss
// Input
$margin: auto;
$padding: null;

div {
  margin: em($margin);
  padding: em($padding);
  background: orange;
}

// Output
div {
  margin: auto;
  background: orange;
}
```

When using rems and ems, changing the `font-size` of an element affects the scale of the children. A way to overcome this without using an extra element is to use the scale argument in a unit function. An `x` unit is used to show that it's a scale.

In the code below, the `font-size` is increased but the margins remain visually the same.

```scss
div {
  font-size: em(24);
  margin: em(16, 24x);
}
```

Output:

```css
div {
  font-size: 1.125em;
  margin: 0.75em;
}
```

The `save` mixin also includes a check for the use of scale arguments.

```scss
div {
  font-size: em(24);
  @include margin(x 16 em 24x);
}
```

Output:

```css
div {
  font-size: 1.125em;
  margin-right: 0.75em;
  margin-left: 0.75em;
}
```

Here's a list of all of LifeSaver's unit functions:

```
px()
em()
rem()
pct()
vw()
vh()
```

## Convert Functions

Convert functions are for safely converting units to help prevent rounding errors.

Note: While the effectiveness of this may vary from browser to browser, it certainly can't hurt anything.

Here's a list of the convert functions:

```scss
convert();
safe();

ceil-convert();
floor-convert();
round-convert();
safe-convert();
```

These unit functions use `safe-convert`:

```scss
un();
em();
rem();
```

This unit function uses `safe`:

```scss
px();
```

These unit functions don't use `safe` or `safe-convert` because it's not necessary:

```scss
pct();
vw();
vh();
```

## Flags

Passing a flag argument tells LifeSaver to apply a flag to each property it generates.

Input:

```scss
.warning {
  @include margin(2 4 x 16 em !important);
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
