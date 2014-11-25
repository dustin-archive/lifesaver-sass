LifeSaver
=========

A Sass mixin that makes working with units and box model properties super easy.



## Index
1. [Benifits](#benifits)
1. [Features](#features)
1. [Getting Started](#getting-started)
1. [Syntax](#syntax)
1. [Core Mixin](#core-mixins)
1. [Shorthand Property Mixins](#shorthand-property-mixins)
1. [Values](#values)
1. [Units](#units)
1. [Skipping](#skipping)
1. [Safe Units](#safe-units)
1. [Scale Compensation](#scale-compensation)
1. [Important Flag](#important-flag)



## Benifits

1. Type less
1. Quicker to edit values
1. Cleaner, shorter code
1. Less math
1. Circumvent browser rounding errors
1. Could replace many of your existing mixins



## Features

1. Multiple properties
1. Longhand or shorthand values
1. Skippable values
1. Multiple units
1. Font size em scaling compensation
1. Safe unit funtions
1. Automatic shorthand output when possible
1. Important argument
1. Shorthand property mixins



## Getting Started

Import LifeSaver into your project at the top of your Sass extensions file (or whatever).

  ```scss
    @import 'extensions/lifesaver/main';
  ```



## Syntax

There's two ways to use LifeSaver. You can either use the core mixin (`ls`) or a shorthand property mixin.

  ```scss
    @include ls( [properties], [values], [units], [scale compensation], [important] );
    @include margin( [values], [units], [scale compensation], [important] );
  ```



## Core Mixin

The core mixin is what does all the magic. The advantage of using just the core mixin over the shorthand property mixins is multiple properties if you want two properties to have the same values. A possible use case for this is a "well" class, or a series of buttons, where you want the same amount of space on the insdie and outside.

  ```scss
    // Input
    @include ls( margin padding, 2 4 x 16, px rem );

    // Output
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

The disadvantage to this is that you can't pass any of the shorthand property values like `size` or `position-absolute` to the core mixin. The reason is that the core mixin is only capable of processing standard CSS to keep the code clean and maintainable. All additional shorthand property logic is stored that property's mixin.



## Shorthand Property Mixins

LifeSaver comes with it's own set of shorthand properties to keep your code small.

  ```scss
    // Input
    @include margin( 2 4 x 16, px rem );

    // Output
    margin-top: 2px;
    margin-right: 4px;
    margin-left: 16px;
    margin-top: 0.125rem;
    margin-right: 0.25rem;
    margin-left: 1rem;
  ```

The only disadvantage with using shorthand properties is that you can no logner use multiple properties. If you find yourself needing a specific combination often you can easily create your own property mixin.

Here's a list of all of the shorthand property mixins:

  ```scss
    @include size();

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
  ````



## Values

LifeSaver can take any value that can be used in CSS including strings like `auto` and `inherit`.



## Units

While LifeSaver can't handle all units, it does handle the most commonly used units.

Here's a list of all the units you can pass to LifeSaver:

  ```
    px
    em
    rem
    pct
  ```



## Skipping

In CSS there's a common problem when using the shorthand syntax. The problem is that you can't skip a value. In order to use the shorthand syntax in CSS you must define all the values. With LifeSaver you can skip values all you'd like by passing an `x` or `null` value.

  ```scss
    // Input
    @include margin( x auto );

    // Output
    margin-top: auto;
    margin-left: auto;
  ```



## Safe Units

LifeSaver has a set of functions for safely converting units to help prevent browser rounding errors that could potentionally break a design.

Here's a list of all the safe unit functions:

  ```
    scale-comp( [value], [scale] );

    ceil-convert( [value] );
    floor-convert( [value] );
    round-convert( [value] );
    convert( [value] );

    un( [value], [scale] );
    em( [value], [scale] );
    rem( [value], [scale] );
    px( [value], [scale] );
    pct( [value], [scale] );

    floor-un( [value] );
    floor-em( [value] );
    floor-rem( [value] );
    floor-px( [value] );

    round-un( [value] );
    round-em( [value] );
    round-rem( [value] );
    round-px( [value] );
  ```



## Scale Compensation

A common problem when using units like rem and em is that when you change the font size of an element it also changes anything else sized with rem and em. To circumvent this, leaving your margins visually the same, you can pass a scale compensation argument equal to the font size.

  ```scss
    // Input
    font-size: 18;
    @include margin( 2 4 x 16, em, 18 );

    // Output
    font-size: 18;
    margin-top: 0.0625em;
    margin-right: 0.0625em;
    margin-left: 0.9375em;
  ```

If you don't want to define scale compensation, but you want to pass an important argument, you can do one of two things:

1. You can set the scale compensation to `x` or `null` telling LifeSaver to ignore this argument.
1. Pass the important argument as shown below.

  ```scss
    @include margin( 1 2, em, $important: important )
  ```



## Important Flag

Passing an important argument tells LifeSaver to apply an important flag to eachy property it generates.

  ```scss
    // Input
    @include margin( 2 4 x 16, em, x, important );

    // Output
    margin-top: 0.125em !important;
    margin-right: 0.25em !important;
    margin-left: 1em !important;
  ```

If you only want to add an important flag to only one of these generated properties, you'll have add another include with only the value you want to add the important flag to.
