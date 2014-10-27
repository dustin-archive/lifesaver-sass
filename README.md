LifeSaver
=========

A Sass mixin that allows for quicker changes to units and values.


##Getting Started
Include LifeSaver into your project at the top of your Sass modules file.

	@include 'modules/safe-units';
	@include 'modules/lifesaver';


##Mixin
	@include ls( [properties], [values], [units], [important] );

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

	// Output is Indented and Commented for Demonstration

	// Margin
		// Pixels
			margin-top: 2px;
			margin-right: 4px;
			margin-left: 16px;

		// Rem
			margin-top: 0.125rem;
			margin-right: 0.25rem;
			margin-left: 1rem;

	// Padding
		// Pixels
			padding-top: 2px;
			padding-right: 4px;
			padding-left: 16px;

		// Rem
			padding-top: 0.125rem;
			padding-right: 0.25rem;
			padding-left: 1rem;


###Properties
+ Pass multiple properties to output them with same values.
+ Properties are output in the order you list them in.

###Units
+ Pass multiple unit types for fallback purposes.
+ Units are output in the order you list them in.

###Skips
+ Skip values while keeping the shorthand syntax. Any value you don't want to re-define, just place an x.

###Functionality
+ You can pass an important argument like you normally but without an exclamation point.
+ You can still pass strings like auto and inherit, along with any other string you throw in there.

###Positions
+ You can pass a "position" argument and enter in values for top, right, bottom, and left as you would expect.


##Functions
There are 16 main functions. They're named very self explanitory so for more info on what they do look in `_safe-units.scss`.

	// Convert
	ceil-convert( $value );
	floor-convert( $value );
	round-convert( $value );

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
