LifeSaver
=========

Shorthand for all your Sass!

## Table of Contents
1. [Getting Started](#getting-started)
1. [Syntax](#syntax)
1. [Save Mixin](#save-mixin)
1. [Property Mixins](#property-mixins)
1. [Values](#values)
1. [Units](#units)
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

@include [property-mixin](values units scale flag);
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

@include size();

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

@include border();
@include border-top();
@include border-right();
@include border-bottom();
@include border-left();

@include radius();

@include position();
@include absolute();
@include fixed();
@include relative();
@include static();
@include sticky();
```

## Values
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
Lifesaver uses [Mint](http://github.com/) for it's unit processing. All of Mint's features are usable in Lifesaver. For details about how the units are processed check out Mint's readme.

Features included in Mint:
+ Value compressing
+ Value scaling
+ Em and rem converting
+ Safe converting

With Mint ems and rems are represented in pixel values based on a default base font size of 16 pixels and then converted.

```scss
div {
  @include margin(2 x x x rem);
}
```

Output:

```css
div {
  margin-top: 0.125rem;
}
```

Just like in Mint, you can also pass a scale argument. When using rems and ems, changing the `font-size` of an element affects the scale of the children. A way to overcome this is to use the scale argument.

In the code below, the `font-size` is increased but the margins remain visually the same.

```scss
div {
  font-size: em(24);
  @include margin(x 16 em 24);
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

In Lifesaver, to scale a unit-less value you have to use a `un` value instead of a length. This is needed because Lifesaver uses the length argument as a sort of delimiter so it can tell a difference between values and scales while keeping your arguments comma-less.

```scss
div {
  @include margin(x 16 un 24);
}
```

Output:

```css
div {
  margin-right: 0.75;
  margin-left: 0.75;
}
```

Just like passing multiple properties you can pass multiple units. This is useful for fallbacks. The units are output in the order you define them. Order is critical if you want your fallback units to work.

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

## Flags
Passing a flag argument tells LifeSaver to add a flag to each property it generates.

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
