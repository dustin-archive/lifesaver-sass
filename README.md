LifeSaver
=========

Sass mixin that makes working with units and box model properties super easy.

Box model mastery! Tame the box! Be a slave no more!

## Getting Started

Import LifeSaver into your project at the top of your Sass extensions file (or whatever). Order matters.

	// Independant
	@import 'extensions/safe-units';
	@import 'extensions/skip';

	// Dependant
	@import 'extensions/lifesaver'; // Requires: safe-units, skip
	@import 'extensions/lifesaver-properties'; // Requires: lifesaver, safe-units, skip
	@import 'extensions/lifesaver-debug'; // Requires: lifesaver


## Quick Overview

	@include ls( [properties], [values], [units], [scale compensation], [important] );

LifeSaver properties:

	// Input
	@include margin( 2 4 x 16, px rem );
	@include padding( 2 4 x 16, px rem );

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


Multiple properties:

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


Scale compensation:

	// Input
	font-size: 18;
	@include margin( 2 4 x 16, em, 18 );

	// Output
		font-size: 18;
		margin-top: 0.0625em;
		margin-right: 0.0625em;
		margin-left: 0.9375em;


## Features

### LifeSaver Properties

+ Type less.
+ Cleaner looking code.

There are 5 LifeSaver properties

	margin()
	padding()
	border-width()
	position()
	size()

### Properties

+ Pass multiple properties to output them with same values.
+ Properties are output in the order you list them in.
+ You can pass a `position` argument and enter in values for `top`, `right`, `bottom`, and `left`.

### Values

+ Shorthand for all box model properties including the `position` property.
+ You can still pass strings like `auto` and `inherit`, along with any other string you throw in there.
+ Browser rounding error fixes built-in.

### Units

+ Pass multiple unit types for fallback purposes.
+ Units are output in the order you list them in.

### Skips

+ Skippable values using `x` or `null` without defaulting to 0.

### Scale compensation

+ You can set or change the font size with `rem` or `em` without affecting other properties that use `rem` or `em`.

### Important

+ You can pass an important argument but without an exclamation point.

### Safe Units

There are 17 functions. They're named very self explanitory. If you want more info on what they do look in `_safe-units.scss`.

	// Convert
	ceil-convert( $value );
	floor-convert( $value );
	round-convert( $value );
	convert( $value );

	// Units
	un( $value );
	em( $value );
	rem( $value );
	px( $value );
	pct( $value );

	// Floor
	floor-un( $value );
	floor-em( $value );
	floor-rem( $value );
	floor-px( $value );

	// Round
	round-un( $value );
	round-em( $value );
	round-rem( $value );
	round-px( $value );
